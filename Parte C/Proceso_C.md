# **Parte C - Tipos de Ruidos y SNR**
## **Signal to Noise Ratio (SNR)**
El SNR (o la Relación Señal-Ruido) mide que tan fuerte es la señal útil (o original) en comparación con el ruido que la contamina.

Es muy útil para determinar que tanto está afectando el ruido a nuestra señal original mediante las siguientes clasificaciones:
* **Mayor a 30 dB:** ***Muy limpio*** - Señal clara.
* **20-30 dB:** ***Aceptable alto*** - Ruido perceptible, pero sin disrupciones considerables.
* **10-20 dB:** ***Aceptable*** - Ruido evidente, pero señal utilizable.
* **0-10 dB:** ***Ruido fuerte*** - Señal muy contaminada, difícil de interpretar.
* **Menor a 0 dB:** ***Dominado por ruido*** - Ruido más fuerte que la señal, casi imposible de analizar.

El SNR se calcula mediante la siguiente fórmula:

<img width="373" height="95" alt="image" src="https://github.com/user-attachments/assets/77dafbd4-9870-4b2b-88c5-b6ca39c7985f" />

Donde $SNR_{dB}$ representa el SNR en decibelios, $P_{señal}$ es la potencia de la señal original y $P_{ruido}$ es la potencia del ruido que la afecta.

Adicionalmente, $P_{señal}$ se calcula mediante:

<img width="269" height="109" alt="image" src="https://github.com/user-attachments/assets/47a86d96-e477-4728-a876-8daf115be735" />

Que no es más que la media de la señal elevada al cuadrado.

Finalmente, $P_{ruido}$ se calcula mediante:

<img width="370" height="97" alt="image" src="https://github.com/user-attachments/assets/860c6271-a17b-476c-b73c-d94d3077652c" />

Que es simplemente la media de la diferencia de la señal ruidosa y la señal original.

## Tipos de Ruido y Contaminación de la Señal

> Ruido Gaussiano

Es un tipo de ruido aleatorio cuya amplitud sigue la distribución normal o _Gaussiana_. Es uno de los ruidos más comunes en los sistemas electrónicos y de procesamiento de señales. Es posible generarlo en Python empleando ``NumPy``.

> Ruido Impulso

Es un tipo de ruido que aparece de manera súbita y breve en la señal, afectándo partes muy concretas de esta en lugar de toda la señal de manera continua. Se pueden ver como unos picos aislados que pueden tener amplitud positiva o negativa. No existe actualmente una manera de generarlo automáticamente en Python.

> Ruido Tipo Artefacto

Es un tipo de ruido periódico que se superpone a la señal original y suele estar originado por interferencias externas como la red eléctrica, movimientos musculares del paciente o interferencias de otros dispositivos electrónicos. Existen varias maneras de generarlo en Python. Por ejemplo, la librería ``wfdb`` posee muestras de este ruido capturadas en la vida real. También pueden modelarse como una sinusoide de determinada frecuencia y amplitud dependiendo del tipo de señal que se quiera representar.

> ¿Como se puede contaminar la señal?

Como las señales implementadas son arrays de datos cuyas posiciones corresponden al número de muestras, es posible contaminar la señal sumando un nuevo array que contenga la señal ruidosa. De esta manera, los datos de la señal ruidosa se superpondrán con los de la señal original, simulando el fenómeno que ocurre en la vida real.

>[!IMPORTANT]
> Como la señal que es capturada se guarda en un array de determinado tamaño (definido en el momento de la captura), es necesario que el array en donde almacenemos la señal ruidosa con la que vayamos a contaminar la original tenga el mismo número de elementos. En el ejemplo que se presenta, la señal capturada posee un número de muestras $n = 10.000$, por lo que todos los arrays de ruidos generados deben de tener ese mismo tamaño.

## **1. Generación de las Señales Contaminadas en Python-Spyder**
>[!TIP]
> El último paso para general la señal contaminada por un tipo de ruido es sumar la original (en este código llamada ``data``) con la señal ruidosa. Este proceso se repite para cada tipo de señal contaminada.
### **1.1. Ruido Gaussiano**

Como se había mencionado antes, es posible generar este tipo de ruido empleando la función ``np.random.normal(loc, scale, size)`` de ``NumPy``.

<img width="476" height="81" alt="image" src="https://github.com/user-attachments/assets/1e58ca86-1cbb-4f2a-b90e-dbd53cd492a2" />

Donde ``loc`` indica que el ruido se distribuye alrededor de 0, ``scale`` es la desviación estándar $\sigma$ de la muestra y ``size`` es el tamaño de la muestra. Así, ``señal_gaussiano`` es la variable que almacena la señal contaminada por el Ruido Gaussiano.

### **1.2. Ruido Impulso**
Para obtener una señal que simule la del ruido impulso, es necesario realizar algunos pasos extra que se describirán brevemente a continuación.

<img width="748" height="123" alt="image" src="https://github.com/user-attachments/assets/628c9ca2-7e86-42a2-8433-5d8bec3f0f1d" />

Inicialmente, se crea un array``ruido_impulso`` lleno de ``0`` con la cantidad de datos $n$ de nuestra señal con ``np.zeros(n)``, luego se crea un nuevo array ``indices`` con una cantidad aleatoria de ``1`` en un array de ``0`` de tamaño $n$ con ``np.random.choice`` y ``p`` representa la probabilidad de aparecer de cada número, donde finalmente habrán más ``0`` que ``1``, simbolizando los impulsos. Por último, se multiplica ``indices`` con un nuevo array que contiene ``1`` y ``-1`` simbolizando impulsos positivos y negativos con una amplitud de ``1.5``. La variable ``ruido_impulso`` es la encargada de guardar el ruido impulso, y ``señal_impulso`` es donde se guarda la señal contaminada por el Ruido Impulso.

### **1.3. Ruido Tipo Artefacto**
Existen varias opciones para generar este ruido en Python, pero para simplificar un poco el desarrollo, se optó por generar una señal sinusoidal que modele la interferencia de la red eléctrica. Puede construirse de manera sencilla con la función ``sin`` de ``NumPy``, amplitud ``0.2`` y frecuencia de ``60`` Hz. La variable ``señal_artefacto`` es la encargada de almacenar la señal contaminada por el Ruido Tipo Artefacto.

<img width="476" height="82" alt="image" src="https://github.com/user-attachments/assets/6ca00392-f895-41db-9496-6b02c3100562" />

>[!NOTE]
>Se incluyó un parámetro `t`, definido por ``t = np.linspace(0, T, n, endpoint=False)`` que crea un vector tiempo empleando parámetros de la captura de la señal original como ``n`` y la duración ``T`` dada por $T=\frac{n}{fs}$.

## **2. Potencias de las Señales**
Únicamente hacen falta las potencias de nuestra señal original y nuestras señales contaminadas para calcular el SNR de cada una de ellas. Estas potencias pueden ser calculadas de manera sencilla empleando únicamente ``NumPy`` y las fórmulas anteriormente mencionadas.

<img width="704" height="120" alt="image" src="https://github.com/user-attachments/assets/7816852e-725d-4503-a135-2c482761b06c" />

## **3. Cálculo del SNR de cada señal contaminada**
De manera directa, aplicamos la fórmula del SNR anteriormente mencionada empleando las potencias anteriormente calculadas.

<img width="621" height="111" alt="image" src="https://github.com/user-attachments/assets/8f8be22b-b9b7-4c83-a028-f2cab840a748" />

Por último, se muestran los valores de SNR correspondientes a cada tipo de señal contaminada.

<img width="564" height="142" alt="image" src="https://github.com/user-attachments/assets/ca818103-5a65-4870-bbdb-b0c7c8673d3b" />

## **4. Discusión**
Es posible realizar varias observaciones al ver el comportamiento del código y los valores de SNR que arroja en cada ejecución. Como se están empleando funciones de carácter aleatorio como ``np.random.normal`` que modifican parámetros de las señales de ruido (como la cantidad de ``0`` y ``1`` en la definición del ruido impulso), en cada ejecución obtendremos un valor diferente de SNR (a excepción del artefacto). No obstante, es posible observar la tendencia que posee cada tipo de ruido de degradar la señal en mayor o menor medida, además de poder jugar con parámetros como las amplitudes para comprobar que tanto pueden llegar a comprometer la señal original.

En una de las ejecuciones, se obtuvieron los siguientes valores de SNR:
* **Gaussiano** = 3.28 dB
* **Impulso** = 5.44 dB
* **Artefacto** = 6.28 dB

Basándose en los datos, podemos afirmar que, con los parámetros que están definidos en el código, las señales ruido afectaron de manera considerable la señal original, perteneciendo a la categoría de ***Ruido fuerte***, que simboliza una gran similitud de intensidad si comparamos los ruidos con la señal original. Para cada caso de ruido particular, es valioso destacar ciertas características:
> Ruido Gaussiano

El que más afectó a la señal, puede atribuirse no solamente a su amplitud, sino a que es constante a lo largo de la señal, afectando más parte de la misma.
> Ruido Impulso

Menos afectación, que puede ser atribuída a su carácter de aparición espontánea. Si aumentamos la cantidad de impulsos así como la amplitud de estos, el SNR bajará simbolizando una mayor disrupción.
> Ruido Tipo Artefacto

El que menos afectó, probablemente gracias a su pequeña amplitud ``0.2``, que si aumenta, con total seguridad reduirá el SNR. Su componente de frecuencia también es relevante, si este resulta ser parte fundamental de nuestra señal, también afectará considerablemente el SNR y la calidad de la misma.

## **5. Conclusiones**
La parte C del laboratorio permitió reconocer la función e importancia del SNR en el Procesamiento Digital de Señales, al identificar con mayor precisión la calidad de una señal y, con ello, su aplicabilidad en distintos análisis o mediciones. Asimismo, fortaleció la comprensión de los diferentes tipos de ruido y su efecto al superponerse con una señal más compleja, además de mostrar cómo generarlos en Python y evaluar su impacto contaminante. Finalmente, se resalta la importancia del tratamiento adecuado de las señales biológicas capturadas, ya que, debido a su baja amplitud, son altamente vulnerables a la interferencia de múltiples ruidos que pueden dificultar su interpretación y comprometer un diagnóstico oportuno.

## **6. Archivo Python-Spyder**
Documento de Python: [Partes B y C - Lab 1 PDS.py](https://github.com/user-attachments/files/21960513/Partes.B.y.C.-.Lab.1.PDS.py)


