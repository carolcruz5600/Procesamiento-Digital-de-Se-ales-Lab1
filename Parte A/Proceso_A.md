# **Parte A - Resultados**
### **Configuración Inicial**
Esta sección importa las librerías esenciales: NumPy para cálculos numéricos, Matplotlib para gráficos, WFDB para leer señales médicas, SciPy para estadísticas avanzadas y Seaborn para visualizaciones elegantes. Es la base técnica que permite procesar y analizar señales ECG de manera correcta.

<img width="520" alt="image" src="https://github.com/user-attachments/assets/a4a25afc-724f-4265-8f3c-a49a7d6a4f4a" />

### **1. Captura y Visualización de la Señal**
El proceso utiliza la librería WFDB para acceder a registros electrocardiográficos de PhysioNet. La función wfdb.rdsamp() carga la señal original de 87,125,000 muestras a 1000 Hz y extrae un segmento de 20,000 muestras para análisis estadístico. Esta segmentación proporciona representatividad adecuada manteniendo eficiencia computacional.
La visualización revela características morfológicas típicas del ECG: complejos QRS regulares, amplitudes entre -500 μV y +3000 μV, y periodicidad consistente indicativa de ritmo cardíaco normal.

> **Código para descargar la señal**
<img width="5000" alt="image" src="https://github.com/user-attachments/assets/1853e1c1-0df8-4766-89b5-dccb226970dc" />


La función wfdb.rdsamp() es la interfaz estándar para leer registros biomédicos en formato MIT-BIH de PhysioNet. Retorna una tupla con los datos de la señal (signals) y un diccionario con metadatos (fields). En este caso, la ruta accede al archivo 103001_ECG desde Google Drive, correspondiente a un registro de la base MIT-BIH Arrhythmia Database.

> **Segmentación y Graficación**
<img width="30%" alt="image" src="https://github.com/user-attachments/assets/38ce9ad5-e413-4d95-94b3-5124e02ad47e" />


> **Gráfica**
<img width="649" height="492" alt="image" src="https://github.com/user-attachments/assets/8386d383-2673-42a6-9f74-790bafcf6559" />

### **2. Cálculo de Valores Estadístico**
> **Método 1: Usando Librerías**
Se emplean funciones optimizadas de NumPy y SciPy para cálculos estadísticos estándar. Los resultados muestran media de 43.35 μV, desviación estándar de 509.03 μV (alta dispersión por naturaleza bifásica de la señal), y curtosis de 16.25 (distribución marcadamente leptocúrtica). El coeficiente de variación de 11.74 confirma variabilidad significativa característica de señales electrocardiográficas.

<img width="80%" height="472" alt="image" src="https://github.com/user-attachments/assets/b926b3f1-b966-4fa3-a401-36a087379455" />

> **Método 2: Implementación Manual**
La implementación algorítmica manual replica los cálculos usando estructuras iterativas básicas de Python. Los bucles procesan secuencialmente las 20,000 muestras calculando media, desviación estándar y curtosis según definiciones estadísticas estándar. Los resultados son numéricamente idénticos a los obtenidos con librerías, validando la correcta implementación de los algoritmos fundamentales.

<img width="415" height="718" alt="image" src="https://github.com/user-attachments/assets/417048ad-78e7-4bfc-b4ba-4b50ded9bc5b" />

### **3. Resultados Estadísticos**
Los cálculos estadísticos muestran una concordancia entre los obtenidos con librerías especializadas y los realizados manualmente, lo que confirma la fiabilidad de ambos procedimientos. La media de 43.35 μV evidencia un ligero desplazamiento positivo respecto al baseline teórico, situación habitual en registros electrocardiográficos debido a pequeñas derivas instrumentales o a variaciones fisiológicas propias del paciente en monitoreos prolongados. La desviación estándar de 509.03 μV refleja la marcada dispersión característica de las señales ECG, originada por la alternancia entre periodos prolongados de baja amplitud correspondientes al baseline y picos súbitos de alta amplitud asociados con los complejos QRS.

Por otro lado, el coeficiente de variación de 11.74 cuantifica esta dispersión relativa frente a la media, acorde con la naturaleza rítmica de la actividad cardíaca.

### **4. Análisis de Distribución - Histogramas**
> **Método 1: Usando Librerías**
El histograma con 35 intervalos revela distribución marcadamente asimétrica con concentración máxima cerca de cero (períodos de baseline) y cola derecha extendida hasta 3000 μV (picos de despolarización). Esta morfología es característica de señales biomédicas donde eventos de baja amplitud son frecuentes y eventos de alta amplitud son esporádicos pero significativos.
<img width="715" height="163" alt="image" src="https://github.com/user-attachments/assets/8cc4518d-3fb0-4319-8248-c873294430d9" />

> **Gráfica**
<img width="733" height="570" alt="image" src="https://github.com/user-attachments/assets/4a387727-dd18-4c1e-93dd-97ab4cbf8348" />

> **Método 2: Sin usar Librerías**
La construcción manual implementa clasificación por intervalos mediante bucles anidados y evaluación condicional. El algoritmo determina rangos automáticamente, calcula anchos de intervalo y clasifica cada muestra secuencialmente. Los resultados reproducen fielmente la distribución automatizada, confirmando correcta implementación del algoritmo de construcción de histogramas.
<img width="878" height="520" alt="image" src="https://github.com/user-attachments/assets/124667ea-2641-45d6-a5a1-daa4c1e1b8c2" />

> **Gráfica**
<img width="719" height="554" alt="image" src="https://github.com/user-attachments/assets/a0adc495-0328-478c-a32e-8527ba25d11a" />

### **5. Análisis de Curtosis**
La visualización combina un histograma con la estimación de densidad por kernel (KDE) usando seaborn. La curva suavizada muestra un comportamiento altamente leptocúrtico, caracterizado por un pico central muy marcado y colas largas que disminuyen de forma lenta. Esta forma concuerda con el valor de curtosis obtenido (16.25), muy superior al de una distribución normal (3.0).
<img width="545" height="138" alt="image" src="https://github.com/user-attachments/assets/be6dd39d-4d2d-4f39-afa6-98754c292ed2" />

> **Gráfica**
<img width="728" height="569" alt="image" src="https://github.com/user-attachments/assets/5a752285-8436-4ac4-a88b-3dc149c7e9f9" />

### **6. Función de Densidad de Probabilidad**
La normalización del histograma (density=True) transforma frecuencias absolutas en densidades de probabilidad donde el área total equivale a la unidad. Esta representación facilita interpretación probabilística: aproximadamente 0.003 de probabilidad para amplitudes cercanas a cero, con probabilidades decrecientes hacia valores extremos. Es fundamental para modelado probabilístico de señales cardíacas.
<img width="659" height="162" alt="image" src="https://github.com/user-attachments/assets/f40b717e-4252-4216-aa08-064ac1535948" />

> **Gráfica**
<img width="738" height="568" alt="image" src="https://github.com/user-attachments/assets/24ad0f94-5ffb-4c19-b80c-504070c4c5ac" />

### **7. Conclusiones**


