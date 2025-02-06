+++
title = "Sistemas de numeración y sus queveres en CC"
date = "2025-01-30"
description = "Un pequeño resumen de los varios sistemas de numeración que existen, pero enfocado a las ciencias de la computación"
path = "blog/250130basesNumericas"
extra.math = true
+++

### Disclaimer
Tenía otro artículo mucho más interesante y significativo preparado para esta semana, pero la verdad es que era de un tema tan complejo y difícil que nunca pude darle una estructura que me gustara jajaj; así que por lo mientras voy a rifarme este artículo, ya de paso como forma de estudio de un tema que estuve viendo toda la semana en la escuela y me resultaría útil repasarlo de esta manera.

Como todo el día de hoy estuve viendo este tema todo el día en todas mis materias, e incluso en una conversación que tuve con una amiga acerca de binario ~~tqm Uma~~, veo prudente comenzar a asentar mis conocimientos de este tema en algún apunte, y ya de paso, aprovechando lo que dije en el anterior párrafo, pues qué mejor que hacerlo en un post de blog si o q.

# Introducción


Primero que nada me gustaría aclarar que todo este artículo estará escrito en varias instancias ~~no pocas~~ usando notaciones algebráicas y conjuntistas, porque pues soy de Ciencias ~~y soy bárbaro~~... y porque siento que a veces ver ciertas demostraciones de por qué funcionan correctamente algunas cositas puede resultar bastante útil para entender bien lo que estamos haciendo. Una vez dicho esto, vamos a comenzar

## Qué es un sistema numérico?.

Piensa que desde los inicios de la capacidad de razonamiento que tenemos como especie ~~no sé si como especie~~ nuestra capacidad de contar cosas y representar las cantidades en papel (o en piedra si eras de Mesopotamia w) era bastante inherente a nuestra naturaleza de ser humanos. Al principio, esta habilidad era utilizada para llevar registro de cosas tan cotidianas como bienes, intercambios comerciales, y en general cosillas más aterrizadas a la realidad del humano primitivo que las utilizaba. Todavía no habían todas las cosas erizas que las matemáticas nos han traído al día de hoy ~~no es queja~~, pero efectivamente para llegar a todas esas cosas complejas, incluída la computación, primero tenemos que satisfacer esta necesidad de cuantificar la vida.
Es aquí donde nacen los sistemas numéricos, donde podemos afirmar, sin pena ni gloria, que un sistema numérico no es más que:
 - Un conjunto de símbolos, cada uno con un valor asignado
 - Una serie de reglas para operarlos, y en base a éstas, construir valores que no tienen un símbolo asignado, pero pueden ser representados como la suma de varios de estos.
 
Existen dos tipos de sistemas de numeración: los posicionales y los no posicionales. Siendo los primeros los que seguiremos abordando el resto del articulo y los segundos los más tempranos a nuestra historia, generalmente menos poderosos y algo que abordaré nomás porque ya estamos aquí jaja.
 
## Sistemas no posicionales
Aqui podemos encontrar sistemas simples, en los que tenemos una serie de símbolos que representan ciertas cantidades básicas, y la posición de estos mismos no suele darles una jerarquía, como si veremos que pasará con los sistemas posicionales.
No quiero profundizar mucho en estos ~~porque no están tan fancys~~ porque pues no suelen ser utilizados para aplicaciones interesantes, entonces solamente te voy a dar el ejemplo más popular que probablemente ya conozcas: el sistema romano.

![Sistema romano](/images/blog/250130basesNum/simbolos_romanos.gif)

En este sistema y en el resto de sistemas posicionales, generalmente lo único que te importa es colocar todos los símbolos necesarios y sumar las cantidades individualmente. La posición de los símbolos no importa, en el sentido de que el valor del símbolo no cambia dependiendo de la posición de este. Usemos como ejemplo el sistema romano:
 - V = 5
 - IV = 4
 - VI = 6
 - XV = 15
 
En todos estos números romanos el símbolo V vale siempre 5, a pesar de que lo estuvimos iterando en varias posiciones distintas respecto al resto de sus compañeros. Contrario a por ejemplo los siguientes ejemplos de números arábigos ~~los normales vaya~~
 - 1
 - 12
 - 123
 
Donde si te das cuenta, la posición del 1 SÏ hace que valga distinto. En el primer ejemplo vale 1, en el segundo vale 10 y en el tercero vale 100.
 
Puedes observar desde ahora que los sistemas de numeración de este estilo están limitados y son menos poderosos.
Limitados porque, debido a que no tenemos la ventaja de la posición, necesitamos cada vez más símbolos para representar números cada vez más grandes. Si quisieras representar millones en el sistema de numeración romano o egipcio, necesitarías un símbolo para representar millones, tal vez uno para un millón. Luego, si quisieras representar 5 millones o más, necesitarías otro símbolo para representar 5 millones, y así sucesivamente. Puedes entender que esto resulta en un problema de escalabilidad bastante claro.

Y menos poderosos porque los algoritmos para realizar operaciones en estos sistemas suelen ser complicados, bastante complicados; por ejemplo, para sumar en romano se siguen los siguientes pasos:

1. Expresión de los números: Se escriben los números romanos que se van a sumar, uno al lado del otro.

2. Simplificación de símbolos: Se juntan los símbolos iguales y se simplifican siguiendo las reglas del sistema romano:

Cinco "I" se sustituyen por una "V".

Dos "V" se sustituyen por una "X".

Cinco "X" se sustituyen por una "L".

Dos "L" se sustituyen por una "C".

Cinco "C" se sustituyen por una "D".

Dos "D" se sustituyen por una "M".

3. Reordenamiento de símbolos: Se reordenan los símbolos de mayor a menor valor.

4. Resultado: El resultado de la suma es la expresión simplificada y reordenada de los símbolos.

Y de hecho este procedimiento puede resultar propenso a errores si lo sigues al pie de la letra, suma XIV + VII y chance encuentras la bronca.

No quiero profundizar mucho en estos porque en general cada uno tiene su propio juego de reglas bien distinto, ~~y yo odio las cosas que no son estandarizadas entonces mejor acá la dejamos con estos flacx, no me preguntes más, aunque yo sé que nomás me preguntaste la hora~~.

## Sistemas posicionales

Estos son los meros buenos, ya que aquí podemos encontrar aquellos en los que tenemos:

- Una serie de símbolos que nos expresan cantidades básicas

- Dependiendo de la posición de un símbolo, este puede tener un valor distinto para colaborar a nuestro número final.

Además, todos estos sistemas se sirven del mismo conjunto de reglas que ahora te puedo explicar con toda la confianza de que te servirá para aprenderlos todos: desde la numeración maya, pasando por la arábiga decimal, hsata el binario ~~potentísimo pa, también me puedo poner formal de una vez, prepara el traje flacx~~.

Entonces, consideremos lo siguiente:

Un sistema posicional se sirve de un conjunto de símbolos, como en los no posicionales. Llamemos a este conjunto $S$

Para dar un pronto ejemplo, en los números arábigos decimales de toda la vida:
$$
S = \\{0,1,2,3,4,5,6,7,8,9\\}
$$

Y ahora, a cada elemento de este conjunto le llamaremos dígito. Y la cantidad de dígitos que tenemos será la _base_ ($b$) de nuestro sistema numérico. Digamos entonces que:
$$
\\#S = b
$$

Y aquí ya tenemos los conceptos principales de un sistema posicional cualquiera. Dependiendo de la posición de un dígito, el valor base de este mismo será multiplicado por una potencia de la base del sistema y ese será el valor final que colaborará al número de la representación. Para ponernos formales, digamos que sea $N$ un número representado en un sistema de numeración de base $b$. Construimos a $N$ de la siguiente forma:
$$
N = \sum_{i=-k}^{n-1} d_ib^i
$$

O, si lo quieres ver de manera más simple:

![Sistema decimal](/images/blog/250130basesNum/posiconesDecimales.png)

Esto es el Teorema Fundamental de la Numeración, el cual en un ratito vamos a demostrar ~~porque soy bárbaro~~. 

Antes de eso, no puedo remarcar más el decir que bajo este teorema y este sistema nacen todos los sistemas de numeración posicionales, por poner algunos ejemplos:
- Binario
- Octal
- Decimal
- Hexadecimal
- El maya, el cual era base 20

Entonces, si este teorema y forma son tan importantes entonces considero que estaría fancy demostrarlo. ~~ya wey déjame, soy de Ciencias~~

## Demostración del Teorema Fundamental de la Numeración

Esta demostración se divide en dos partes: primero queremos demostrar que cualquier número que se nos ocurra se puede representar con cualquier base (mayor a 1) y colección de símbolos.

Sea $N$ un número entero positivo, y sea $b$ la base a utilizar, vamos a proceder por inducción sobre N:

- **Caso base:** Si $ N = 0 $, se elige $ k = 0 $ y $ a_0 = 0 $, lo cual cumple con la ecuación.

- **Paso inductivo:** Supongamos que todo número $ m $ tal que $ 0 \leq m < N $ puede representarse en base $ b $. Demostremos que $ N $ también puede representarse de esta forma.

  Aplicamos el algoritmo de la división entera entre $ N $ y $ b $:

  $$
  N = q b + r
  $$

  donde $ 0 \leq r < b $ y $ q = \lfloor N / b \rfloor $.  
  Como $ q $ es menor que $ N $, por la hipótesis inductiva existe una representación en base $ b $:

  $$
  q = a_k b^k + a_{k-1} b^{k-1} + \dots + a_1 b^1 + a_0 b^0
  $$

  Sustituyendo $ q $ en la ecuación de la división, obtenemos:

  $$
  N = (a_k b^k + a_{k-1} b^{k-1} + \dots + a_1 b^1 + a_0 b^0) b + r
  $$

  que reorganizando da:

  $$
  N = a_k b^{k+1} + a_{k-1} b^k + \dots + a_1 b^2 + a_0 b^1 + r b^0.
  $$

  Así, $ N $ también tiene una representación en base $ b $, completando el paso inductivo.

Después, queremos verificar que dicha representación es de hecho única

Supongamos que existe otra representación de $ N $ en base $ b $:

$$
N = a_k b^k + \dots + a_1 b + a_0 = a'_m b^m + \dots + a'_1 b + a'_0.
$$

Sin pérdida de generalidad, supongamos que ambas representaciones tienen la misma longitud $ k $ (rellenamos con ceros si es necesario). Restando ambas ecuaciones:

$$
(a_k - a^\prime_k) b^k + (a_{k-1} - a^\prime_{k-1}) b^{k-1} + \dots + (a_0 - a^\prime_0) b^0 = 0
$$


Dado que cada $ a_i, a'_i $ satisface $ 0 \leq a_i, a'_i < b $, cada diferencia $ (a_i - a'_i) $ está en el intervalo $ (-b+1, b-1) $, lo que implica que la suma ponderada en potencias de $ b $ solo puede ser cero si todos los coeficientes son cero, es decir:

$$
a_i = a'_i \quad \text{para todo } i.
$$

Esto demuestra la unicidad de la representación.

Y con esto hemos terminado ~~en bombiza pa~~, concluyendo que con este teorema y sistemas podemos representar TODOS los números que se nos ocurran de una manera UNICA.

# Va, y todo esto para qué me sirve en Ciencias de la Computación?

Bueno, ahí te va...
Particularmente los sistemas de numeración binarios, octales y hexadecimal van a ser el pan de cada día si te pones a trabajar en programación de bajo nivel ~~en los alambritos decía una profesora~~; porque al final del día todos los circuitos digitales solamente pueden distinguir entre dos estados: encendido y apagado, 0 y 1 pa los cuates, verdadero y falso pa los lógicos.

Entonces, cualquier número que representes en la computadora, y cualquier instrucción que le vayas a dar, y cualquier dirección de memoria a la que quieras acceder, será escrita en binario.

Y aquí nace naturalmente la pregunta de... ok, los sistemas de numeración sirven para representar números enteros positivos, pero cómo le hacemos para representar números negativos y decimales? Bueno, ahí te va.

## Números negativos en binario
Hay que aclarar un problema importante de las computadoras que nos obliga a tomar con pinzas este problema: las computadoras (en esencia) sólo saben sumar. Podríamos como arquitectos de computadoras rifarnos un nuevo chip súper fancy y trucutrú para hacer restas entre dos números positivos, simplemente aclarándole a este nuevo circuito cuál es el restando y cuál es el restado ~~no sé si se llamen así pero ajá~~ pero pues es rudeza innecesaria; si ya sabemos sumar, sólo necesitamos crear una forma de representar números negativos que se porte bonito ~~si tu me lo pides yo me porto bonito~~ con el algoritmo de suma que ya tenemos en las computadoras. 

Para esto, vamos a representar los números negativos en su forma complemento a dos:
- Reservaremos el bit más relevante para el signo, si es 0 es positivo, si es 1 es negativo
- Convertiremos el número a su forma en complemento a 1 (para los cuates, cambia todos los 1s por 0s y viceversa)
- Le sumamos 1

Entonces, por ejemplo, si quisieramos representar el -5 en 4 bits:
5 → 0101
−5 → Complemento a 1: 1010, luego sumamos 1: 1011.

Ahora, fíjate que pasa si sumamos un número positivo con uno negativo con esta solución:

    3−5=3+(−5)

    0011 (3)

    1011 (-5)

    Suma:

    0011

    + 1011

    --------

    1110  (que es -2 en complemento a 2)

Está mágico el asunto no? Con esta solución podemos chambear con los números negativos de manera super fácil y operarlos con los algoritmos del decimal que ya existen.

Esta es la solución que se usa en las computadoras actuales.

## Números de punto flotante

Primero que nada aclarar que de hecho sí puedes representar números fraccionarios en binario, y de hecho de una forma bastante parecida y natural a como esperarías hacerlo con el sistema decimal de toda la vida: colocas un punto, y después de ese punto, todos los números son multiplicados ahora por potencias negativas de tu base. Es decir, de la misma forma en la que 10.5 es lo mismo que $1 * 10 + 0 * 1 + 5 * 10^-1$, podríamos tener un número en binario tal que sea: 10101.11001.

Pero esta forma de chambear no es apropiada, pues en tu memoria no puedes asignar otro valor que no sea 0 o 1 para decirle "e we, aquí está el punto, todo lo que sigue son fracciones"... Bueno, podrías hacerlo, podrías tener números de 32 bits y decirle a la compu que los primeros 16 bits son para representar números enteros y los siguientes 16 para representar la parte fraccionaria del número; pero la bronca nacería en que:

Imaginate que tienes este sistema, y le das tu compu a un arquitecto que quiere construir un puente y va a chambear con números grandotes con casi nada de parte fraccionaria. Estás tirando 16 bits a la basura.

O imagínate que ahora le das tu compu a un ingeniero civil, y necesita operar con números fraccionarios muy pequeños, en la práctica sólo va a tener 16 bits para chambear en esos números pequeñitos... ~~te van a funar~~

Estaría interesante poder recorrer el punto decimal según tus necesidades no? Bueno, es aquí donde nacen las representaciones en punto flotante.

Vamos a chambear con un número de punto flotante de 32bits, aunque también existen convenciones para números de punto flotante de 64 bits (de doble precisión) pero ps el fundamento es el mismo.

El primer bit es para el signo, los siguientes 8 para el exponente (dame chance, ahorita vemos qpd) y los que quedan para la mantisa (dame chance, ahorita vemos qpd x2)

Te acuerdas de la notación científica que viste en la prepa? Esa que te decía que si querías representar un número muy grande... digamos 10000000, podías hacerlo como $1x10^7$, o un número muy pequeño, digamos 0.000023 como $2.3*10^-5$. Bueno, pues el punto flotante se basa en este principio. Tu mantisa es la parte con información de tu número científico, y tu exponente es.... tu exponente....

Pero aquí hay varias peculiaridades a destacar antes de seguir.
 - La parte destinada al exponente tiene un sesgo de 127, es decir, para evitarnos el problemón de números negativos que vimos hace rato, recorremos todos los números 127 lugares. De esta manera, si tenemos 00000000 en nuestra parte exponente, en realidad esto es -127, no 0
 - La mantisa no se guarda en componente a dos si es negativa, pa eso tienes el bit del signo.
 
Para que amarre el concepto, te va un ejemplo.
Tomemos el número decimal **5.75** y veamos cómo se representa en **punto flotante de 32 bits**.

#### Paso 1: Convertir a binario
$ 5.75 $ en binario es:
$$
5.75 = 101.11_2
$$
(101 es 5 en binario, y `.11` es 0.75 en binario).

#### Paso 2: Escribirlo en notación científica binaria
Queremos que el número esté en la forma:

$$
1.xxxx \times 2^n
$$

Movemos el punto decimal hasta después del primer `1`:

$$
1.0111 \times 2^2
$$

Aquí:
- **Mantisa** = `0111` (los bits después del `1.`).
- **Exponente real** = `2`.

#### Paso 3: Obtener el exponente almacenado
El exponente en IEEE 754 se almacena con **bias 127**:

$$
E_{\text{almacenado}} = E_{\text{real}} + 127 = 2 + 127 = 129
$$

129 en binario es `10000001`.

#### Paso 4: Ensamblar los bits
- **Signo** = `0` (porque es positivo).
- **Exponente** = `10000001`.
- **Mantisa** = `01110000000000000000000` (rellenamos con ceros hasta 23 bits).

💾 **Resultado final en binario (32 bits)**:
```
0 10000001 01110000000000000000000
```

Ahora, hay que decir que este proceso no es perfecto, existen varios casos en los que podemos perder precisión cuando los operamos, y de hecho, hay casos en los que ni siquiera necesitamos operarlos para perder precisión, ya sólo por existir pueden ser imprecisos. Pero es lo que hay, y es la solución que se implementa en los sistemas modernos.

# Life hacks y conclusión
Y con esto ya somos unos expertasos en binario y podemos hablar con la computadora de tú por tú, porque ya entendemos lo básico de sistemas de numeración ~~y ya leímos quiubole con el binario de Adal Ramones~~ y podemos operar en binario sin asustarnos...

Pero ahí te va un último tip y con este me despido pq ya me dió sueño, este artículo quedó más largo de lo que esperaba.

## Mejor hexadecimal u octal
Si vas a trabajar con números binarios, no trabajes con números binarios :D

Las computadoras no tienen opción pero para nosotros es bastante feo estar leyendo secuencias grandotas de 0100011111011111... y más considerando que el estándar actual en computadoras es que los números binarios sean de 64 bits o 32 bits, está horrible leer algo así.

Pero para eso vienen los números hexadecimales a salvarnos, pues resulta que puedes representar números binarios en hexadecimal de manera súper fácil, y traducirlos de vuelta de manera súper fácil también. Sólo tienes que partir tu número binario en trozos de 4 dígitos, comenzando por el bit menos relevante, y convertirlos en sus representantes en hexadecimal.

![Binario a hex](/images/blog/250130basesNum/binarytoHex.png)

De esta manera, un número binario de 32 bits pasa a ser un número hexadecimal de 8 dígitos, una buena mejora no?

Este metodo se usa sobre todo por muchas herramientas para referirse a direcciones de memoria, porque generalmente estas son direcciones de 64 bits, y si yo te digo que tu programa está accediendo a la dirección 0xFFF32BB8 ~~me vas a mentar la madre de todas formas~~ es más práctico a que te diga que está en la dirección
11111111111100110010101110111000.

Y con el octal es lo mismo, pero con trozos de 3 en lugar de trozos de 4.

Listo, ahora si ya me voy a dormir jjj.

