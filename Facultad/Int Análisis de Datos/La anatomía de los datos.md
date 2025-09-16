## Agenda de la clase

- [ ] Clasificación de los datos en función de su estructura
- [ ] Tipos de variables
- [ ] Organización para el análisis

### :LiDatabase: Ciclo de vida del Análisis de datos

> Recolección > limpieza > análisis exploratorio de datos > construcción del modelo > implementación del modelo

#### Clasificación de los datos según su estructura:

###### **Estructurados:** 
Son datos que se amoldan a un modelo predefinido, organizados en filas y columnas. Son tipos de datos más fáciles de analizar.
*Ejemplo Práctico*: una tabla de clientes en una base de datos SQL, con columnas fijas como ID_Cliente, Apellido, Email , y Fecha_Registro. Donde cada fila es un registro de cliente y casa columna una características o atributo de ese cliente

###### **Semi-estrucurados:** 
En estos casos los datos no se ajustan a una estructura tabular rígida, pero contiene etiquetas o marcadores para separar elementos y jerarquías.
*Ejemplo Práctico*: un archivo JSON devuelto por una API. Por ejemplo, la información de un objeto con número variable de atributos (algunos productos tendrán "color" y "talle", otros tendrán "resolución" y "memoria")

###### **Datos no estructurados:** 
Datos sin una estructura interna predefinida. Constituyen la mayor parte de los datos en la vida diaria.
*Ejemplo Práctico*:  El contenido de los correos electrónicos, los comentarios de una publicación de red social, una imagen JPG, un vídeo MP4, un archivo de audio MP3.

Su análisis requiere técnicas más avanzadas como:
* *Reconocimiento de Entidades Nombradas (NER, por sus siglas en inglés):* es una técnica de PLN que identifica y clasifica información clave (o "entidades") en un texto
* *Análisis de Sentimiento:* También conocido como minería de opiniones, el análisis de sentimiento es otra técnica de PLN que se enfoca en determinar el tono emocional contenido en un texto,
* *Modelado de Temas (Topic Modeling):* es una técnica de ML no supervisada que se utiliza para escanear un conjunto de documentos y descubrir los temas abstractos o asuntos principales que se tratan en ellos.

#### Tipos de Variables (Atributos):
Para realzar el análisis de datos estructurados, es fundamental entender los tipos de variables (columnas/atributos) que contienen.

###### Categóricas (Cualitativas): Describen una cualidad o característica.
* *Normales*: Categorías sin un orden Intrínseco. 
	* Ejemplo Práctico: En un dataset de ventas, la columna Provincia ("Chaco", "Corrientes", "Formosa") es nominal. No hay una provincla que sea "mayor" o "menor" que otra
* *Ordinales*: Categorías que tienen un orden jerárquico clara. 
	* Ejemplo Práctico: Una columna Nivel_Satisfacción con valores como "Malo", "Regular", "Bueno". En este caso hay un claro orden de Jerarquía entre los conceptos.
###### Numéricas (Cuantitativas): Describen una cantidad medible.
* *Discretas*: Valores enteros que se pueden contar. 
	* Ejemplo Práctico: La columna Cantidad_Productos_Carrito en un sistema de e-commerce. Un cliente puede tener 2, 3 o 5 productos pero no 2.5.
* *Continuas*: Valores que pueden tomar cualquier valor numérico dentro de un rango. 
	* Ejemplo Práctico: La columna Precio_ Producto puede ser $1500.50, $2310.75, etc.

#### Organización para el Análisis: El Modelo Tabular
Es la estructura de filas (registros o ejemplos) y columnas (variables) vistas en los datos estructurados. Es la base para trabajar con librerías de tratamientos de datos como Pandas

###### Series:
Conjunto de valores numéricos o no numéricos que están relacionados entre si y se organizan de forma secuencial o temporal.
Es la estructura que representan a una sola columna de una tabla. Es un arreglo *unidimensional* de datos, donde todos lo valores son del mismo tipo.
- Ejemplo Práctico: La columna Precio_producto de un dataset de ventas de una Serie.
###### Dataset o DataFrame:
Es la estructura que representa la tabla completa. Es un conjunto de Series (arreglo *multidimensional*) que comparten el mismo índice (las filas). Es la estructura de datos más utilizada en el análisis de datos.
- Ejemplo Práctico: La tabla entera de Ventas, con sus columnas ID_Ventas, Fechas, ID_Cliente, Provincias, Precio_Producto, etc. Es un DataFrame.



