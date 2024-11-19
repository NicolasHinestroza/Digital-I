# Informe de Práctica I: Electrónica Digital I

## Objetivos

El objetivo de esta práctica es estudiar las características de dispositivos lógicos fabricados en tecnologías TTL y CMOS mediante el análisis teórico de sus especificaciones. Posteriormente, se implementará una operación lógica para observar diferencias en parámetros como tiempo de respuesta, disipación de potencia y fan-out.

## Resumen Teórico

La electrónica digital utiliza diferentes tecnologías para construir circuitos lógicos, y entre las más comunes están las tecnologías **TTL (Transistor-Transistor Logic)** y **CMOS (Complementary Metal-Oxide-Semiconductor)**. Cada tecnología tiene características específicas que afectan el rendimiento y las aplicaciones de los circuitos. En esta práctica se examinan dos negadores:

- **Negador TTL 74LS04**
- **Negador CMOS CD4069**

Estas tecnologías difieren en términos de voltaje de operación, disipación de potencia, tiempos de retardo y capacidad de carga (fan-out), lo que afecta su idoneidad en diferentes aplicaciones electrónicas.



## Circuitos Equivalentes
### Circuito equivalente de: CD4069 


CMOS:<br>
La tecnología CMOS tiene como principio de funcionamiento interno el estar conformada por dos transistores MOSFET, uno de canal N y otro de canal P, los cuales se encuentran complementados, es decir que mientras uno se encuentra activo el otro no. 

Transistor MOSFET canal N:<br>
EL MOSFET de canal N se caracteriza por permitir el paso de corriente cuando el voltaje VGS (Diferencia de potencial entre la puerta y la fuente) es mayor al Voltaje de umbral.
Este es implementado como la conexión entre GND y la salida de la compuerta cuando se encuentra activo.<br>
Transistor MOSFET canal P:<br>
EL MOSFET de canal P se caracteriza por permitir el paso de corriente cuando el voltaje VSG (Diferencia de potencial entre la fuente y la puerta) es mayor al valor absoluto del Voltaje de umbral.
Este es implementado como la conexión entre el voltaje de alimentación y la salida de la compuerta cuando se encuentra activo.

Cuando la entrada está a un voltaje alto, el NMOS se activa (porque V_GS > V_th) y conecta la salida a tierra, lo que da como resultado un cero logico. El PMOS se apaga porque V_GS es demasiado positivo o en otras palabras (V_SG < ∣Vt_h∣). Cuando la entrada está a un voltaje bajo, el PMOS se activa y conecta la salida a VDD (alimentación), mientras que el NMOS se apaga.

CIRCUITO:

 <img src="/laboratorios/Laboratorio01/Imagenes/NOT-CMOS.JPG" alt="VIH CMOS" width="50%">

 SIMULACIÓN:

  <img src="/laboratorios/Laboratorio01/Imagenes/CMOS-V.JPG" alt="VIH CMOS" width="50%">
 


### Circuito equivalente de: 74LS04


TTL:<br>
La tecnología TTL tiene como principio de funcionamiento interno el estar conformada por un transistor BJT NPN, aunque dependiendo de la configuración se pueden incluir mas componentes. 

Transistor BJT NPN:<br>
EL BJT NPN en un TTL basico se utiliza como interruptor en donde al recibir un 1 logico (Voltaje superior al de umbral) este se activa y se conecta a GND entregando un 0 logico 

En otras configuraciones se puede incluir un segundo transistor NPN (Q2) que cumple la función de "limitador" con el objetivo de evitar que el transistor Q1 (es decir el principal) alcance un voltaje muy elevado.

CIRCUITO:

 <img src="/laboratorios/Laboratorio01/Imagenes/NOT-TTL.JPG" alt="VIH CMOS" width="50%">

 SIMULACIÓN:

  <img src="/laboratorios/Laboratorio01/Imagenes/TTL-V.JPG" alt="VIH CMOS" width="50%">
 

## Comparación de Dispositivos TTL y CMOS



### Características Generales

| Característica               | TTL (74LS04)                    | CMOS (CD4069)                  |
|------------------------------|----------------------------------|--------------------------------|
| Voltaje de operación         | 5V                              | 3V - 15V                      |
| Rango de temperatura         | 0 °C a 70 °C                   | -40 °C a 85 °C                |
| Tiempo de retardo de propagación | 10 ns (más rápido)              | 25-50 ns (más lento)           |
| Disipación de potencia       | 1 mW - 20 mW por compuerta     | 0.2 mW - 10 mW                 |
| Corriente de salida          | 8 mA                           | 6.8 mA                         |
| Número de compuertas         | 6                              | 6                              |
| Número de pines              | 14                             | 14                             |

### Voltajes de Entrada y Salida

Cada dispositivo tiene niveles de voltaje de entrada y salida para distinguir entre estados lógicos de "0" y "1". A continuación, se muestran los voltajes requeridos:

| Parámetro                       | TTL (74LS04)                     | CMOS (CD4069)                 |
|---------------------------------|----------------------------------|-------------------------------|
| **Input High Voltage (VIH)**    | Mínimo 2V                        | Mínimo 3.5V                   |
| **Input Low Voltage (VIL)**     | Máximo 0.8V                      | Máximo 1V                     |
| **Output High Voltage (VOH)**   | Mínimo 2.7V (típico 3.4V)        | Típico 4.95V                  |
| **Output Low Voltage (VOL)**    | Máximo 0.5V (típico 0.35V)       | Máximo 0.05V                  |

### Fan-in y Fan-out

El **fan-out** es la cantidad de dispositivos que una puerta lógica puede controlar en su salida sin pérdida de funcionalidad, mientras que el **fan-in** es la cantidad de entradas que puede manejar una puerta sin degradar la señal. Estos parámetros difieren entre TTL y CMOS:

| Característica             | TTL (74LS04)                 | CMOS (CD4069)                      |
|----------------------------|------------------------------|------------------------------------|
| **Fan-out**                | Hasta 10 puertas TTL         | Más de 50 puertas CMOS             |
| **Fan-in**                 | Limitado a 1-2 entradas      | Número alto de entradas debido a alta impedancia |


### Disipación de Potencia

La disipación de potencia es un parámetro crucial para entender la eficiencia energética de un dispositivo. La tecnología TTL tiene un consumo de energía constante, mientras que la CMOS consume principalmente durante los cambios de estado.

- **TTL (74LS04)**: Disipación de potencia entre 1 mW y 20 mW por compuerta.
- **CMOS (CD4069)**: Disipación de potencia de 0.2 mW a 10 mW, dependiendo de la frecuencia de operación.
  




## Análisis de Parámetros de las Puertas Lógicas CMOS y TTL

### Resultados Experimentales

Se aplicó una señal cuadrada de 1 kHz y se midieron los siguientes parámetros:

| Parámetro | CMOS           | TTL            |
|-----------|----------------|----------------|
| VIH       | 1.04 V         | 2.36 V         |
| VIL       | 0.64 V         | 0.64 V         |
| VOH       | 4.32 V         | 4.08 V         |
| VOL       | 0.24 V         | 0.68 V         |
| UP (tr)   | 92 µs          | 118 µs         |
| DOWN (tf) | 110 µs         | 94 µs          |

---
## Análisis de Medidas


### CMOS


1. **VIH:**
   <img src="/laboratorios/Laboratorio01/Imagenes/VIH%20CMOS.jpeg" alt="VIH CMOS" width="50%">

2. **VIL:**
   <img src="/laboratorios/Laboratorio01/Imagenes/VIL%20CMOS.jpeg" alt="VIL CMOS" width="50%">

3. **VOH:**
   <img src="/laboratorios/Laboratorio01/Imagenes/VOH%20CMOS.jpeg" alt="VOH CMOS" width="50%">

4. **VOL:**
   <img src="/laboratorios/Laboratorio01/Imagenes/VOL%20CMOS.jpeg" alt="VOL CMOS" width="50%">

---

### TTL


1. **VIH:**
   <img src="/laboratorios/Laboratorio01/Imagenes/VIH%20TTL.jpeg" alt="VIH TTL" width="50%">

2. **VIL:**
   <img src="/laboratorios/Laboratorio01/Imagenes/VIL%20TTL.jpeg" alt="VIL TTL" width="50%">

3. **VOH:**
   <img src="/laboratorios/Laboratorio01/Imagenes/VOH%20TTL.jpeg" alt="VOH TTL" width="50%">

4. **VOL:**
   <img src="/laboratorios/Laboratorio01/Imagenes/VOL%20TTL.jpeg" alt="VOL TTL" width="50%">


### Comparación con los Datasheets
## Análisis de Medidas y Comparación con Datasheets

| Parámetro | Experimental CMOS | Datasheet CMOS | Experimental TTL | Datasheet TTL | Cumplimiento |
|-----------|-------------------|----------------|------------------|---------------|--------------|
| **VIH**   | 1.04 V           | Mín. 3.5 V    | 2.36 V          | Mín. 2 V      | CMOS: No TTL: Sí |
| **VIL**   | 0.64 V           | Máx. 1 V      | 0.64 V          | Máx. 0.8 V    | Sí            |
| **VOH**   | 4.32 V           | Típ. 4.95 V   | 4.08 V          | Típ. 3.4 V    | CMOS: Ligeramente inferior, TTL: Sí |
| **VOL**   | 0.24 V           | Máx. 0.05 V   | 0.68 V          | Típ. 0.35 V   | CMOS: Ligeramente superior, TTL: Ligeramente superior |

---

### Gráficos de Entrada y Salida

A continuación, se presentan los gráficos obtenidos en el osciloscopio para las medidas de cada parámetro:

#### CMOS
- ##### Entrada y Salida
<img src="/laboratorios/Laboratorio01/Imagenes/CMOS%20XY.jpeg" alt="Curva de Entrada y Salida CMOS" width="50%">

- ##### Tiempo de Subida 
   <img src="/laboratorios/Laboratorio01/Imagenes/CMOS%20UP.jpeg" alt="Curva de Entrada y Salida CMOS" width="50%">
   
- ##### Tiempo de bajada 
  <img src="/laboratorios/Laboratorio01/Imagenes/CMOS%20DOWN.jpeg" alt="Curva de Entrada y Salida CMOS" width="50%">

#### TTL
- ##### Entrada y Salida:
   <img src="/laboratorios/Laboratorio01/Imagenes/TTL%20XY.jpeg" alt="Curva de Entrada y Salida CMOS" width="50%">
- ##### Tiempo de Subida:
   <img src="/laboratorios/Laboratorio01/Imagenes/SUBIDA%20TTL.jpeg" alt="Curva de Entrada y Salida CMOS" width="50%">
- ##### Tiempo de Bajada**:
   <img src="/laboratorios/Laboratorio01/Imagenes/TTL%20DOWN.jpeg" alt="Curva de Entrada y Salida CMOS" width="50%">

### Oscilador en anillo basado en la compuerta NOT

Los osciladores en anillo basados en la compuerta NOT se caracterizan por generar una señal oscilatoria de alta frecuencia sin necesidad de una señal de entrada externa. Se forma conectando un número impar de compuertas lógicas NOT (inversores) en un bucle cerrado.

Su funcionamiento basico consiste en que al conectar la entrada de la primera compuerta con la salida de la ultima,  se crea una realimentación. Ademas, debido a al retraso inherente en cada compuerta el sistema no logra alcanzar un estado fijo, lo que produce una continua alternancia. 

#### Oscilador en anillo con 3 compuertas NOT

  <img src="/laboratorios/Laboratorio01/Imagenes/Anillo-3.JPG" alt="VIH CMOS" width="50%">
   <img src="/laboratorios/Laboratorio01/Imagenes/Vout-Anillo-3.JPG" alt="VIH CMOS" width="50%">
     <img src="/laboratorios/Laboratorio01/Imagenes/Anillo-3-LAB.jpg" alt="VIH CMOS" width="50%">
     
#### Oscilador en anillo con 5 compuertas NOT

 <img src="/laboratorios/Laboratorio01/Imagenes/Anillo-5.JPG" alt="VIH CMOS" width="50%">
   <img src="/laboratorios/Laboratorio01/Imagenes/Vout-Anillo-5.JPG" alt="VIH CMOS" width="50%">
     <img src="/laboratorios/Laboratorio01/Imagenes/Anillo-5-LAB.jpg" alt="VIH CMOS" width="50%">
  
  





### Conclusiones

1. **CMOS**:
   - El valor experimental de **VIH** no cumple con las especificaciones mínimas del datasheet, posiblemente debido a la configuración experimental o interferencias externas.
   - **VOH** y **VOL** cumplen en mayor medida, aunque **VOL** muestra una ligera desviación.
   - La disipación de potencia y tiempos de transición son bajos, alineándose con la naturaleza eficiente de la tecnología CMOS.

2. **TTL**:
   - Los valores de entrada y salida cumplen con las especificaciones del datasheet. Los tiempos de propagación son más rápidos que los de CMOS, lo que confirma la ventaja de TTL en aplicaciones donde la velocidad es crítica.
   - **VOL** está levemente por encima del valor típico, pero dentro de los límites funcionales.

3. **Recomendación para Aplicaciones**:
   - **CMOS**: Ideal para sistemas de bajo consumo y alta impedancia.
   - **TTL**: Recomendado para aplicaciones donde la velocidad es un factor crítico.

4. **Impacto de la Carga**:
   - Las diferencias observadas en los tiempos de transición y niveles de salida están relacionadas con la carga capacitiva y las condiciones de prueba.

---




