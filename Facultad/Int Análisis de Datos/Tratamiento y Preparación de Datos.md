### Principios de la preparación de datos (Garbage In, Garbage Out) (GIGO):
Concepto que afirma que la calidad de los resultados del procesamiento de datos es directamente proporcional a la calidad
 de los datos de entrada que se le proporciona. Si los datos que ingresa es defectuoso, inexactos o de baja calidad ("basura"), la salida generada también sera de  baja calidad o incorrectos.
 Solución: preparación de los datos antes de ingresarlos al sistema de procesamiento. Esto insume en general entre  el 60% y el 70% del tiempo de un proyecto de datos.
 > Que se busca? Que los datos a analizar tengan sentido
 > Son coherentes las cifras que tenemos? Están dentro de un rango aceptable?  
 
#### Anomalías en los datos:
- **Datos duplicados o irrelevantes**:
	- *Datos duplicados*: ocurren cuando se integran fuentes de datos diferentes o por fallas en el control de ingreso de datos.
		- Eje: EL campo No aplicable puede presentarse como N/A, NA, No Aplica 
	- *Datos irrelevantes*: Son aquellos que no influyen o impactan en el problema que se intenta resolver.
		- Eje: si se está analizando el PBI en países asiáticos, tiene sentido incorporar al análisis datos de países europeos o americanos?
- **Datos faltantes**:
	- *Completamente aleatorio (MCAR)*: La ausencia de datos es completamente al azar. La ausencia del dato es accidental e involuntario. No depende de la variable misma.
		- Eje: El atributo incompleto profesión puede relacionarse con el dato Edad: <18 años.
	- *Aleatorios(MAR)*: La ausencia de está relacionada con el parecencia de otros datos observados en el dataset.
		- Eje: A quien votará en las próximas elecciones, número de teléfono personal. Monto de una deuda. En general son datos que no se quieren revelar
	- *No aleatorios (MNAR)*: La ausencia de los datos no es al azar. En este caso el dato faltante es voluntario
		- Eje: Calificaciones de; servicio de WiFi en lugares donde no hay WiFi
	- *Datos estructuralmente faltantes*: La estructura de los datos no representa el negocio.
- **Datos atípicos (Outliers):**
	![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRj0ws-HMcuKFxr6F5INPfzhf3JNCnv75AIdw&s)
	- Un valor atípico es aquel que escapa del rango normal de valores de la variable en estudio. Generalmente se producen por errores en las medidas o describen fenómenos que no representan el funcionamiento común de lo estudiado.
		- Eje: Una persona cuyo valor en la característica altura es de 3 metros, claramente es un valor atípico.
		- Los valores atípicos deben ser analizados. En el ejemplo de la altura una persona de 18 metros tal vez es el producto de un mal ingreso (1,8m).
		- Otro caso: un producto que tiene un precio de $20.000 y normalmente cuesta $35.000 puede estar en descuento o puede ser un precio especial de mayorista 
	- *Causa de los valores atípicos:*
		- Errores de medición: fallos en los equipos o en la toma de datos
		- Errores de entrada: errores humanos al ingresar la información.
		- Fenómenos naturales: desviación inherentes a la población o fenómenos en estudio.
		- Cambios en el comportamiento: Por ejemplo, picos excepcionales de actividad o errores en sistemas.
		- Información valiosa: A veces, un outlier puede ser una observación real que indica algo nuevo o inusual que debe ser investigado.
	- *Detección de valores atípicos:*
		- Gráficos: La forma más sencilla es visualizarlos mediante diagramas de dispersión o histograma, ya que los outliers suelen aparecer aislados.
		- Ordenando los datos: Ordenando el conjunto de datos permite identificar rápidamente valores inusualmente altos o bajos.
		- Métodos estadísticos:
			- Se pueden usar técnicas como las vallas basadas en el rango intercuartílico o para determinar formalmente que puntos son atípicos. Los valores fuera de las vallas son atípicos.
			- Puntuación basada en la distribución normal y desvío estándar de los datos. Los valores más alejados de la media, tienen mayor puntaje.
