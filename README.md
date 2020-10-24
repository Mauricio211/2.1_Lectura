![](https://images.cooltext.com/5474909.png)

## Características generales de la arquitectura ARM
ARM es una arquitectura RISC (Reduced Instruction Set Computer=Ordenador
con Conjunto Reducido de Instrucciones) de 32 bits, salvo la versión del core ARMv8-
A que es mixta 32/64 bits (bus de 32 bits con registros de 64 bits). Se trata de una
arquitectura licenciable, quiere decir que la empresa desarrolladora ARM Holdings
diseña la arquitectura, pero son otras compañías las que fabrican y venden los chips,
llevándose ARM Holdings un pequeño porcentaje por la licencia.

### Registros
La arquitectura ARMv6 presenta un conjunto de 17 registros (16 principales más
uno de estado) de 32 bits cada uno.

![](Imagenes/r1.png)

__Registros Generales.__ Su función es el almacenamiento temporal de datos. Son los
13 registros que van R0 hasta R12.

__Registros Especiales.__ Son los últimos 3 registros principales: R13, R14 y R15.
Como son de propósito especial, tienen nombres alternativos.

__Registro CPSR.__ Almacena las banderas condicionales y los bits de control. Los
bits de control definen la habilitación de interrupciones normales (I), interrup-
ciones rápidas (F), modo Thumb 1
(T) y el modo de operación de la CPU.


## El entorno
Los pasos habituales para hacer un programa (en cualquier lenguaje) son los
siguientes: lo primero es escribir el programa en el lenguaje fuente mediante un editor de programas. El resultado es un fichero en un lenguaje que puede entender el
usuario, pero no la máquina. Para traducirlo a lenguaje máquina hay que utilizar
un programa traductor. Éste genera un fichero con la traducción de dicho programa,
pero todavía no es un programa ejecutable.

## Ejemplos de ejecucion en QENU

![](Imagenes/cmd.png)

![](Imagenes/consola.png)

![](Imagenes/amg.png)


## Rotaciones y desplazamientos
En este apartado veremos el funcionamiento de las instrucciones de desplamiento
y rotación. Las instrucciones de desplazamiento pueden ser lógicas o aritméticas.
Los desplazamientos lógicos desplazan los bit del registro fuente introduciendo
ceros (uno o más de uno). El último bit que sale del registro fuente se almacena en el
flag C (figura 1.4). El desplazamiento aritmético hace lo mismo, pero manteniendo
el signo (figura 1.5).

![](Imagenes/amg2.png)


![](https://images.cooltext.com/5474911.png)


## Modos de direccionamiento del ARM
En la arquitectura ARM los accesos a memoria se hacen mediante instrucciones específicas ldr y str (luego veremos las variantes ldm, stm y las preprocesadas push y pop).
El resto de instrucciones toman operandos desde registros o valores inmediatos, sin excepciones. En este caso la arquitectura nos fuerza a que trabajemos de
un modo determinado: primero cargamos los registros desde memoria, luego procesamos el valor de estos registros con el amplio abanico de instrucciones del ARM,
para finalmente volcar los resultados desde registros a memoria.

* __Direccionamiento inmediato.__ El operando fuente es una constante, formando parte de la instrucción.
* __Direccionamiento inmediato con desplazamiento o rotación.__ Es una variante del anterior en la cual se permiten operaciones intermedias sobre los registros.
* __Direccionamiento a memoria, sin actualizar registro puntero.__ Es la forma más sencilla y admite 4 variantes. Después del acceso a memoria ningún registro implicado en el cálculo de la dirección se modifica.
* __Direccionamiento a memoria, actualizando registro puntero.__ En este modo de direccionamiento, el registro que genera la dirección se actualiza con la propia dirección. 

## Tipos de datos
* __Tipos de datos basicos.__En la siguiente tabla se recogen los diferentes tipos de datos básicos que podrán aparecer en los ejemplos, así como su
tamaño y rango de representación.

![](Imagenes/amg3.png)

__Punteros.__ Un puntero siempre ocupa 32 bits y contiene una dirección de memoria.
En ensamblador no tienen tanta utilidad como en C, ya que disponemos de registros
de sobra y es más costoso acceder a las variables a través de los punteros que directamente

__Vectores.__ Todos los elementos de un vector se almacenan en un único bloque de
memoria a partir de una dirección determinada. Los diferentes elementos se almacenan en posiciones consecutivas, de manera que el elemento i está entre los i-1 e i+1.

__Matrices bidimensionales.__ Una matriz bidimensional de N×M elementos se almacena en un único bloque de memoria. Interpretaremos una matriz de N×M como
una matriz con N filas de M elementos cada una. Si cada elemento de la matriz
ocupa B bytes, la matriz ocupará un bloque de M ×N ×B bytes.

## Instrucciones de salto
Las instrucciones de salto pueden producir saltos incondicionales (b y bx) o
saltos condicionales. Cuando saltamos a una etiqueta empleamos b, mientras que
si queremos saltar a un registro lo hacemos con bx. La variante de registro bx la solemos usar como instrucción de retorno de subrutina, raramente tiene otros usos.

## Estructuras de control de alto nivel
Las estructuras for y while se pueden ejecutar un mínimo de 0 iteraciones (si
la primera vez no se cumple la condición). Para programar en ensamblador estas estructuras se utilizan instrucciones de salto condicional.

<a href="http://cooltext.com" target="_top"><img src="https://cooltext.com/images/ct_pixel.gif" width="80" height="15" alt="Cool Text: Logo and Graphics Generator" border="0" /></a>
