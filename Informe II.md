# Lab02 - Medidor de carga

# Integrantes
David Santiago Díaz Rivera.
Daniel Guillermo Rincón.
Nicolás Daniel Hinestroza García

# Informe

Indice:

1. [Diseño implementado](#diseño-implementado)
2. [Simulaciones](#simulaciones)
3. [Implementación](#implementación)
4. [Preguntas](#preguntas)
5. [Conclusiones](#conclusiones)
6. [Referencias](#referencias)

## Diseño implementado

### Descripción

### Diagramas


## Simulaciones 

<!-- (Incluir las de Digital si hicieron uso de esta herramienta, pero también deben incluir simulaciones realizadas usando un simulador HDL como por ejemplo Icarus Verilog + GTKwave) -->

### Simulación del bloque de alarma de descarga

### Simulación del sumador de 1 y 4 bits

### Simulación del bloque comparador


## Implementación

## Preguntas

1. ¿Qué desafíos pueden surgir al implementar en *hardware* un diseño que funcionaba correctamente en simulación?
El desafío más importante que surgió a la hora de implementar corresponde con la lógica negativa de la FPGA. Lo anterior, debido a que no resulta evidente el comportamiento de este dispositivo, ya que por ejemplo se encontró también que los deep switchs estaban conectados de forma invertida. Por lo tanto, fue necesario hacer modificaciones al código realizado en Verilog por medio de prueba y error, con el fin de conseguir el funcionamiento esperado.


2. Describa el enfoque estructural y comportamental en el contexto de electrónica digital y cómo los implementó en el reto. ¿Qué hace Quartus con cada uno?
En esta práctica se desarrolló un sistema medidor de carga diseñado para monitorear el estado de carga de un banco de baterías compuesto por dos celdas. El objetivo principal fue proporcionar advertencias al usuario según niveles de carga específicos.

Se diseñó un sistema para monitorear un banco de baterías con las siguientes características:
Cada batería se representa con un valor binario de 4 bits (0-15), donde:
0000 (0): Batería completamente descargada.
1111 (15): Batería completamente cargada.

Se deben cumplir los siguientes criterios funcionales:
Alerta por batería descargada: Si alguna batería tiene un valor de 0000, se genera una señal de advertencia (alertaB1 o alertaB2).
Estado crítico del banco de baterías: Si la suma total del nivel de carga es menor o igual al 10% de la carga máxima (≤ 3), se activa una alarma visual o auditiva.

Indicadores de carga: El diseño debe clasificar el nivel de carga total en las categorías crítico, regular y aceptable.
El sistema debía ser implementado de manera modular y escalable, permitiendo futuras expansiones y una mayor claridad en su verificación.
El laboratorio se basó en principios de lógica combinacional. Además, se emplearon herramientas como el Lenguaje de Descripción de Hardware (en este caso, Verilog) y softwares como Digital para realizar esquemáticos, GTKWave para simulaciones, y Quartus para la implementación del código en la FPGA.
A continuación, se explica el sistema utilizando como referencia la figura de Gajski.
Nivel Comportamental:
El propósito de este laboratorio fue diseñar e implementar un sistema de monitoreo para un banco de baterías compuesto por dos celdas. Este sistema debía supervisar los niveles de carga de cada batería y generar advertencias según distintos criterios de carga predefinidos.
Para ello, se implementaron diseños basados en lógica combinacional y se emplearon herramientas como Verilog para modelar el comportamiento del sistema en dos niveles de abstracción principales: estructural y comportamental. Además, se llevó a cabo la validación mediante simulaciones con GTKWave y la implementación en una FPGA utilizando Quartus.
El diseño incluye señales de advertencia que cumplen las siguientes funciones:
Alertar cuando alguna batería esté completamente descargada.
Emitir una alarma si el nivel de carga total del banco está en un estado crítico (<10%).
Clasificar el estado de carga total en tres categorías:
Aceptable: Suma total entre 16 y 30.
Regular: Suma total entre 4 y 15.
Crítico: Suma total entre 1 y 3.

Nivel Estructural:
En este nivel se desarrollaron dos enfoques diferentes, ambos válidos y funcionales.
Código 1:Lógica combinacional pura
El primer código consta de un módulo principal denominado Control_baterias, que incluye las siguientes variables:
Este enfoque implementa todas las operaciones mediante puertas lógicas, incluyendo la clasificación de los niveles de carga.
Módulo principal: Control_baterias
Entradas:
Dos señales de 4 bits (A y B) que representan el nivel de carga de las baterías.
Una señal de 1 bit (Cin).
Salidas:
Señal de 4 bits (S) que representa la suma.
Señales de 1 bit para alertas y clasificación de niveles de carga.
Submódulos incluidos:
full_adder: Realiza la suma de un bit, instanciado cuatro veces para completar la operación de 4 bits.
bateria_cero: Detecta baterías completamente descargadas y activa las señales alertaB1 y alertaB2.
comparadores: Implementa la lógica de clasificación mediante expresiones booleanas generadas en la herramienta Digital.
Implementa la lógica de comparación utilizando una tabla de verdad generada en Digital. Sirve para diferenciar las tres categorìas
La tabla fue transformada automáticamente en código Verilog.
Este módulo también se instancia en el módulo principal.

Código 2: Sentencias de control
En este enfoque, las categorías de carga se implementaron utilizando sentencias if-else dentro del módulo Niveles_Carga.
El código 2 tiene los mismos módulos que el primero, pero hay una diferencia clave en cómo se clasifican las categorías de carga (crítica, regular y aceptable). En el primer código, esta clasificación se hace usando únicamente compuertas lógicas. Por otro lado, en este nuevo código se optó por usar condicionales, ya que Verilog permite realizar este proceso de comparación de manera más sencilla a través de estos.



Nivel Físico
La herramienta utilizada fue la FPGA que tiene lógica negativa. Adicionalmente se menciona que los dips switchs también están negados.


3. ¿Cómo afecta el diseño del sumador y de comparadores al uso de recursos en la FPGA (LUTs, FFs, BRAMs, etc.)? Muestren el uso de recursos de su diseño.

4. ¿Qué impacto tiene aumentar el número de bits de la lectura de cada batería? ¿Qué impacto tiene aumentar el número de baterias del banco? 

5. Describa las diferencias entre los tipos de dato ```wire``` y  ```reg``` en Verilog y compare ambos con el tipo de dato ```logic``` en System Verilog.

6. Únicamente con lo que se vio en clase, describa cómo se usó el bloque ```always```. Enfoque su respuesta hacia la implementación de lógica combinacional.




## Conclusiones


## Referencias
