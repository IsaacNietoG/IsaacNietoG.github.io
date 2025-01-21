+++
title = "¿Por qué cambiaría un entorno de escritorio por un gestor de ventanas?"
date = "2025-01-14"
description = "En este artículo te voy a platicar mi experiencia haciendo el cambio a un gestor de ventanas, te hablaré de todos los obstáculos que me he topado a lo largo de este proceso, pero también todas las ventajas que me he encontrado"
path = "blog/250114gestorDeVentanas"
+++

# Pequeños antecedentes

Desde que ingresé a la carrera, y probablemente desde un poco antes, he sentido un gran interés para encontrar maneras de mejorar mi flujo de trabajo, desde implementar herramientas en mi computadora, hasta implementar marcos de trabajo que me ayuden a aprovechar mejor mi tiempo. Esto porque me considero una persona bastante ~~floja~~ dispersa y a veces me cuesta entrar en mi estado de flujo para trabajar. Por lo que necesito tener la certeza de que cuando encuentro este estado, voy a lograr exprimir todo el jugo posible del mismo.
Un ejemplo que ahora recuerdo con nostalgia pero en su momento me resultó bastante estresante fué cuando me decidí a aprender a utilizar Emacs y aprender a usar el teclado correctamente (sin usar nomás dos dedos). Cambiar mi memoria muscular y a la vez aprender a usar una herramienta nueva que parece diseñada para tener la curva de dificultad más pronunciada de la historia (sin hate a Emacs, es lo mejor que me ha pasado en la facultad) fue algo bastante difícil pero definitivamente ahora lo agradezco bastante

En mi permanente viaje por "mejorar mi flujo de trabajo" me he topado con bastantes herramientas que me han hecho volverme más rápido para programar, hacer mis tareas, ~~madrearme el teclado~~ y aprender cosas nuevas, esto último siendo lo que más me gusta hacer después de descomponer cosas.
Y algo que no había probado hasta hace poco, y que es el motivo principal de este artículo son los gestores de ventanas. Si no entiendes a qué me refiero con gestor de ventanas, te voy a platicar un poco acerca de este concepto.

# Que es gestor de ventanas? Y que es un entorno de escritorio, ya que andamos por aquí?

Primero que nada vamos a platicar un poco el motivo histórico de ambos conceptos.
Considera que la potencia de las computadoras en los inicios de las mismas era tan baja que cosas como un programa con interfaz gráfica, algo que nos parece tan común hoy en día, solamente se podía encontrar en los departamentos de I+D de las mejores empresas y en los sueños más guajiros de algún estudiante de CC ~~yo ese~~. Y además, los pocos programas que existían así, eran tan demandantes en recursos que era dudoso que pudieras tener varios abiertos a la vez (y que quisieras hacerlo en primer lugar). Por lo que los primeros sistemas operativos no tenían como tal gestores de ventanas, y si los tenían, eran la suma rara de una linea de comandos, un servidor gráfico para dibujar cosillas en la pantalla, y tal vez un puntero de ratón, si tu empresa o universidad cagaba dinero. (mira por ejemplo la interfaz de la Xerox Alto, la primera computadora con interfaz gráfica, o algo así).

![Interfaz de la Xerox Alto](/images/blog/250114gestor/xeroxalto.jpg)

Fue hasta que fueron avanzando los años, y las computadoras poco a poco comenzaron a salir de las universidades y empresas y llegar a las casas de la gente, que empezaron a surgir las interfaces gráficas como las conocemos. Comenzaron a crearse más programas con interfaces gráficas (a veces con color :D), y comenzaba a resultar necesario poder tener varios de estos a la vez; fue aquí donde se comenzaron a buscar soluciones para esto, y nació el concepto de ventanas.

## Usemos Windows como ejemplo pa' ambos conceptos
Te voy a hablar un poco de Windows porque creo que su evolución nos permite explicar ambos conceptos de manera fácil, aunque curiosamente todo este artículo solo vale la pena ser leído si no usas Windows, por razones que te explicaré más adelante.
Como ya podrías haber escuchado en algún lugar antes de leer este artículo ~~si eres mi amigo o una morra que me intenté ligar en un bar, probablemente yo te lo conté~~ Windows en sus inicios no era un sistema operativo como tal, en sus inicios empezó como un programa de MS-DOS que podías abrir para tener a tu acceso una interfaz gráfica que te permitiera abrir aplicaciones diseñadas para esto ~~aiwei, el Word~~, o varias aplicaciones hechas para MS-DOS, pero con énfasis en _varias_, no solo una, como era usual.

![Windows 1.0](/images/blog/250114gestor/windows1st.png)

Y era algo que podríamos ahora un poco encajar como un gestor de ventanas, en el sentido de que hacía poco más que justamente darte acceso a tener ventanas, un menú para que las lanzaras con el mouse, y poquito más. No podías ni siquiera hacer que se colocara una detrás de la otra porque todavía no existía un programa compositor que te lo permitiera.

Esto es, no justamente, pero lo suficientemente cercano para servir de ejemplo, un gestor de ventanas. Ahora, para hablar de entornos de escritorio, avancemos un poco en la historia a Windows, no mucho, solo hay que movernos a Windows 95.
Quiero hablar de Windows 95 porque es el que, a mi consideración y la de la crítica, ya era un entorno de escritorio completo (tal vez, ahora sí, un sistema operativo como tal, pero no me voy a meter en eso)

![Windows 95](/images/blog/250114gestor/win95.png)

Esta versión ya incluye una barra de tareas, con todo y el famosísimo Menú Inicio, la capacidad de tener un fondo de pantalla, un navegador de Internet ~~aiwei~~, y en general, suficientes avances en su interfaz que podrías usarlo hoy en día y solamente quejarte de que _se ve horrible_; pero hay que entender el contexto de la época, apenas hace unos añitos las pantallas no tenían color, y todo esto ya era mercado doméstico, pero solamente para la gente con un poder adquisitivo considerable. ~~puro wero~~

## Entonces, concluyendo
Podrías decir que entonces un gestor de ventanas te ofrece...
 - Tener varias ventanas abiertas a la vez, que puedes cerrar, abrir, mover y cambiar de lugar
 - Y ya jaja
 
Mientras que un entorno de escritorio te ofrece...
 - Una interfaz completa, con íconos, menú de inicio, paneles, fondos de pantalla y widgets ~~me da risa hablar de widgets porque nadie usa eso desde el 2011~~
 - Aplicaciones preinstaladas, como tal vez un navegador de internet, reproductor multimedia, explorador de archivos, etc, etc
 - Enfoque en ser fácil de usar por el usuario final, a veces mediante integraciones entre los programas que contiene, que le permiten una navegación sin esfuerzos entre todo el entorno.
 
## Pero entonces por qué querrías NO usar un entorno de escritorio?

El gran sacrificio que nos trae usar un entorno de escritorio es la configurabilidad.
Como regla general (aunque no siempre), lograr una mejor experiencia para el usuario final se da en intercambio por la configurabilidad. Ya que mientras más opciones tengas disponibles para cambiar de un producto, la curva de aprendizaje de este mismo se vuelve más difícil. Tener un exceso de opciones a cambiar puede, además de abrumarte, llevar a que sea más fácil que ~~la cagues~~ el usuario final llegue a comportamientos inesperados, configuraciones mal hechas que lleven a problemas difíciles de solucionar; y muchas otras cosas feas que una empresa no busca que le ocurran a sus usuarios.
Este principio es la razón por la que todas las empresas actuales van a un enfoque de simplicidad más que de configurabilidad, y la razón de comenzar entonces a ponderar acerca de estos dos conceptos, y de por qué no uso un entorno de escritorio.
Sabiendo esto, podemos polarizar entonces este mundillo en dos polos opuestos de un espectro: configurabilidad y usabilidad(fuera de la caja). Y ponernos a pensar entonces en los dos usuarios que representan cada polo de este espectro: el usuario casual y el usuario avanzado, donde al usuario casual siempre le va a beneficiar cualquier intercambio de configurabilidad por usabilidad (UX para los compas), y al usuario avanzado todo lo contrario; siempre se verá contento de encontrar herramientas configurables al máximo.
Quiero aclarar que esta polarización es para entender mejor el concepto, y que ambos usuarios son arquetípicos e ideales. Cualquier persona real vive en realidad en el espectro que se forma entre estos dos y nadie puede llenar estos arquetipos completamente.
Porque quiero ver al que se identifique como el usuario avanzado compilar su propio kernel, sistema operativo, configurar y programar sus propias herramientas a su gusto y mantener este estilo de vida en su día a día ~~tal vez si usas Arch Linux o Gentoo pero ni asi. no te emociones~~. O quiero ver al usuario casual usando cualquier cosa directamente como viene de la caja, sin explorar un tantito las cosas que puede cambiar de su producto para sentirlo -aunque sea un poco- más "suyo".

Y entonces, retomando el concepto principal de este post, voy a colocar a los entornos de escritorio en el lado UX de este espectro, por ser la herramienta ideal para navegar la computadora para el usuario casual, y a los gestores de ventanas como la herramienta ideal para navegar la computadora del usuario avanzado.

# Ahora entonces, hablemos de Linux
En Linux, y creo que también en Mac OS(y en realidad en varios otros sistemas operativos ~~pero de los que usamos los ñoños~~) tenemos la posiblidad de cambiar nuestra forma de navegar la computadora, y tenemos una variedad de opciones para esto.
Existen varios entornos de escritorio que podemos elegir para nuestro sistema, como GNOME, KDE ~~ftw~~, Xfce, etc, etc; y también existen varios gestores de ventanas que podemos elegir.
Y cuando me enteré de esto, inmediatamente me puse a investigar y utilizar los más populares para ver cuál me gustaba más, y al final me terminé decantando un poco por KDE, ya que encontré que sus programas encajaban bastante bien en mis gustos personales y mi flujo de trabajo; particularmente me gustaría mencionar Dolphin, su explorador de archivos, y KDE Connect, su solución para interconectar dispositivos. Opciones que de hecho sigo usando actualmente para mi día a día.
Pero, su entorno de escritorio, Plasma, no me terminó de convencer al 100%. Y podría excusarme detrás de la falta de estabilidad que encontraba en mi computadora al usarlo, donde me topaba con varios glitches gráficos y detallitos que me hacían ponerme nervioso unos cuantos minutos de mi día; pero la verdad es que, leyendo en varios lugares de internet, pude concluir que no eran errores que le podía achacar a los desarrolladores y a la herramienta en sí, tal vez simplemente los componentes de mi computadora son demasiado viejos, o tal vez _we weren't meant to be_, como con mi ex.
Pero la realidad es que simplemente había un algo que no me terminaba de convencer, y como ya había probado varios entornos de escritorio, decidí entonces comenzar a probar con los gestores de ventanas.

# Ahora si, mi experiencia con los entornos de escritorio
Quería comenzar con BSPWM, pero al leer un poco sobre su configuración la verdad es que me sentí intimidado al ver la cantidad de configuraciones que tiene, sentí que era demasiado para mí así que tal vez debía buscar algo un poco más simple ~~me dió hueva~~. Y aunque ví que hay varias configuraciones predeterminadas (dotfiles) que uno puede descargar para tener un inicio más sencillo, la verdad es que consideré que usar dotfiles hechas por otras personas para configurar tu gestor de ventanas sería... raro? Considero que las dotfiles deben ser personales y ajustadas específicamente a tu uso, forma de trabajar, y gustos. Claro que puedes usar dotfiles de otras personas para agarrar inspiración pero bueno, considero que una _personal_ ización debería de ser _personal_, o estarías un poco madreandote el concepto de todo esto en primer lugar.

Entonces, investigando un poco por internet, decidí comenzar con i3, que aunque también ofrece muchas configuraciones, considero que es el punto medio que yo busco entre configurabilidad y personalización. Tener algo usable te toma menos de 15 minutos y después de eso tienes las suficientes configuraciones y posibilidades como para no sentirte encerrado.

# Hablemos de i3
Y es que instalar i3 en ambas dos de mis computadoras fueron experiencias bastante sencillas, a pesar de que en este momento ninguna de las dos compartía una distribución de Linux en común.
En mi laptop, que tenía inicio dual de Manjaro y Kali, tuve que rifarme un

pacman -S i3

y un

sudo apt install i3

respectivamente

Y en mi computadora de escritorio, que tenía Ubuntu y Windows, tuve que rifarme un

sudo apt install i3

y un

llanto de impotencia, porque Windows no te permite cambiar tu entorno de escritorio

respectivamente

Y con eso ya tenía instalado i3 en todos mis sistemas, y ya que la configuración default de i3 es lo suficientemente poderosa, en todos era usable ya desde este paso.
Aunque inmediatamente después me topé con problemas que aunque no eran irreconciliables, si que me afectaban a la calidad de vida significativamente, y ahí fue donde empecé a configuar mi i3

## Fondo de pantalla
i3 no ofrece un fondo de pantalla por defecto, y de hecho, ningun fondo en absoluto, ni siquiera negro. Esto, te lleva a que el fondo de pantalla de tu i3 inicialmente es el fantasma de tu pantalla de inicio de sesión, lo cual pues no afecta al uso, pero se ve horrible. Esto lo resolví en 10 minutos instalando feh, que es un programa que configuras en 10 minutos y te da el fondo de pantalla para que seas feliz

## Bindings de VIM... a medias
Si vienes de no usar VIM, o al menos algo que te acerque a sus bindings, esto es un tema que probablemente te duela mucho. Y es que en i3, la forma que tienes de moverte sobre las ventanas es con algo parecido a los bindings de VIM. Si no los conoces, de manera breve te los platico:

H para moverte a la izquierda

J para moverte hacia abajo

K para moverte hacia arriba

L para moverte hacia la derecha

Si no los conoces, entonces probablemente al leerlos y ver lo contraintuitivos que pueden resultar a ser en un inicio, me podrías preguntar ¿Y yo para qué ~~verga~~ quería usar eso?. Bueno, hay todo un mundo detrás, pero para rápido:
Coloca tus dedos en la posición apropiada para usar el teclado:

![](/images/blog/250114gestor/homerow.jpeg)

Y te darás cuenta de que no ocupas mover tus manos de esta posición casi nada para moverte con estos bindings. Esa es la razón de ergonomía.

Pero el problema en i3 está en que los bindings no son directamente los de VIM. Aquí no se usa HJKL, se usa JKL;. Y esto es por un dato curioso ~~de esos que ocupo pa ligar en las pedas~~ que ahorita te voy a platicar.

Y es que bueno, primero hay que decir que los bindings de VIM no son los bindings de VIM, en realidad son los bindings de vi, que es el editor de texto en el que está basado VIM (ViIMproved), y los bindings de vi en realidad no son los bindings de vi, son los bindings que se usaban en la computadora del creador de vi, Bill Joy. Su computadora (o bueno, la terminal que el usaba para su computadora) era una ADM-3A de Lear Siegler, y la forma de mover el puntero en esta era justamente HJKL. Considera que todo esto viene de los albores de los 70s, donde todavía no habían teclados con flechitas, y también faltaban años todavía para que a la chaviza gamer se les ocurriera usar WASD, como actualmente hacemos. ~~de hecho hay un video de Facu Peralta que lo explica~~

![](/images/blog/250114gestor/adm3akb.png)

En cambio, i3 usa un enfoque parecido pero no el mismo, pues recorre estos controles a justamente la posición tradicional de tu mano derecha, para que si tienes una técnica correcta de teclado, no tengas que mover los dedos en absoluto de esta posición para desplazarte.
Esto es conflictivo si no usas VIM, porque vendrás de usar las flechitas, pero lo es también si lo usas, porque entonces tendrías que configurar tu i3 para moverte con los bindings de VIM, o configurar tu VIM para moverte como lo haces con i3 (para tener un estándar en toda tu computadora claro está). Yo elegí la primera opción.

O, si no quieres aprender estos bindings, siempre puedes cambiarlo a las teclas que tu quieras, o navegar con el mouse, el mundo es tuyo, y ese es justamente el propósito de tener un gestor de ventanas.

## Programas varios
Un gestor de ventanas no vendrá equipado con cualquier programa que puedas necesitar, ya que justamente la sencillez de los mismos viene de que, como vimos previamente, solo te proveen el medio para moverte entre las ventanas de los programas que puedas abrir, no te vendrán con otra cosa.
Esto lo tienes que tener en cuenta incluso para las cosas más triviales, como explorar los archivos de tu computadora, conectarte a una red WIFI, etc.
Si vienes de un entorno de escritorio, lo más probable es que los programas de este mismo persistan, y todos los que hayas instalado hasta el momento.
Eso entonces te permitiría, por ejemplo, si vienes de GNOME o KDE, usar los programas de estos mismos para todas las necesidades que puedas requerir, y si ya tenías un navegador instalado, lo puedes seguir abriendo.
Pero si no fue así, entonces tienes que considerar que necesitas instalar todos los programas que necesites usar, y que ahora no tienes una interfaz gráfica para hacerlo, así que ahora tendrás que usar la consola; aunque si estás leyendo esto es porque probablemente estás usando Linux, por lo que en realidad no deberías de tener muchos problemas para instalar programas usando el gestor de paquetes de tu distribución.

## Después de los problemas principales.

Una vez configurando esto, en realidad ya tienes algo bastante usable, solamente necesitas paciencia para aprenderte los comandos en teclado, porque aquí no hay botones, y listo, esa es toda la curva de dificultad que necesitarás para usarlo. Pero si quieres realmente aprovecharlo, entonces deberías de entrar a la parte por la que estamos aquí en estos momentos, y eso es la configurabilidad.
Y es que un gestor de ventanas puede ser tan complejo como tú lo quieras hacer, o tan simple como exactamente tú lo quieras hacer. Cualquier cosa que te moleste la puedes cambiar. Ejemplo de esto son las tantas publicaciones en reddit de r/unixporn, donde la gente ~~la mera elite de los ñoños~~ se junta para compartir sus configuraciones de gestores de ventanas.

![](/images/blog/250114gestor/ejemploi3.png)

Y por ejemplo, mi configuración final terminó siendo esta

![](/images/blog/250114gestor/mientorno.png)

# Ventajas y desventajas finales
Y ahora, podemos comenzar a platicar sobre las ventajas que me ha traído usar un gestor de ventanas. Que no son pocas.

## Ventajas

### Simplicidad
Como te platiqué previamente, un gestor de ventanas no viene con otra cosa que no sea él mismo. Cualquier otra cosa adicional que necesites la vas a tener que instalar tú. Viendolo como ventaja (aunque también lo veremos como desventaja más adelante), esto significa que cualquier programa que exista en tu computadora es un programa que tú mismo decidiste instalar, en tu infinita sabiduría sobre tu flujo de trabajo.

### Rapidez
Un gestor de ventanas, por lo general, suele manejarse usando atajos de teclado. Esto ya que, como vimos previamente, no tienes menús para navegar entre tus programas, ni iconos para abrir programas rápidamente, o al menos no en un inicio (podrías tenerlo, al final del día todo esto se trata de personalización).
Esto trae una curva de dificultad más pronunciada, pues tienes que aprender todos estos atajos, pero una vez aprendes a navegar sobre tu gestor de ventana usando los atajos de teclado, encontrarás que tu fluidez para abrir y cerrar ventanas, moverte entre ellas y reposicionarlas a tu gusto es potencialmente mucho más rápido que en un entorno de escritorio.

### Uso de recursos menor
Los entornos de escritorio normalmente suelen venir con mucho software adicional que corre tareas de fondo mientras estás trabajando. No me atrevo a decir que es _bloatware_ porque honestamente, usar esta palabra a veces es una cuestión delicada considerando que cada usuario tiene sus propias necesidades ~~a ti te molesta, pero probablemente a tu abuelita le haya encantado ver que su computadora con Windows ya venía con Candy Crush instalado~~. Pero con un gestor de ventanas, en principio, deberías de tener la certeza de que cualquier cosa que esté corriendo en tu computadora está ahí porque tú la quisiste. Esto también incluye efectos visuales, animaciones, etc, etc.
Por ejemplo, actualmente mi computadora en reposo, con nada abierto, ocupa apenas 400MB de RAM, mientras que por ejemplo con KDE, el consumo en reposo era de aproximadamente 2.5GB, y esto es una cifra parecida con GNOME.

Cada una de estas ventajas es simple pero poderosa, pues en general usar un gestor de ventanas te provee de un control granular muy poderoso sobre cada aspecto de la interfaz de tu computadora, y si sabes usar esto a tu favor, puedes encontrar esto bastante apremiante.

## Desventajas

Pero no todo es bonito, siempre hay que encontrarle algo feo a las cosas.

### Curva de aprendizaje
La experiencia estándar actualmente en entornos de escritorio es usar el mouse para muchas cosas, siempre verás botones, deslizadores, menús, etc.
Esto es lo contrario en los gestores de ventanas, donde te encontrarás con que, como dicho previamente, la gran mayoría (no conozco uno que no, pero siempre daré el beneficio de la duda) están enfocados en ser navegados con atajos de teclado.
Esto cuando lo dominas te trae la rapidez que te señalé como ventaja, pues usar el teclado siempre es inherentemente más rápido una vez lo conviertes en segunda naturaleza, pero mientras lo haces, la curva de aprendizaje de hacerlo es una desventaja pronunciada.

![](/images/blog/250114gestor/i3cheatsheet.png)

Esa tabla de arriba fue mi mejor amigo durante muchos días mientras aprendía a navegar i3, pero una vez lo dominé, todo eso se volvió memoria muscular.

### Integración inexistente
Los programas que tiene un entorno de escritorio (uno bien hecho) están hechos para trabajar en conjunto y proveerte de una experiencia uniforme a través de toda su interfaz. Esto puede llegar a ser extrañado si solías usar mucho estas features, aunque debo decir que no en muchos entornos de escritorio estas integraciones suelen ser tan buenas como para que las extrañes.

### Configuraciónes complejas
Si decides usar un gestor de ventanas tienes que estar ~~preparado pa' los putazos~~ listo para sufrir un rato, pues cada pequeño detalle de tu experiencia debe ser configurado por ti mismo. Como justamente lo mencioné previamente, estás intercambiando mucha usabilidad por configurabilidad, y eso te traerá problemas al inicio, pero el potencial de lograr que tu entorno de trabajo se vuelva algo hecho a tu medida, diseñado por la persona que mejor te conoce: tú mismo.

# Conclusión

Los gestores de ventanas te pueden ofrecer una experiencia de escritorio altamente personalizable y eficiente. Aunque primero, necesitarás una inversión inicial de tiempo para superar todos los problemas que te puede traer el comenzar a diseñar tu propia experiencia de trabajo. Debes aprender los atajos de teclado del gestor que decidas usar, configurarlo a tu gusto, y estar dispuesto a solucionar todos los problema que se te puedan atravesar en este proceso.
Pero una vez lo logras, la recompensa es un entorno hecho a tu medida, diseñado específicamente por tí para tí, y con un control granular sobre cada aspecto de tu interfaz.

Si te interesa, yo te recomiendo que empieces con i3 o con xmonad, pues son los que yo considero los más populares y por lo tanto documentados. Y si quieres inspiración, puedes buscar mis configuraciones personalizadas en Github, las cuales tengo públicas justamente para que puedas tomarlas como referencia y tomar lo que más te agrade.
Espero que este artículo te haya gustado :D
