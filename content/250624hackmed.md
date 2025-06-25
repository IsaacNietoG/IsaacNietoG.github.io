+++
title = "Road to HackMex: Dia 4 - Catcabbage"
date = "2025-06-24"
description = "Cuarta máquina del entrenamiento para Hackmex"
path = "blog/250624hackmex2025"
+++

# Writeup: catcabbage - echoCTF

## Información General

![](https://i.ibb.co/zVz297Mp/Screenshot-20250623-104359.png)

## Descripción de la máquina
Come see our unique cat that likes to eat cabbage!!! Come on in, have a bite.

## Enumeración
### Escaneo Inicial
Comenzamos escaneando con Nmap mientras concurrentemente nos metemos a la ip en el navegador para descubrir rápidamente un posible servicio HTTP.
Y efectivamente, encontramos un servicio HTTP el cual está hosteando un CMS llamado BlackCat. 
De paso, cuando termina nmap, nos confirma dicho servicio, varias carpetas interesantes prohibidas por robots.txt y un servicio SSH en puerto 22.
 
![](https://i.ibb.co/q3VQ8PNz/Screenshot-20250623-100954.png)


### Análisis de Servicios
Encontramos un BlackCat CMS en el servicio http el cual carga mal y dice que está en mantenimiento.

![](https://i.ibb.co/nMLjwVB8/Screenshot-20250623-100740.png)

Si clickeamos a cualquier enlace interactivo de ahí nos redirigirá a un dominio específico, quiero pensar que la mala carga es por hojas de estilo ligadas al dominio. Entonces ligamos la ip a dicho dominio en nuestro /etc/hosts y con esto carga correctamente

![](https://i.ibb.co/hRQKV7nt/Screenshot-20250623-100843.png)
![](https://i.ibb.co/bRRVTTJM/Screenshot-20250623-100905.png)

Una vez teniendo buena visibilidad del sitio, podemos comenzar a explorar el servicio para ver qué podemos encontrar, comencemos por explorar los sitios prohibidos por robots.txt que nos dió nmap y que también nosotros podríamos explorar en /robots.txt
Varios son redirecciones que nos llevan directamente de regreso a la página de mantenimiento y unas cuantas son sitios directamente prohibidos, excepto por uno.
Encontramos panel de admin en /backend y comenzamos a probar contraseñas
![](https://i.ibb.co/qYTFnV5P/Screenshot-20250623-101641.png)
Empecé con las credenciales tradicionales y que por fuerza de hábito siempre probaremos a mano para ahorrarnos configurar herramientas:

- admin:admin
- admin:password
- **admin:admin123**

Y la ultima fue la que amarró. Entonces ya tenemos credenciales de admin.


## Explotación
### Busqueda de vulnerabilidades

Vamos a buscar vulnerabilidades que nos puedan ayudar, y comencemos por el servicio hosteado, porque es poco común que el foothold se encuentre en los otros dos servicios (el servidor HTTP en sí y la versión de SSH)

Y el primer resultado al buscar exploits para este CMS es el siguiente:

[Blackcat Cms v1.4 - Remote Code Execution (RCE) - PHP webapps Exploit](https://www.exploit-db.com/exploits/51605)

Vamos a probar si el servicio es vulnerable a este exploit, y a festejar porque su primer requisito es justamente tener credenciales de admin

![](https://i.ibb.co/zTPHQJ6r/Screenshot-20250623-101058.png)

### Intentos de explotaciones

Preparamos el payload según lo marcan las instrucciones del exploit y lo subimos bajo estas mismas instrucciones. Si lo intentamos consultar en la estructura dada por el exploit nos encontraremos con un error 404, pero lo que debemos hacer es simplemente ajustar la estructura del enlace a la estructura de la máquina. Para esto vamos a considerar las siguientes cosas:

- En el exploit veremos que el backend vive en /BlackCatCMS-1.4/upload/backend/......
- En la máquina, el backend vive directamente en /backend
- Entonces, en el exploit /BlackCatCMS-1.4/upload/ es equivalente a la raíz / en la máquina

Dado esto, el enlace correcto para buscar nuestra payload es:

/modules/lib_jquery/plugins/poc/poc.php?code=cat%20/etc/passwd

### Explotación

Si entramos al payload nos daremos cuenta de que fué exitoso y podremos ejecutar comandos, lo cual ya nos da nuestro primer foothold.

![](https://i.ibb.co/sptYwRfv/Screenshot-20250623-102401.png)

Usando este foothold levantamos nuestro netcat, upgradeamos la terminal y we are in

![](https://i.ibb.co/5X0b1RQz/Screenshot-20250623-102547.png)

Ya desde el payload podíamos sacar la bandera en /etc/passwd, pero si no la tenemos todavía, ahora con la shell la podemos sacar. Una vez dentro, también por fuerza de hábito probaremos si ya podemos también encontrar la bandera en printenv

![](https://i.ibb.co/cKqd72zy/Screenshot-20250623-102638.png)

## Escalación de Privilegios
### Análisis

Una vez dentro, comenzamos a analizar nuestras capacidades para ver de dónde nos vamos a agarrar para escalar privilegios. Antes de correr linpeas voy a correr un sudo -l porque ultimamente me ha pagado bastante bien ese comando. Y justo vemos que tenemos permiso de correr como sudo un binario llamado cabbage. -curiosamente la máquina se llama catcabbage-.

![](https://i.ibb.co/TDyzZtWC/Screenshot-20250623-102804.png)

Y analizando su código fuente vemos que es lo siguiente:

![](https://i.ibb.co/K1dJWM3/Screenshot-20250623-102952.png)

El binario entonces lo que hace es tomar una serie de archivos y los pasa por broccoli-compass, que es una librería que traduce SASS en CSS.

Si googleamos la biblioteca, nos encontraremos con la siguiente vulnerabilidad:

[Vulnerability in broccoli-compass](https://github.com/omnitaint/Vulnerability-Reports/blob/9d65add2bca71ed6d6b2e281ee6790a12504ff8e/reports/broccoli-compass/report.md)

![](https://i.ibb.co/4Zhw8JPM/Screenshot-20250623-103504.png)

La vulnerabilidad permite ejecución de comandos sirviéndose de contaminar el nombre de un archivo que pueda ser recibido por la biblioteca en la lista de archivos a traducir. Si analizamos la PoC adjunta, podemos entender claramente su funcionalidad y darnos cuenta de que es replicable en nuestro caso.

![](https://i.ibb.co/MDB92mSy/Screenshot-20250623-103723.png)

Vemos que efectivamente es replicable a nivel de nuestro usuario actual, si lo corremos como root con sudo es altamente probable de que sea el mismo caso.

### Explotación

De aquí podríamos proceder de varias formas una vez teniendo ejecución de comandos como sudo, podríamos:

- Correr un netcat para abrirnos una sesión de root en otro puerto
- Modificar /etc/passwd para modificar la contraseña de root y acceder probablemente por ssh
- Ponerle SUID a /bin/bash para poder abrirnos in-spot un bash con id de root.
- Dumpear las banderas en textos legibles por nosotros

Y yo voy a aplicar la última jajaj. Vamos a dumpear las banderas que nos faltan, que es:
- El archivo en /root
- La bandera en /etc/passwd

Con los siguientes comandos:

    sudo cabbage '$(cat /etc/shadow > /tmp/hola)'
    sudo cabbage '$(ls -la /root > /tmp/holaa)'

![](https://i.ibb.co/zVz4hcKv/Screenshot-20250623-103758.png)

Si leemos estos archivos, tendremos las banderas

**headshot**
