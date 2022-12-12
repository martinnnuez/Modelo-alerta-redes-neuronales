# Entrenamiento y validación de un modelo de alerta a partir de series temporales. 

Rodríguez Nuñez Martin, Balzarini Mónica.

* Universidad Nacional de Córdoba, Facultad de Ciencias Agropecuarias, Departamento de estadística y biometría. Córdoba, Argentina.

* Consejo Nacional de Investigaciones Científicas y Técnicas. Córdoba, Argentina.

Mejorar la calidad del aire es uno de los mayores desafíos ambientales de la actualidad. La ciudad de Córdoba, Argentina presenta niveles de contaminación de aire que exceden límites nacionales e internacionales. Su ubicación, topografía y meteorología favorecen condiciones atmosféricas perjudiciales para la salud humana cuando existe interacción con emisiones antropogénicas. Los modelos predictivos de contaminación de aire son un pilar fundamental en la salud pública, dado a que permiten alertar a la población ante condiciones adversas de calidad, en especial en sitios donde no se realiza seguimiento de los niveles de contaminación, como lo es esta ciudad. El objetivo de este trabajo es evaluar distintas metodologías de entrenamiento y validación de modelos predictivos para determinar cual permite el mejor ajuste de un sistema de alerta temprana de contaminación de aire. La finalidad del modelo es predecir la variable respuesta en observaciones con las cuales no se ha entrenado, es decir que no ha “visto” antes. El error mostrado por defecto tras entrenar un modelo suele ser el error de entrenamiento, error que comete el modelo al predecir las observaciones que han formado parte del conjunto de datos de entrenamiento. Si bien estos permiten entender cómo se desarrolla el aprendizaje del modelo (estudio de residuos), no es una estimación realista de cómo se comporta ante nuevas observaciones. Para conseguir una estimación más certera, se tiene que recurrir a un conjunto de testeo, o bien emplear estrategias de validación basadas en el re muestreo. Los métodos de validación son estrategias que permiten estimar la capacidad predictiva de los modelos cuando se aplican a nuevas observaciones, haciendo uso únicamente de los datos de entrenamiento. Se basan en el ajuste del modelo empleando un subconjunto de los datos y su evaluación en las observaciones restantes. Este proceso se repite múltiples veces y los resultados se agregan, al realizar múltiples repeticiones se compensan posibles desviaciones que puedan surgir por el reparto aleatorio de los datos. La diferencia entre métodos radica en la forma en la que se generan los subconjuntos de entrenamiento y validación. Dado a la naturaleza temporal de los datos con los cuales se entrenó el modelo, en este trabajo se evaluaron tres mecanismos de fraccionamiento cuyos algoritmos mantienen al mínimo la destrucción de la secuencialidad existente en las series temporales. Los métodos evaluados fueron K-Fold cross validation, Time Series cross validation y por último un mecanismo diseñado por los autores en el cual se genera un muestreo aleatorio de puntos estratificado con el objetivo de que en cada subconjunto de datos de entrenamiento y testeo se encuentren representadas todas las condiciones temporales posibles de los datos, sin perjudicar la secuencialidad en los datos de entrenamiento. Los distintos métodos se implementaron en Python haciendo principalmente uso de la librería scikit-learn. Los resultados obtenidos muestran que los métodos que ya se encontraban implementados tienen la falencia de que al generar los subconjuntos de entrenamiento y validación no logan una representatividad completa de las diversas condiciones presentes en los datos, lo cual termina impactando en la capacidad predictiva del modelo. De esta forma el modelo predictivo falla al predecir combinaciones de las variables que no formaron parte del set de datos de entrenamiento, de aquí la importancia de generar una representatividad completa de las distintas posibles combinaciones de variables que pueden surgir a partir de los datos. Por otra parte, el mecanismo de evaluación diseñado por los autores permite maximizar la representatividad de las diversas situaciones a las cuales puede enfrentarse el modelo predictivo, al mismo tiempo que minimiza las perturbaciones sobre la secuencialidad existente en el conjunto de datos de entrenamiento. El desempeño del algoritmo predictivo entrenado a través de esta metodología fue ampliamente superior en las distintas bases de datos de testeo y permitió una mejor representación de la información contenida en los datos, disminuyendo a la mitad los errores cometidos por los otros métodos de fraccionamiento al ajustar los mismos modelos predictivos. De esta forma se concluye que para el entrenamiento de un modelo predictivo de alerta a partir de series temporales, debe buscarse maximizar la representatividad de las distintas condiciones posibles existentes en la base de datos tanto en los datos de entrenamiento como de validación, además de preservar la secuencialidad en el set de datos de entrenamiento. De esta forma además de entrenar el modelo predictivo en todo el espectro de situaciones posibles se obtienen estimaciones confiables del error, maximizando su desempeño.

**Modelado predictivo**, **series de tiempo**, **validación**, **machine learninig**.