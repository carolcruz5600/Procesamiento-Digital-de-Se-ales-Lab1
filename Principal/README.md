# **Laboratorio 1 Análisis Estadístico de la Señal** 
En este repositorio se encontrara el desarrollo para el analisis estadistico de una señal electrocardiografica
## Objetivos 
* Importar una señal ECG desde la base de datos PhysioNet.
* Capturar una señal electro fisiológica dada por un generador de señales.
* Agregar diferentes tipos de ruido gaussiano, impulso y tipo artefacto para contaminar la señal.
* Identificar los estadísticos que describen una señal biomédica.
* Determinar los estadísticos de las señales usando dos formas: funciones de programación y de manera manual. 

[Diagramas] 
## Parte A
En esta sección se trabajó con el análisis estadístico de una señal biomédica descargada desde la base de datos PhysioNet. Se importó la señal seleccionada en Python, se generó su representación gráfica y se calcularon los principales estadísticos descriptivos utilizando dos metodologías: primero programando manualmente las fórmulas matemáticas desde cero, y segundo empleando las funciones predefinidas de Python. Los parámetros calculados incluyeron media, desviación estándar, coeficiente de variación, histogramas, función de probabilidad y curtosis, lo que permitió caracterizar completamente el comportamiento estadístico de la señal fisiológica analizada.

[Parte A](https://github.com/carolcruz5600/Procesamiento-Digital-de-Se-ales-Lab1/blob/main/Parte%20A/Proceso_A.md)
## Parte B 
Para esta parte de la práctica se trabajará con una señal fisiológica similar a la que se analizó en la primera parte del laboratorio, pero en lugar de emplear datos que ya se han registrado previamente, se utilizará un generador de señales biológicas. Este nos permite simular de manera controlada una señal de ECG con las frecuencias que se necesiten o deseen. La señal generada será adquirida a través de un DAQ para posteriormente ser almacenada en un código de captura y en un formato **.txt** o **.wfdb** para lograr su análisis.
Una vez capturada y guardada la señal será importada a python, para realizar su representación gráfica y cálculos de sus estadísticos descriptivos que permiten cuantificar su comportamiento.

[Parte B](https://github.com/carolcruz5600/Procesamiento-Digital-de-Se-ales-Lab1/blob/136da857a6735b4a114f9adb2d36dc1d329a2b1f/Parte%20B/Proceso_B.md)
## Parte C
[Parte C](https://github.com/carolcruz5600/Procesamiento-Digital-de-Se-ales-Lab1/blob/136da857a6735b4a114f9adb2d36dc1d329a2b1f/Parte%20C/Proceso_C.md)
