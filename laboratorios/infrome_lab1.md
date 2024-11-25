# Informe de Práctica I: Electrónica Digital I

## Índice

1. [Objetivos](#objetivos)
2. [Resumen Teórico](#resumen-teórico)
3. [Comparación de Dispositivos TTL y CMOS](#comparación-de-dispositivos-ttl-y-cmos)
4. [Especificaciones Técnicas](#especificaciones-técnicas)
5. [Conclusiones](#conclusiones)
6. [Instrucciones para la Parte Práctica](#instrucciones-para-la-parte-práctica)

---

## Objetivos

El objetivo de esta práctica es estudiar las características de dispositivos lógicos fabricados en tecnologías TTL y CMOS mediante el análisis teórico de sus especificaciones. Posteriormente, se implementará una operación lógica para observar diferencias en parámetros como tiempo de respuesta, disipación de potencia y fan-out.


## Resumen Teórico

La electrónica digital utiliza diferentes tecnologías para construir circuitos lógicos, y entre las más comunes están las tecnologías **TTL (Transistor-Transistor Logic)** y **CMOS (Complementary Metal-Oxide-Semiconductor)**. Cada tecnología tiene características específicas que afectan el rendimiento y las aplicaciones de los circuitos. En esta práctica se examinan dos negadores:

- **Negador TTL 74LS04**
- **Negador CMOS CD4069**

Estas tecnologías difieren en términos de voltaje de operación, disipación de potencia, tiempos de retardo y capacidad de carga (fan-out), lo que afecta su idoneidad en diferentes aplicaciones electrónicas.

## Comparación de Dispositivos TTL y CMOS

### Características Generales

| Característica               | TTL (74LS04)                    | CMOS (CD4069)                  |
|------------------------------|---------------------------------|--------------------------------|
| Voltaje de operación         | 5V                              | 3V - 18V                       |
| Rango de temperatura         | -55 °C a 125 °C                | -55 °C a 125 °C                |
| Tiempo de retardo de propagación | 10 ns (más rápido)              | 25-50 ns (más lento)           |
| Disipación de potencia       | 1 mW - 20 mW por compuerta     | 0.2 mW - 10 mW                 |
| Corriente de salida          | 8 mA                           | 6.8 mA                         |
| Número de compuertas         | 6                              | 6                              |
| Número de pines              | 14                             | 14                             |

## Especificaciones Técnicas

### Voltajes de Entrada y Salida

Cada dispositivo tiene niveles de voltaje de entrada y salida para distinguir entre estados lógicos de "0" y "1". A continuación, se muestran los voltajes requeridos:

| Parámetro                       | TTL (74LS04)                     | CMOS (CD4069)                 |
|---------------------------------|----------------------------------|-------------------------------|
| **Input High Voltage (VIH)**    | Mínimo 2V                        | Mínimo 5V                     |
| **Input Low Voltage (VIL)**     | Máximo 0.8V                      | Máximo 1V                     |
| **Output High Voltage (VOH)**   | Mínimo 2.5V (típicamente 3.5V)   | Típicamente 4.95V             |
| **Output Low Voltage (VOL)**    | Máximo 0.5V (típicamente 0.35V)  | Máximo 0.5V                   |

### Fan-in y Fan-out

El **fan-out** es la cantidad de dispositivos que una puerta lógica puede controlar en su salida sin pérdida de funcionalidad, mientras que el **fan-in** es la cantidad de entradas que puede manejar una puerta sin degradar la señal. Estos parámetros difieren entre TTL y CMOS:

| Característica             | TTL (74LS04)                 | CMOS (CD4069)                      |
|----------------------------|------------------------------|------------------------------------|
| **Fan-out**                | Hasta 10 puertas TTL         | Más de 50 puertas CMOS             |
| **Fan-in**                 | Limitado a dos entradas      | Puede tener un número alto de entradas debido a la alta impedancia de entrada |

### Disipación de Potencia

La disipación de potencia es un parámetro crucial para entender la eficiencia energética de un dispositivo. La tecnología TTL tiene un consumo de energía constante, mientras que la CMOS consume principalmente durante los cambios de estado.

- **TTL (74LS04)**: Disipación de potencia entre 1 mW y 20 mW por compuerta.
- **CMOS (CD4069)**: Disipación de potencia de 0.2 mW a 10 mW, dependiendo de la frecuencia de operación.

---
### Circuito Implementado
Para este caso, el circuito implementado fue el siguiente:
## Conclusiones

1. **Velocidad de operación**: El dispositivo TTL (74LS04) tiene un tiempo de retardo de propagación más bajo, lo que lo hace adecuado para aplicaciones de alta velocidad. El CMOS (CD4069) es más lento en comparación, pero su bajo consumo de potencia lo hace ideal para aplicaciones de bajo consumo energético.
   
2. **Disipación de potencia**: La tecnología CMOS consume menos energía en estado estático, lo cual es ventajoso en aplicaciones donde la eficiencia energética es crítica, mientras que TTL consume energía constantemente.

3. **Fan-out**: CMOS tiene un fan-out significativamente mayor debido a su alta impedancia de entrada, permitiendo que una salida controle múltiples entradas sin degradación de la señal.

4. **Versatilidad de voltaje**: El CMOS permite un rango de voltaje de operación más amplio (3V - 18V), lo que le da más flexibilidad en diferentes configuraciones de circuitos.

---

## Instrucciones para la Parte Práctica

1. **Observar el Comportamiento de Entrada y Salida**:
   - Medir y graficar $V_{in}$ vs $V_{out}$ para ambos dispositivos para determinar los parámetros $V_{IH}$, $V_{IL}$, $V_{OH}$, y $V_{OL}$.
   - **Instrucciones para insertar imagen**: Aquí deberá incluirse una imagen que muestre los gráficos obtenidos de la relación $V_{in}$ vs $V_{out}$ para ambos dispositivos.

2. **Medición de Tiempos**:
   - Medir el tiempo de subida ($t_r$), tiempo de bajada ($t_f$), tiempo de retardo ($t_{pd}$) y tiempo de almacenamiento ($t_s$).
   - **Instrucciones para insertar imagen**: Aquí deberá incluirse un gráfico de los tiempos medidos en la simulación, comparando ambos dispositivos.

3. **Análisis del Oscilador en Anillo**:
   - Construir osciladores en anillo con diferentes números de inversores y observar la forma de onda y frecuencia de oscilación.
   - **Instrucciones para insertar imagen**: Incluir una imagen del circuito del oscilador en anillo y los resultados de las simulaciones.

4. **Comparación de Simulaciones y Mediciones Reales**:
   - Comparar las mediciones obtenidas en la práctica con los resultados de las simulaciones.
   - **Instrucciones para insertar imagen**: Aquí deberá añadirse una tabla o gráfico comparativo entre las mediciones prácticas y los valores simulados para cada parámetro relevante.

---

