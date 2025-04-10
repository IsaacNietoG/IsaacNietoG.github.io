+++
title = "Writeup para Attacktive Directory - TryHackMe"
date = "2025-04-10"
description = "Resultados de mi sesión de estudio sobre Attacktive Directory para dar clases en Pumahat. Este artículo irá cambiando con el paso del tiempo probablemente"
path = "blog/250410AttacktiveWriteup"
+++

# Attacktive Directory Anotaciones

Esto comienza como una colección de apuntes sobre la máquina Attacktive Directory que vamos a realizar en Pumahat para aprender sobre Active Directory. Idealmente podría evolucionar a ser un writeup, si ~~dejo de ser un procrastinador~~ puedo darle un formato que me sea satisfactorio, por ahora, solo son anotaciones útiles para dar la clase.

## Tarea 1: Deploy the machine

Esta parte es trivial, solamente nos explica sobre cómo conectarnos a la máquina del laboratorio mediante la VPN de THM, si ya haz hecho máquinas de THM entoces esto es conocido para ti.

## Tarea 2: Setup

Aqui vamos a preparar las herramientas que vamos a utilizar para este laboratorio. Es aqui donde podemos empezar a señalar ciertos detalles para cada una de las herramientas que vamos a utilizar en el laboratorio y particularidades que podemos señalar.

Voy a asumir que estás usando Kali.

### Impacket

Vamos a empezar por lo dificil, Impacket es una colección de herramientas escritas en Python con las que podemos trabajar con ciertos portocolos de red, particularmente para nuestro uso actual: con SMB y MSRPC

Las instrucciones para instalar Impacket que están declaradas en esta sección no se pueden seguir para Kali, porque las dependencias de Python de Kali son manejadas por el sistema operativo. Esto significa que no podremos ni siquiera instalar las dependencias necesarias, mucho menos el paquete en sí.

Esto de que los entornos de Python estén manejados por el sistema es algo cada vez en mayor uso por más distribuciones de Linux, y la solución tradicional es crear un entorno virtual en Python desde el cual correríamos el paquete, sin modificar la instalación de Python del sistema.

Para instalar Impacket, en su lugar vamos a usar pipx, el cual es una herramienta de linea de comandos que se va a encargar por nosotros de esto del entorno virtual y todo lo demás, y además existe ya en los repositorios de Kali por lo que nos es conveniente usarla.

Para instalar pipx:

    sudo apt install python-pipx

Y luego, usando pipx:

    pipx install impacket

Con esto tendremos instalado Impacket y podemos continuar.

### Bloodhound y Neo4J

Estas herramientas se pueden instalar tal y como dice el laboratorio.

### Extra: Kerbrute

Vamos a usar kerbrute más adelante, entonces pues me parece adecuado que de una vez la descarguemos.
Kerbrute es compilada y hasta donde pude averiguar en una instalación de Kali tradicional, es portable, entonces en realidad no necesitamos otra cosa que descargar su ultima release del repositorio oficial, este ejecutable nos sirve sin problemas.

https://github.com/ropnop/kerbrute

## Task 3: Welcome to Attacktive Directory

Esta es la primera parte de enumeración, aquí vamos a enumerar la máquina para ver qué puertos tenemos abiertos y cierta información sobre el dominio que podemos recuperar desde ya con los scripts de nmap y una herramienta llamada enum4linux (que viene por default en Kali)

El comando sugerido es

    nmap -Pn -T4 -A -p- $IPDELAMAQUINA

Con este comando correremos todos los scripts de reconocimiento de nmap, en todos los puertos, a la máxima velocidad posible, por lo que podremos obtener toda la info que nos podrá proporcionar nmap.

Te sugiero que guardes la información obtenida por este nmap, porque aquí vamos a encontrar otras cosillas que necesitaremos más adelante.

Por lo pronto, observemos que estan abiertos los puertos 139 y 445. Estos son puertos para el servicio SMB, vamos a ver que información obtenemos con

    enum4linux $IPDELAMAQUINA

De aquí obtendremos el nombre NetBIOS de dominio de la máquina. Aquí ya llevaremos dos respuestas a las preguntas.

La tercera respuesta es .local

Esto porque la recomendación de Microsoft para dominios de Active Directory (y la buena práctica) es usar dominios registrados que tengamos bajo posesión, y el TLD .local no es válido en la ICANN.

## Task 4: Enumerating Users via Kerberos

Es aqui donde entra al spotlight nuestro querido Kerbrute, el cual es una herramienta que nos permite bruteforcear y enumerar a través de la preautenticación (AS\_REQ y AS\_REP)

Primero nos interesa enumerar nombres de usuario válidos, para esto vamos a descargar la lista de posibles usuarios y usarla para correr kerbrute.

    kerbrute userenum --dc $IPDELAMAQUINA -d $NOMBREDELDOMINIO userlist.txt

El nombre del dominio lo obtuvimos durante el escaneo con nmap, lo vas a poder encontrar en la información obtenida sobre el servicio que está corriendo en el puerto 389.

Cuando comencemos a enumerar, rápidamente nos vamos a encontrar con dos cuentas interesantes: svc-admin y backup.

La primera es una cuenta de servicio que se usa para ejecutar servicios (apoco?). La segunda es una cuenta de backup, generalmente las cuentas backup tienen privilegios interesantes que podemos aprovechar a nuestro favor, vamos a considerar estas dos cuentas.

## Task 5: Abusing Kerberos

Esta tarea nos consiste de buscar si alguna de las cuentas encontradas es vulnerable a ASREPRoasting, para esto vamos a usar una herramienta que nos provee Impacket llamada GetNPUsers.py

ASREPRoast (Authentication Service Request Roasting) es un método que permite a un atacante solicitar un ticket de autenticación Kerberos (específicamente, un TGT - Ticket Granting Ticket) para cuentas de usuario que tienen deshabilitada la preautenticación. Luego, el atacante puede extraer un hash de la contraseña de ese ticket y intentar descifrarlo offline, sin necesidad de interactuar repetidamente con el dominio.

Vamos a probarla con las dos cuentas interesantes que señalamos previamente

    GetNPUsers.py -no-pass -usersfile usuarios -dc-ip $IPDELAMAQUINA thm-ad/

svc-admin es vulnerable a ASREPRoasting y nos dará su hash correspondiente. Vamos a investigar un poco sobre el hash y lo quebraremos con Hashcat y la lista de contraseñas suministrada en la tarea previa.

    hashcat -m 18200 hash passwordlist.txt

Ahora tenemos una cuenta de servicio con todo y contraseña.

## Task 6: Back to the basics

Con esta cuenta obtenida podemos enumerar los shares a los que tenemos acceso.

    smbclient -L \\\\$IPDELAMAQUINA -U 'svc-admin'

Nos pedirá la contraseña, que ya sabemos por el paso previo.

Al listar los shares nos llamará la atención rápidamente el disco backup. Veremos su contenido con

    smbclient \\\\$IPDELAMAQUINA\\backup -U 'svc-admin'

Aqui encontraremos un archivo de texto interesante, recuperemoslo con 

    get backup\_credentials.txt

Y luego

    exit

Si vemos el contenido de este archivo veremos que es un base64, lo decodificaremos y adentro encontraremos que es el usuario backup y su contraseña.

## Task 7: Elevating Privileges within the Domain

Es aquí donde entra en juego el hecho de que ahora tenemos acceso al usuario backup.

Este usuario tiene el derecho a solicitar sincronizaciones de la base de datos del domain controller. Esto lo explotaremos para dumpear los hashes de las cuentas de este dominio usando DRSUAPI

DRSUAPI es una interfaz de programación (API) utilizada por los controladores de dominio para replicar datos entre sí en un entorno de AD.

Esta API permite acceder a los datos almacenados en NTDS.DIT como parte del proceso legítimo de sincronización entre DCs.

Sin embargo, puede ser abusada por atacantes o herramientas de pentesting para "dumpear" (extraer) el contenido de NTDS.DIT sin necesidad de detener el servicio de AD o acceder directamente al archivo en disco.

A grosso modo, vamos a impersonarnos como otro Domain Controller y solicitarle al DC real que nos de la base de datos, mediante este mecanismo de replicación completamente legítimo.

Esto está completamente automatizado con otra herramienta de Impacket llamada secretsdump.py

    secretsdump.py -just-dc backup@$IPDELAMAQUINA

Y una vez teniendo los hashes de las contraseñas de todos los usuarios del dominio, podemos rifarnos un chulo pass the hash.

Logeamos en la máquina como Administrator usando

    evil-winrm -i $IPDELAMAQUINA -u administrator -H hashObtenido

Oficialmente we are in, tenemos una sesión de powershell de administrador con la cual obtendremos el resto de banderas, las cuales se encuentran en los escritorios de cada usuario.

