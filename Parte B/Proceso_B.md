# Proceso parte B
## Generar la señal 
Utilizando el generador de señal biológica de ECG con una frecuencia de 0,5 a 100 Hz, verificando que la señal este funcionando o se visualice de manera adecuada, se conecta el generador de señales con el DAQ y luego al computador para realizar la correcta captura de datos.
## Captura de datos 
Para la captura de datos se usa una interfaz de python en la cual ayudara a retener la señal ya genereada
* Se necesitan importar librerías de DAQ para que pueda leer los datos y guaradarlos. Importar librerías tambien como scipy, numpy, matplotlib, seaborn para poder realizar gráficas y calcular los estadísticos descriptivos con funciones.
<img width="542" height="115" alt="image" src="https://github.com/user-attachments/assets/d93cb98f-e55a-484c-895f-bc878e41b42e" />

* Se crea una tarea en el NI-DAQ para organizar la adquisición de datos y facilitar la programción. Configurar el canal de entrada analógica: En este caso sera **Dev1/ai1** siendo el despositivo y el canal de entrada. Configurar el muestre con: Frecuencia de muestre (**fs**), tipo de adquisición, cantidad de muestras que se tomaran para el canal (**n**). Leer los datos.

<img width="712" height="95" alt="image" src="https://github.com/user-attachments/assets/05fe1636-d616-4436-bdf7-d66080285720" />

## Grafica de la Señal
![Imagen de WhatsApp 2025-08-24 a las 16 01 25_17408cdb](https://github.com/user-attachments/assets/80958bd5-81f5-4924-a769-b658a0ba7b29)
### Estadístiscos Descriptivos
