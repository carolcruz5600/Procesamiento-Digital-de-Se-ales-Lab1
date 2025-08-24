# **Parte A - Resultados**
## **Configuración Inicial**
Esta sección importa las librerías esenciales: NumPy para cálculos numéricos, Matplotlib para gráficos, WFDB para leer señales médicas, SciPy para estadísticas avanzadas y Seaborn para visualizaciones elegantes. Es la base técnica que permite procesar y analizar señales ECG de manera correcta.

<img width="60%" alt="image" src="https://github.com/user-attachments/assets/a4a25afc-724f-4265-8f3c-a49a7d6a4f4a" />

## **1. Captura y Visualización de la Señal**
El proceso utiliza la librería WFDB para acceder a registros electrocardiográficos de PhysioNet. La función wfdb.rdsamp() carga la señal original de 87,125,000 muestras a 1000 Hz y extrae un segmento de 20,000 muestras para análisis estadístico. Esta segmentación proporciona representatividad adecuada manteniendo eficiencia computacional.
La visualización revela características morfológicas típicas del ECG: complejos QRS regulares, amplitudes entre -500 μV y +3000 μV, y periodicidad consistente indicativa de ritmo cardíaco normal.

> ### **Código para descargar la señal**

La función wfdb.rdsamp() carga el archivo ECG retornando los datos numéricos y metadatos técnicos del registro. La operación de segmentación signals[80000:100000] extrae específicamente 20,000 muestras del registro original para análisis enfocado. Retorna una tupla con los datos de la señal (signals) y un diccionario con metadatos (fields). En este caso, la ruta accede al archivo 103001_ECG desde Google Drive, correspondiente a un registro de la base MIT-BIH Arrhythmia Database.

<img width="1175" height="305" alt="image" src="https://github.com/user-attachments/assets/d5766fc6-459d-4746-a5ea-b1815a978238" />



> ### **Segmentación y Graficación**

El comando plt.plot() con color='red' genera la representación gráfica lineal de la señal, mientras que plt.xlabel() y plt.ylabel() establecen etiquetado científico con las respectivas unidades. La función plt.show() ejecuta la renderización final del gráfico con las especificaciones de formato establecidas.

<img width="35%" alt="image" src="https://github.com/user-attachments/assets/38ce9ad5-e413-4d95-94b3-5124e02ad47e" />


> ### **Gráfica**

<img width="649" height="492" alt="image" src="https://github.com/user-attachments/assets/8386d383-2673-42a6-9f74-790bafcf6559" />

## **2. Cálculo de Valores Estadístico**

> ### **Método 1: Usando Librerías**
Se emplean funciones optimizadas de NumPy y SciPy para cálculos estadísticos estándar. Los resultados muestran media de 43.35 μV, desviación estándar de 509.03 μV (alta dispersión por naturaleza bifásica de la señal), y curtosis de 16.25 (distribución marcadamente leptocúrtica). El coeficiente de variación de 11.74 confirma variabilidad significativa característica de señales electrocardiográficas. 

<img width="90%" alt="image" src="https://github.com/user-attachments/assets/b926b3f1-b966-4fa3-a401-36a087379455" />

> ### **Método 2: Implementación Manual**
La implementación algorítmica manual replica los cálculos usando estructuras iterativas básicas de Python. Los bucles procesan secuencialmente las 20,000 muestras calculando media, desviación estándar y curtosis según definiciones estadísticas estándar. Los resultados son numéricamente idénticos a los obtenidos con librerías, validando la correcta implementación de los algoritmos fundamentales.

<img width="416" height="694" alt="image" src="https://github.com/user-attachments/assets/191911a1-0f19-4a10-b317-f6d715ea27bc" />

<br>
<img width="432" height="108" alt="image" src="https://github.com/user-attachments/assets/7dfb836b-bd00-46f7-996c-2396cb2a811e" />



## **3. Resultados Estadísticos**
Los cálculos estadísticos muestran una concordancia entre los obtenidos con librerías especializadas y los realizados manualmente, lo que confirma la fiabilidad de ambos procedimientos. La media de 43.35 μV evidencia un ligero desplazamiento positivo respecto al baseline teórico, situación habitual en registros electrocardiográficos debido a pequeñas derivas instrumentales o a variaciones fisiológicas propias del paciente en monitoreos prolongados. La desviación estándar de 509.03 μV refleja la marcada dispersión característica de las señales ECG, originada por la alternancia entre periodos prolongados de baja amplitud correspondientes al baseline y picos súbitos de alta amplitud asociados con los complejos QRS. Por otro lado, el coeficiente de variación de 11.74 cuantifica esta dispersión relativa frente a la media, acorde con la naturaleza rítmica de la actividad cardíaca.

## **4. Análisis de Distribución - Histogramas**
> ### **Método 1: Usando Librerías**

La función plt.hist() construye automáticamente el histograma procesando las 20,000 muestras de la señal. El parámetro bins=35 divide el rango de amplitudes en 35 intervalos equiespaciados, proporcionando resolución adecuada para visualizar la distribución. La configuración edgecolor='black' y color='red' optimiza la presentación visual manteniendo consistencia cromática con la señal original. Los comandos de etiquetado establecen contexto científico apropiado con unidades estándar en microvolts, mientras que plt.grid() añade referencia cuantitativa sin interferir con los datos principales.

<img width="60%" alt="image" src="https://github.com/user-attachments/assets/8cc4518d-3fb0-4319-8248-c873294430d9" />

> ### **Gráfica**

El histograma con 35 intervalos muestra cómo se distribuyen las amplitudes de la señal ECG. La gráfica revela una concentración masiva de datos cerca de cero microvolts, correspondiente a los períodos de reposo entre latidos cardíacos. Esta acumulación es normal teniendo en cuenta que el corazón pasa la mayor parte del tiempo en estado básico entre despolarizaciones.
 
<img width="649" height="492" alt="image" src="https://github.com/user-attachments/assets/4a387727-dd18-4c1e-93dd-97ab4cbf8348" />

> ### **Método 2: Sin usar Librerías**

La construcción manual del histograma se realizó mediante bucles anidados y condiciones que permiten clasificar las muestras en sus respectivos intervalos. El algoritmo calcula de forma automática los rangos y el ancho de cada clase, asignando secuencialmente cada valor. Los resultados obtenidos coinciden con la distribución generada de manera automática, lo que confirma la correcta implementación del procedimiento de clasificación. 

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/124667ea-2641-45d6-a5a1-daa4c1e1b8c2" />

> ### **Gráfica**
> 
<img width="649" height="492" alt="image" src="https://github.com/user-attachments/assets/a0adc495-0328-478c-a32e-8527ba25d11a" />

## **5. Análisis de Curtosis**
La visualización combina un histograma con la estimación de densidad por kernel (KDE) usando seaborn. La curva suavizada muestra un comportamiento altamente leptocúrtico, caracterizado por un pico central muy marcado y colas largas que disminuyen de forma lenta. Esta forma concuerda con el valor de curtosis obtenido (16.25), muy superior al de una distribución normal (3.0).

<img width="545" height="138" alt="image" src="https://github.com/user-attachments/assets/be6dd39d-4d2d-4f39-afa6-98754c292ed2" />

> ### **Gráfica**
> 
<img width="649" height="492" alt="image" src="https://github.com/user-attachments/assets/5a752285-8436-4ac4-a88b-3dc149c7e9f9" />

## **6. Función de Densidad de Probabilidad**

El código emplea plt.hist() con el parámetro density=True que normaliza las frecuencias absolutas transformándolas en densidades de probabilidad. Esta normalización garantiza que el área total bajo el histograma sea igual a 1.0, convirtiendo la representación en una función de densidad válida. La conversión np.array(signals) asegura compatibilidad con las operaciones de normalización, mientras que la configuración de 35 bins mantiene la resolución establecida, permitiendo interpretación directa de las alturas como probabilidades por unidad de voltaje.


<img width="659" height="162" alt="image" src="https://github.com/user-attachments/assets/f40b717e-4252-4216-aa08-064ac1535948" />

> ### **Gráfica**
> 
<img width="649" height="492" alt="image" src="https://github.com/user-attachments/assets/24ad0f94-5ffb-4c19-b80c-504070c4c5ac" />

## **7. Conclusiones**


