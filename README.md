Descripción del dataset personalizado

El dataset proporcionado contiene información extraída de archivos ejecutables de
Windows, tanto maliciosos como benignos. Se utilizaron características híbridas,
que incluyen contenido binario hexadecimal y llamadas a bibliotecas DLL (Dynamic
Link Libraries). A continuación, se detallan características clave del dataset:
	*Tamaño: 373 muestras (301 maliciosas, 72 benignas)
	*Desbalance: Prevalencia de muestras maliciosas
	*Características: 531 características representadas como F_1 a F_531
	*Etiqueta: Columna indicando si el archivo es malicioso o no (true para malware)
	*Nota: Las características binarias se representan numéricamente por simplicidad (F_1, F_2, etc.)

Se realizó una exploración de los datos en donde se pudo determinar que no existían valores nulos, además se realizó el procedimiento para renombrar las etiquetas donde non-malicious' es igual a 0, y 'malicious' es igual a 1.
Además, se realizó el procedimiento para separar X que son todos los elementos a excepción de la columna label y Y como columna única que especifica el label (si es malicioso o no)

Se realizó el balanceo de las variables aplicando un sobre muestreo (oversampling) para el ajuste de las variables.
Se normalizaron las variables a través del StandardScaler para poder manejar la sobredimensionalidad y el balanceo de las variables.


Técnicas de aprendizaje automático utilizadas y justificación de su elección

Realizando una investigación acorde a una investigación de la universidad de Cornell manifiesta que las tecnicas de ML más usados para el manejo de problemas de ciberseguridad son:
	*árboles de decisión
	*Redes Neuronales convolucionales (CNNs)
	*Máquina de Soporte Vectorial (SVM)
	*K-means Classifier
	*Gaussian Mixture Models (GMMs)
Para reducir el sobreajuste y mejorar la precision y robustez (Ensemble Learning)
	*Random Forest
	*Gradient Boosting Classifier
Por Deep Learning
	*Redes Neuronales Profundas
	*Redes neuronales recurrentes (RNNs)

Debido al comportamiento de los datos y sabiendo que tienen un comportamiento binario se realizarón la prueba de los siguientes algoritmos para determinar su rendimiento:
	*Gradient Boosting Classifier. Esto con el objetivo de combinar multiples arboles de decisión de forma secuencial para mejorar la precision y robustez y reducir el riesgo de 	sobreajuste
	*Clasificador de perceptrón multicapa (MLP) que se basa en redes neuronales artificiales para resolver problemas de clasificacion. Este algorítmo como representante de modelos de clasificacion de aprendizaje automatico
	*SVM Se realizo para la eficiencia en espacios de alta dimensionalidad (531 en este caso) con esto mejora el cojunto de datos. Además busca la generalización para prevenir el 	sobreajuste dandole una robustez en este item y el manejo adecuado de conjuntos de datos desequilibrados.
	*Random Forest Classifier. Se usó este algortimo debido al manejo sólido de caracteristicas heterogeneas y robustez al sobreajuste y ayuda mucho a la buena interpretación de los 	resultados.



Resultados del entrenamiento y la evaluación del modelo

**********************Gradient Boosting Classifier********************************************
Basado en los resultados obtenidos del modelo Gradient Boosting Classifier, se puede concluir lo siguiente:

El modelo ha logrado una alta precisión global de 0.9556, lo que indica que es capaz de clasificar correctamente la gran mayoría de las muestras en el conjunto de datos.

Para la clase 0 (no malware), se ha obtenido una precisión de 0.8462. Esto significa que el modelo clasifica correctamente el 84.62% de las muestras que realmente pertenecen a la clase no malware. Aunque ligeramente menor que la precisión perfecta, este resultado sigue siendo bastante alto y sugiere que el modelo es eficaz para identificar software benigno.

Para la clase 1 (malware), se ha obtenido una precisión de 1.0, lo que indica que el modelo clasifica todas las muestras de malware correctamente. Este resultado es especialmente notable, ya que significa que el modelo no ha cometido ningún error al identificar software malicioso.

En resumen, el modelo Gradient Boosting Classifier ha demostrado ser altamente efectivo en la clasificación de malware, logrando una alta precisión global y precisión perfecta en la clasificación de malware. Estos resultados sugieren que el modelo es adecuado para su aplicación en la detección de amenazas de seguridad informática y puede proporcionar una defensa robusta contra software malicioso.

**********************Support Vector Machine********************************************
Mediante los resultados obtenidos del modelo Support Vector Machine, podemos evidenciar una exactitud del 0.978 con lo cual se demuestra que el modelo es altamente preciso y que puede identificar correctamente el 97% de la muestra analizada.

En conclusión este modelo es altamente efectivo dado su nivel de exactitud. 


**********************Random Forest Classifier********************************************
Con Base en los resultados obtenidos del modelo Random Forest Classifier, podemos concluir en lo siguiente:

El modelo cuenta con una precisión razonable, ya que ha conseguido una excactitud del 0.93 resultado que demuestra que el modelo puede identificar correctamente razonablemente las muestras del conjunto de datos. 

Especificamente: 

Para la clase 0 (no malware), se ha obtenido una excactitud del 1.0, lo que revela que su clasificación es del 100% sobre las muestras que realmente no son malware.
Por otro lado en la clase 1 (malware) revela una excactitud moderada del 0.92, lo cual indica que el 92% de las muestras identificadas como malware son identificadas correctamente.

En conclusión el modelo Randon Forest Clasifier, demuestra en agregado una alta precisión.


**********************Clasificador de perceptrón multicapa (MLP)*******************************************

Análisis crítico de los resultados del modelo Clasificador de perceptrón multicapa (MLP), dan como resultado lo siguiente: 

El modelo cuenta con una precisión del 0.955 con lo cual se evidencia una alta excactitud en la identificación de las muestras del conjunto de datos. 

Al detalle podemos identificar que en el conjunto de datos clase 0 (no malware), se obtiene un 0.85, demostrando que su nivel de exactitud es del 85% para identificar aquellas aplicaciones que no corresponden a malware. 

Por otro lado respecto de la clase 2 (malware) su nivel de exactitud asciende al 0.98, resultando ser mas efectivo en la identificación de malware con un 98% de excactitud. 

En conclusión el modelo Clasificador de perceptrón multicapa (MLP), demuestra ser razonablemente adecuado en la detección de malware. 

*********Conclusiones Generales*********

Con los resultados obtenidos en el ejercicio, apreciamos que los modelos presentan un alto nivel de detección, y cada uno arroja resultados cercanos y fortalezas en la detección tanto para la clase 0 (no malware) como en la clase 1 (malware). 
