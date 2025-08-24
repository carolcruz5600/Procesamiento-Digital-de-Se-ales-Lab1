# Parte B
## Configuración Librerias
Para la captura de datos se usa una interfaz de python en la cual ayudara a retener la señal ya genereada
* Se necesitan importar librerías de DAQ para que pueda leer los datos y guaradarlos. Importar librerías tambien como scipy, numpy, matplotlib, seaborn para poder realizar gráficas y calcular los estadísticos descriptivos con funciones.
<img width="542" height="115" alt="image" src="https://github.com/user-attachments/assets/d93cb98f-e55a-484c-895f-bc878e41b42e" />

## 1. Generación y captura de la señal 

### **Reproducción de la señal**

Utilizando el generador de señal biológica de ECG con una frecuencia de 0,5 a 100 Hz, verificando que la señal este funcionando o se visualice de manera adecuada, se conecta el generador de señales con el DAQ y luego al computador para realizar la correcta captura de datos. 
Para la captura de datos se usa una interfaz de python en la cual ayudara a retener la señal ya genereada
Se necesitan importar librerías de DAQ para que pueda leer los datos y guaradarlos. Importar librerías tambien como scipy, numpy, matplotlib, seaborn para poder realizar gráficas y calcular los estadísticos descriptivos con funciones.

### **Captura de la señal**

<img width="712" height="95" alt="image" src="https://github.com/user-attachments/assets/05fe1636-d616-4436-bdf7-d66080285720" />

Se crea una tarea en el NI-DAQ para organizar la adquisición de datos y facilitar la programción. Configurar el canal de entrada analógica: En este caso sera **Dev1/ai1** siendo el despositivo y el canal de entrada. Configurar el muestre con: Frecuencia de muestre (**fs**), tipo de adquisición, cantidad de muestras que se tomaran para el canal (**n**). Leer los datos.


## 2. Grafica de la Señal

![Imagen de WhatsApp 2025-08-24 a las 16 01 25_17408cdb](https://github.com/user-attachments/assets/80958bd5-81f5-4924-a769-b658a0ba7b29)

## 3. Estadístiscos Descriptivos
<img width="462" height="189" alt="image" src="https://github.com/user-attachments/assets/9dc0f106-5b1f-4391-8641-4c5eaba16d3c" />

Con las funciones que tenemos en el codigo nos dan valores de:

* __Media:__ -0.008
* __Desviación Estandar:__ 0.291
* __Coeficiente de Variación:__ -35.19
* __Curtosis:__ 20.312

La señal analizada presenta una media de **-0.008**, indicando que los datos se encuentran centrados alrededor del eje horizontal. La desviación estandar muestra que los valores de la señal se dispersaen promedio tres décimas alrededor de la media correspondiendo a una variabilidad moderada. Siendo no completamente uniforme pero tampoco presentando fluctuaciones excesivas en relación con la amplitud.
## 4. Histograma
### Programación
<img width="411" height="90" alt="image" src="https://github.com/user-attachments/assets/de8a4b75-a070-468e-bb79-d0db8ac9e5da" />

### Grafica

![Imagen de WhatsApp 2025-08-24 a las 16 01 34_1183e47a](https://github.com/user-attachments/assets/f7f9024d-9a48-4f40-9cdd-f2c03896ba6c)

El histograma permite visualizar la forma en la que están distribuidos los datos, en este caso se evidencia que los datos que se centran entre 0.0 v tienen un pico con más de 8000 repeticiones lo que concuerda con lo que nos dio en la media.

## 5. Curtosis
### Programación
<img width="446" height="94" alt="image" src="https://github.com/user-attachments/assets/b1e6e7b8-3ba8-405c-95cd-1dd016b4d1c7" />

### Curtosis Gráfico
![Imagen de WhatsApp 2025-08-24 a las 16 01 47_c4d78f05](https://github.com/user-attachments/assets/7f3e59b9-1716-4fea-b815-773eb326ce8d)

Se observa qué es un pico muy estrecho y alto, estando en concordancia con el valor de curtosis alto, indicando que se mantiene la concentración marcada de los datos en torno a la media, pero también presenta picos menos frecuentes que pueden corresponder a ondas p y t.

## 6. Función de probabilidad
### Programación 
<img width="524" height="91" alt="image" src="https://github.com/user-attachments/assets/c96627db-ffa6-4d50-b84f-41b8fac22daa" />

### Gráfica
![Imagen de WhatsApp 2025-08-24 a las 16 01 57_0a631310](https://github.com/user-attachments/assets/9079bda7-c66a-47a8-af9e-8646b8fb26e2)

