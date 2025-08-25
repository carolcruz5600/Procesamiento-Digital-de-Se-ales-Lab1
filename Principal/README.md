# **Laboratorio 1 Análisis Estadístico de la Señal** 
En este repositorio se encontrara el desarrollo para el analisis estadistico de una señal electrocardiográfica

## Integrantes
* Laura Valentina Velásquez Castiblanco (5600846)
* Carol Valentina Cruz Becerra (5600845)
* Carlos Felipe Moreno Guzmán (5600881)
  
## Objetivos 
* Importar una señal ECG desde la base de datos PhysioNet.
* Capturar una señal electro fisiológica dada por un generador de señales.
* Agregar diferentes tipos de ruido gaussiano, impulso y tipo artefacto para contaminar la señal.
* Identificar los estadísticos que describen una señal biomédica.
* Determinar los estadísticos de las señales usando dos formas: funciones de programación y de manera manual. 

## Diagramas de Flujo

[Diagrama Parte A](https://github.com/carolcruz5600/Procesamiento-Digital-de-Se-ales-Lab1/blob/main/Imagenes/Esquemas-2.jpg)

[Diagrama Parte B](https://github.com/carolcruz5600/Procesamiento-Digital-de-Se-ales-Lab1/blob/main/Imagenes/Esquemas-3.jpg)

## Parte A
En esta sección se trabajó con el análisis estadístico de una señal biomédica descargada desde la base de datos PhysioNet. Se importó la señal seleccionada en Python, se generó su representación gráfica y se calcularon los principales estadísticos descriptivos utilizando dos metodologías: primero programando manualmente las fórmulas matemáticas desde cero, y segundo empleando las funciones predefinidas de Python. Los parámetros calculados incluyeron media, desviación estándar, coeficiente de variación, histogramas, función de probabilidad y curtosis, lo que permitió caracterizar completamente el comportamiento estadístico de la señal fisiológica analizada.

[Parte A](https://github.com/carolcruz5600/Procesamiento-Digital-de-Se-ales-Lab1/blob/main/Parte%20A/Proceso_A.md)

## Parte B 
Para esta parte de la práctica se trabajará con una señal fisiológica similar a la que se analizó en la primera parte del laboratorio, pero en lugar de emplear datos que ya se han registrado previamente, se utilizará un generador de señales biológicas. Este nos permite simular de manera controlada una señal de ECG con las frecuencias que se necesiten o deseen. La señal generada será adquirida a través de un DAQ para posteriormente ser almacenada en un código de captura y en un formato **.txt** o **.wfdb** para lograr su análisis.
Una vez capturada y guardada la señal será importada a python, para realizar su representación gráfica y cálculos de sus estadísticos descriptivos que permiten cuantificar su comportamiento.

[Parte B](https://github.com/carolcruz5600/Procesamiento-Digital-de-Se-ales-Lab1/blob/136da857a6735b4a114f9adb2d36dc1d329a2b1f/Parte%20B/Proceso_B.md)

### Comparación Parte A y Parte B

Si miramos primero la señal qye se ha tomado del generador que analizamos antes, se nota que estaba centrada en torno a 0 V, con una media de -0.008 V prácticamente pegada al eje, y una desviación estándar baja de 0.291 V, lo que significa que casi todos los valores se quedaban cerca de la línea base sin alejarse mucho. En cambio, en el ECG real que se sacó con PhysioNet, la media quedó en 43.35 μV, arriba de cero, mientras que con la dispersión: la desviación estándar fue de 509.03 μV. Lo que indica que el ECG tomado de la base de datos es mucho más variable que la señal generada en el laboratorio, con subidas y bajadas muy marcadas.

Otra diferencia se encuentra en la curtosis. La señal de la parte B tenía un valor de 20.3, mostrando que estaba concentrada en torno al cero, con picos que también eran presentes pero poco frecuentes. En el ECG, la curtosis fue de 16.25, que se considera a la vez un valor alto. Esto se puede notar en los histogramas: en ambos hay valores acumulados cerca de la línea base, pero en el ECG los picos hacia los valores grandes son más frecuentes porque cada complejo QRS mete saltos muy altos de amplitud.

Si se habla del coeficiente de variación, la señal, aunque tranquila, tenía un CV grande ya que la media era casi cero y eso aumentaba el valor. En cambio, en el ECG el coeficiente fue de 11.74, lo que refleja una variabilidad grande, pero con valores que se acercaban a la realidad debido a que viene de la dinámica propia de los latidos (los momentos de reposo y los picos de actividad). En otras palabras, el ECG tiene más dispersión absoluta, pero en términos relativos la variabilidad se entiende mejor.

## Parte C
En la presente sección, se empleó la señal previamente extraída del generador de señales biológicas y almacenada en formato **.txt**, para contaminarla con diferentes tipos de ruido, como el ***Ruido Gaussiano***, el ***Ruido Impulso*** y ***Ruido Tipo Artefacto***. Posteriormente, se calculó el **SNR** de cada señal contaminada. En la discusión de este apartado, se definirá el SNR con sus respectivas fórmulas e interpretaciones, así como la generación de cada tipo de ruido en Python-Spyder y la forma de contaminación de la señal original.

[Parte C](https://github.com/carolcruz5600/Procesamiento-Digital-de-Se-ales-Lab1/blob/136da857a6735b4a114f9adb2d36dc1d329a2b1f/Parte%20C/Proceso_C.md)
