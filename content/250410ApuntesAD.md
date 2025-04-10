+++
title = "Apuntes para la clase de Active Directory Pumahat"
date = "2025-04-10"
description = "Resultados de mi sesión de estudio sobre Active Directory para dar clases en Pumahat. Este artículo irá cambiando con el paso del tiempo probablemente"
path = "blog/250410apuntesAD"
+++
# Apuntes para clases de Active Directory

## Que es Active Directory?

Active Directory es la implementación de Microsoft de un servicio de directorio, es decir, es el approach de Microsoft a ofrecer un servicio que nos permita almacenar y organizar la información de una red de ordenadores y los recursos a los que tiene acceso; le permite a los administradores gestionar el acceso de los usuarios a los recursos de la red según las necesidades correspondientes.

Un servicio de directorio es una capa de abstracción entre los usuarios y los recursos compartidos.

### Capa de abstracción entre usuarios y recursos compartidos

Este es el término clave. Imagina que tienes una empresa en donde tienes a todos tus empleados (USUARIOS), los cuales para realizar su trabajo deben de tener acceso a ciertos servidores, impresoras, carpetas compartidas, computadoras(que sus cuentas sirvan para entrar a varias computadoras, sea remotamente o in situ), repositorios, etc (RECURSOS COMPARTIDOS).

Este es un problema, porque evidentemente necesitas establecer políticas para acceder a estos recursos, desde el qué hasta el cómo, para mayor seguridad. Y si lo haces a manita pues está difícil.

Entonces es aquí donde entran los servicios de directorio como Active Directory, que son herramientas administrativas que justamente te permiten definir la especificación de cómo tus usuarios van a acceder a los recursos compartidos, y a  cuáles tiene acceso cada grupo de usuarios.

### Que provee active directory?

Provee funciones de autorización y autenticación, dentro del sistema operativo Windows (pq ps Microsoft flaco).

Una forma "sencilla" de establecer políticas grupales de acceso a recursos compartidos.

Retrocompatibilidad con muchas versiones de Windows y Windows Server

Muchisima escalabilidad, se pueden manejar millones de objetos por dominio, y varios dominios por organización.


### Problemas notorios desde un principio

Una documentacíón que parece más un libro de leyes lol

La retrocompatiblidad (trae fallas de seguridad)

Las configuraciones default suelen ser propensas a ser vulnerables (not secure by default)

### Interés en ciberseguridad

El 95% de las empresas de Fortune 500 utilizan Active Directory, entonces tenemos q saber q rollo
Active Directory es casi un monopolio cuando hablamos de servicios de directorio, si haces pentesting de red es casi seguro que te lo topes

## Estructura

Tenemos un bosque, el cual contiene varios "arboles" a los que llamaremos dominios (los cuales a su vez también pueden tener más dominios adentro, pero luego vemos eso). Cada uno de estos dominios es independiente entre sí, excepto cuando se establecen "trust relationships" entre ellos.

Las trust relationships son relaciones entre dominios que permiten que los usuarios de un dominio puedan acceder a otro con las mismas credenciales. 

Un dominio contiene dentro de si objetos que representan tanto a los usuarios, como a los recursos compartidos, como a las maquinas encargadas de controlar estos accesos y portar ciertas sutilezas especiales. Estos ultimos son los Domain Controllers, los cuales veremos más adelante.

Cada objeto posee atributos que definen características del objeto (como en la programación orientada a objetos). Por ejemplo, una instancia de "Computer" podría tener atributos tales como el hostname o el DNS name. Todos los atributos tienen un nombre LDAP asociado.

Existe un schema, el cual es la guía de qué objetos pueden existir dentro de todo el bosque y cuáles serán sus atributos. Si te vas a POO, piensalo como el archivo que define todas las clases que serán usadas por el programa. Este es único por bosque y si alguno de los dominios lo edita, el cambio se refleja en todos los demás.

Existen tambien contenedores, los cuales pertenecen a un dominio y contienen objetos.

Las hojas son objetos que ya no contienen otros objetos x si mismos

## Atributos globales para los objetos

### Identificadores: GUID, SID, Distinguished Name

Todo objeto en AD posee GUID, el cual es único por objeto, y de hecho como es una implementación de UUID (de implementación cerrada) podemos confiar en q si Microsoft hizo bien su chamba, genuinamente esta GUID es única incluso a nivel universal(la probabilidad de que no lo sea es menor a la probabilidad de escoger dos veces un mismo átomo aleatorio entre todos los átomos de la galaxia).

Ahora, existen tipos de objetos especiales llamados Security principals, los cuales son aquellos que se pueden autenticar "sean usuarios, cuentas de computadora, procesos, etc". Estos tienen también otrp identificador llamado security identifier (SID). Este también es "unico" en todo el forest, pero no es unico en todo el universo, y de hecho hay algunos SIDs conocidos que se reutilizan para identificar ciertos grupos y usuarios genéricos, luego los veremos probablemente.

El distinguished name(DN) de un objeto es la ruta completa al objeto. Ejemplo: cn=bjones, ou=IT, ou=Employees, dc=inlanefreight, dc=local. Su DN es inlanefreight.local/Users/Sales/Managers/BJones

### Otros

Tambien tenemos otros identificadores que generalmente se derivan de los anteriores o no son tan importantes pero tampoco es malo tener la referencia de cuáles son:

#### Relative Distinguished Name

Es el distinguished name pero recortado al nivel que lo pueda hacer unico al nivel de la Organizational Unit a la que pertenece. Generalmente es la ultima sección del distinguised name.

#### sAMAccountName

Es otro identificador para Security Principals (objetos autenticables). Puedes pensarlo como el nombre de usuario que utilizas para autenticarte, solo que con la característica especial de que este brother es compatible con SAM (es decir, con sistemas antiguos de Windows)

#### userPrincipalName

Ooootro identificador, pero este diseñado en formato de cuenta de correo (usuario@dominio) Este no es obligatorio.

## Domain Controller

Los domain controllers son las partes encargadas de darle la funcionalidad a Active Directory.

Son máquinas a las cuales se les asignan distintas labores relacionadas con la autenticación, los permisos, el uso de recursos, etc. En un principio había un solo domain controller por dominio y era el que bisneaba todo, pero después se crearon los *Roles FSMO* (Flexible Single Master Operation) para tener distintos controladores de dominio con distintas responsabilidades. Aqui hay algunos ejemplos.

No todos estos son Roles FSMO, se hará la aclaración correspondiente en cada uno.

### Schema Master (uno por bosque)

Guarda la copia maestra del Schema

### Domain Naming Master (uno por bosque)

Maneja los nombres de los dominios, se asegura de que dos dominios del mismo nombre no puedan ser creados en el mismo bosque.

### Relative ID Master (RID pa los cuates)(uno por dominio)

Asigna bloques de RIDs a otros Domain Controllers dentro del dominio. Esto asegura que a los objetos no se les asigne un mismo SID.

### Primary Domain Controller Emulator (PDC pa los cuates)(uno por dominio)

Este es el mero fuerte, este es el domain controller autoritativo que responde a las solicitudes relacionadas con autenticación, como cambios de contraseñas, etc. También es este el brother que mantiene la hora y fecha maestra para todo el dominio.

### Infraestructure Master(uno por dominio)

Se encarga de traducir GUIDs, SIDs y DNs entre dominios, trabaja en conjunto con el resto de DCs del bosque para asegurarse de que estos se mantengan consistentes trabajando de la mano particularmente con el Global Catalog

### Global Catalog

Guarda una copia parcial y limitada de todos los objetos del bosque. Esto facilita busquedas en todo el bosque, facilita la autenticación entre dominios y como vimos trabaja de la mano con el IM para mantener estas congruencias en los nombres.

Un global catalog no es un rol FSMO, por lo que en realidad un servidor de global catalog no es un controlador de dominio, aunque trabaja de la mano con ellos. De hecho se recomienda que el GC y el IM no existan en la misma máquina.

### Nivel de funcionalidad

La versión de Windows que ejecutan los domain controllers de un dominio determinan las funcionalidades que puede poseer un dominio. Esto mediante el Domain Functional Level.

El nivel funcional de un dominio se determina por la versión más antigua que esté ejecutando un controlador de dominio. También este es un dato interesante a tener en cuenta cuando andes bisneando un dominio.

## Access Control Entries

Es aquí donde comenzamos a hablar de permisos.

Cada Access Control Entry contiene los siguientes datos:

- Trustee (cuenta de usuario, grupo, o sesión)

- Permisos del trustee

- Negaciones del trustee

Una ACE forma parte siempre de una ACL, y la ACL a su vez está vinculada siempre al objeto que protege.

### Access Control List
Son todas las ACEs que aplican a un objeto dado, pueden ser de dos tipos: DACL y SACL

### Discretionary Access Control List
Son las ACEs vinculadas al objeto que hablan de los permisos que tiene cada usuario sobre este objeto. Estas hablan de acceso y por lo tanto en el sentido más estricto de autenticación esta es la verdadera ACL

### System Access Control List
Esta no define permisos de acceso, esta define los eventos a auditar sobre el objeto que luego los administradores va a poder consultar en los registros correspondientes.

## Donde se guardan estos datos?

Toda la información que acabamos de revisar sobre un Active Directory se guarda en NTDS.DIT

Este es un archivo que se guarda en un Domain Controller, especificamente en la ruta C:\Windows\NTDS\

En este archivo se guarda toda la información sobre los usuarios, los objetos, los grupos y particularmente para nosotros, aquí existen los *password hashes* que luego podremos usar para algunos ataques fancys


Pero cabe señalar que cada Domain Controller solo guarda en su NTDS.DIT la información de su dominio, no la de todo el bosque.

## Protocolos

Active Directory utiliza varios protocolos para cumpir con sus funciones, los principales a observar son:


### Kerberos

Es el protocolo de autenticación que utiliza Active Directory. Para entender por qué es tan complejo primero tenemos que entender los principios buscados detrás de su diseño.

#### 1. No transmitir contraseñas en texto plano

La contraseña nunca debe viajar por la red, pues una posible interceptación de la misma podría traer problemas. En lugar de eso, la contraseña se usará solamente para validar la identidad del usuario y así darle un ticket, el cual es el que usará para el resto del procedimiento

#### 2. Autenticación mutua

Las tres partes involucradas (autenticador, servicio y cliente) se demuestran sus autenticidades mediante secretos que cada una de estas partes debería de conocer por su posición.

#### 3. Minimizar la exposición de las credenciales

Solamente el servidor de autenticación conoce los secretos de cada una de las partes, ni el servicio conoce la contreña del usuario ni el cliente conocerá el secreto del servicio. Y además, esta confianza se tiene que estar renovando constantemente pues la autenticación es temporal.

#### 4. Centralización para escalabilidad

Tanto clientes como servicios negocian los accesos unicamente con el servidor y por ocasiones contadas. Asi no es necesario que el cliente tenga que estar demostrando su identidad con cada servicio que quiera usar, y con esto, que todos los servicios deban de tener la infraestructura necesaria para hacer esto.

#### 5. Modularidad

Cada paso de Kerberos se encuentra modularizado (como si fueran microservicios) por lo que actualizarlos para mantenerlos vigentes a las necesidades actuales es sencillo.


Entonces, el flujo de Kerberos es el siguiente:

1. El usuario le pide un TGT al Authentication Service (AS), esto lo hace mediante un mensaje (AS\_REQ) que contiene su nombre y una timestamp cifrada usando su contraseña. Este mensaje lo envía al AS

2. El AS recibe el mensaje, consulta la base de datos del KDC para obtener la contraseña del usuario e intenta usarla para desencriptar el mensaje, si es exitoso este proceso, entonces le da un TGT al usuario (AS\_REP). El TGT está cifrado con la clave secreta del TGS (contraseña del usuario krbtgt), la cual solo conocen el TGS y el AS.

3. El cliente arma un mensaje (TGS\_REQ), esta vez destinado al TGS, el cual contiene el TGT, un autenticador (mensaje cifrado con la identidad del cliente y otra timestamp) y el nombre del servicio al que quiere acceder.

4. El TGS recibe el mensaje y lo intenta desencriptar con su clave secreta, extrae los datos adjuntados y los verifica.

5. EL TGS responde con un mensaje (TGS\_REP) que contiene un Service Ticket cifrado con la clave secreta del servicio y una clave de sesión cliente-servicio.

El service ticket contiene una timestamp que dice la fecha en la que fué expedida, para que el servicio pueda saber que el ticket está fresco.

6. El usuario usa el Service Ticket para autenticarse con el servicio. Si el servicio logra desencriptar el ticket con su clave privada y reconoce que la info dentro es correcta, entonces le da acceso al usuario.

El protocolo Kerberos suele usar el puerto 88 para intercambiar tickets, entonces puedes localizar los domain controllers escaneando las máquinas que estén escuchando en este puerto.

#### Nota:

Todos los DC tienen la facultad de funcionar como KDCs, pero se le da prioridad al PDC Emulator, y este ultimo tiene ciertas facultades especiales.

### LDAP

Apache es a HTTP lo que Active Directory es a LDAP.
Este es el protocolo de comunicación que usa AD pues

### DNS

Trivialote no?
El servidor DNS escucha en el puerto 53, por si alguien te pregunta :D

### MSRPC

### NTLM

Otra vez tu bro? Exacto, este protocolo de autenticación se suele usar en lugar de Kerberos en ciertas situaciones, por ejemplo:

1. Sistemas heredados que no soportan Kerberos

2. Fallo de Kerberos (no hay ningún KDC disponible)

3. Acceso local

4. Aplicaciones heredadas que no soportan Kerberos

Aunque el protocolo de autenticación solo se usa en estos casos, los hashes usados para todos los pasos de Kerberos de hecho son NT Hashes

## Ataques comunes a considerar

### Kerberoasting

Un Service Ticket y un vaso de agua no se le niegan a nadie, y el Service Ticket puede contener el hash NTLM de una cuenta en el servicio. Por lo que kerberoasting se sirve de una cuenta estandar para pedirle un Service Ticket al KDC, una vez obtenido lo extrae de memoria y el atacante se pone a desencriptarlo offline, si el hash NTLM estaba ligado a una contraseña débil entonces esta es obtenida y con esto tenemos acceso a una cuenta de servicio con potencialmente mejores permisos, o también a potencialmente hacer un ataque Silver Ticket a ese servicio.


### Golden ticket

Si ya comprometimos un DC y podemos obtener la clave privada del KDC (la que se comparten el AS y el TGS) entonces podemos forjarnos nuestros propios TGTs con acceso ilimitado al dominio impersonando a cualquier usuario y acceder a cualquier servicio, sin necesidad de conocer las contraseñas de los usuarios.


### Silver ticket

En lugar de falsificar TGTs, falsificamos Service Tickets para acceder a un servicio específico. Para esto necesitamos conocer el hash del servicio, el cual podríamos haber obtenido con kerberoasting

