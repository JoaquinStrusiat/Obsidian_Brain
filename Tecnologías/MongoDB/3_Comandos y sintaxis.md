### Comandos primarios
Llamaremos comandos primarios a todos aquellos comandos que nos dejen ver las estructura de nuestras bases y acceder a ellas:

`show dbs / show databases`: si estamos parados en la raíz de nuestro gestor este comando nos permite ver las bases de datos que tenemos en nuestro sistema.
``` sh
> show dbs
admin   0.000 KiB
config  0.000 KiB
local   0.000 KiB
```

`use dbName`: para acceder a una base de datos usamos el comando "use" seguido del nombre de la base de datos a la que queremos acceder. 
Una vez que accedemos a una BD podemos observar como el índice de entrada de texto cambiará agregando el nombre de la base de datos en la que nos encontramos, hacemos esta aclaración ya que esto es visible solo en las nuevas versiones de la Shell.
``` sh
> use admin
admin> 
```

`db.getName()`: esta función nos devuelve el nombre de la base de datos en la que estamos parados.
``` sh
admin> db.getName()
admin
```

`show collections`: si nos encontramos dentro de una base de datos podremos ejecutar el siguiente comando para ver las colecciones que se encuentran almacenadas dentro de esta.
```sh
admin> show collections
system.users
system.version
```

### Métodos de manipulación y recuperación:
Mongo nos provee de una serie de métodos que podemos ejecutar para modificar y obtener datos de forma directa sobre nuestros registros "CRUD".
Para poder ejecutar los siguientes comando es necesario que nos paremos sobre una base de datos en específico, utilizando el comando `use nuestraBaseDeDatos`

**Algo muy importante para tener en cuenta es que el sistema gestor de base de datos MongoDB es LAZY por defecto, esto significa que por más que creemos una nueva base de datos en el sistema, esta no será visible hasta que tenga creada al menos una colección, y lo mismo pasa con las colecciones, no serán visibles hasta que tenga al menos un documento**
#### Insert:
la Shell de Mongo nos provee de dos métodos principales para la inserción de nuevos documentos en una colección:

- Para insertar un único documento: `db.collection.insertOne()`
	- Este método recibe por parámetros el documento que queremos almacenar y retorna el documento almacenado incluyendo un `_id` el cual es la clave primaria o identificador único del mismo:
``` js
use sample_mflix

sample_mfli> db.movies.insertOne(
  {
    title: "The Favourite",
    genres: [ "Drama", "History" ],
    runtime: 121,
    rated: "R",
    year: 2018,
    directors: [ "Yorgos Lanthimos" ],
    cast: [ "Olivia Colman", "Emma Stone", "Rachel Weisz" ],
    type: "movie"
  }
)

```

- Para insertar más de un documento: `db.collection.insertMany()`
	- Este método recibe un arreglo con los documentos que queremos almacenar y retorna los documento almacenados incluyendo un `_id` por cada documento el cual es la clave primaria o identificador único del mismo:
``` js
use sample_mflix

sample_mfli> db.movies.insertMany([
   {
      title: "Jurassic World: Fallen Kingdom",
      genres: [ "Action", "Sci-Fi" ],
      runtime: 130,
      rated: "PG-13",
      year: 2018,
      directors: [ "J. A. Bayona" ],
      cast: [ "Chris Pratt", "Bryce Dallas Howard", "Rafe Spall" ],
      type: "movie"
    },
    {
      title: "Tag",
      genres: [ "Comedy", "Action" ],
      runtime: 105,
      rated: "R",
      year: 2018,
      directors: [ "Jeff Tomsic" ],
      cast: [ "Annabelle Wallis", "Jeremy Renner", "Jon Hamm" ],
      type: "movie"
    }
])
```

#### Read:
Mediante este métodos podemos obtener los documentos que tengamos almacenados dentro de una de nuestras colecciones 
- `db.collection.find()`
	- Este método es el equivalente a "SELECT * FROM tableName" en bases de datos sql
``` js
use sample_mflix

sample_mfli> db.movies.find()
sample_mfli>
{
    title: "The Favourite",
    genres: [ "Drama", "History" ],
    runtime: 121,
    rated: "R",
    year: 2018,
    directors: [ "Yorgos Lanthimos" ],
    cast: [ "Olivia Colman", "Emma Stone", "Rachel Weisz" ],
    type: "movie"
},
{
	title: "Jurassic World: Fallen Kingdom",
	genres: [ "Action", "Sci-Fi" ],
	runtime: 130,
	rated: "PG-13",
	year: 2018,
	directors: [ "J. A. Bayona" ],
	cast: [ "Chris Pratt", "Bryce Dallas Howard", "Rafe Spall" ],
	type: "movie"
},
{
	title: "Tag",
	genres: [ "Comedy", "Action" ],
	runtime: 105,
	rated: "R",
	year: 2018,
	directors: [ "Jeff Tomsic" ],
	cast: [ "Annabelle Wallis", "Jeremy Renner", "Jon Hamm" ],
	type: "movie"
}
```

Este es uno de los métodos más importantes ya que es el que nos permite pasar por parámetro una consultas de tipo JSON, que siguiendo una sintaxis simplificada de consulta nos permite filtrar los documentos especificado una condición: `<"key">:<"value">`

- `db.movies.find( { "title": "Jurassic World: Fallen Kingdom" } )`
	- El equivalente en sql: SELECT * FROM movies WHERE title = "Jurassic World: Fallen Kingdom"
``` js
use sample_mflix

sample_mfli> db.movies.find( { "title": "Jurassic World: Fallen Kingdom" } )
sample_mfli>
{
	title: "Jurassic World: Fallen Kingdom",
	genres: [ "Action", "Sci-Fi" ],
	runtime: 130,
	rated: "PG-13",
	year: 2018,
	directors: [ "J. A. Bayona" ],
	cast: [ "Chris Pratt", "Bryce Dallas Howard", "Rafe Spall" ],
	typ
```

:LiLibraryBig: **Sintaxis completa**: [[1_Sintaxis de Consulta|Sintaxis de consulta y Filtros]]

#### Update:
La Shell de MongoDB proporciona los siguientes métodos para actualizar documentos en una colección:
-  Para actualizar un solo documento, utilice `db.collection.updateOne(filter, update, options)`. 
	- **filter**: Especifica el criterio para encontrar el documento que quieres actualizar. Es un documento de consulta que define qué registros deben ser considerados.
	- **update**: Describe las modificaciones que se deben aplicar al documento seleccionado.
		- *Operadores Básicos:*
			- **$set**: Establece el valor de un campo específico. Si el campo no existe, lo crea.
				 ```db.collection.updateOne({ _id: 1 }, { $set: { neme: "Alice" } });```
			- **$unset**: Elimina un campo del documento.
				- `db.collection.updateOne({ id: 1 }, { $unset: { age: "" } });`
			- **$inc**: Incrementa el valor de un campo por una cantidad especificada. Se usa generalmente para campos numéricos.
				- `db.collection.updateOne({ _id: 1 }, { $inc: { age: 1 } });`
			- **$currentDate**: Establece el valor de un campo con la fecha y hora actual. Puedes especificar el tipo de datos como `true` para `Date` o `{ $type: "timestamp" }` para un timestamp.
				- `db.collection.updateOne({ _id: 1 }, { $currentDate: { lastModified: true } });`
		- *Operadores de Arreglo:*
			- **$push**: Añade un elemento al final de un arreglo.
				- `db.collection.updateOne({ _id: 1 }, { $push: { hobbies: "reading" } });`
			- **$pop**: Elimina el primer o último elemento de un arreglo (`-1` para el primero, `1` para el último).
				- `db.collection.updateOne({ _id: 1 }, { $pop: { hobbies: 1 } });`
			- **$pull**: Elimina todos los elementos de un arreglo que coincidan con una condición específica.
				- `db.collection.updateOne({ _id: 1 }, { $pull: { hobbies: "reading" } });`
			- **$addToSet**: Añade un elemento a un arreglo solo si no está ya presente (previene duplicados).
				- `db.collection.updateOne({ _id: 1 }, { $addToSet: { hobbies: "swimming" } });`
		- *Operadores de Campo:*
			- **$rename**: Cambia el nombre de un campo.
				- `db.collection.updateOne({ _id: 1 }, { $rename: { "oldName": "newName" } });`
			- **$min**: Solo actualiza el campo si el valor especificado es menor que el valor actual.
				- `db.collection.updateOne({ _id: 1 }, { $min: { age: 18 } });`
			- **$max**: Solo actualiza el campo si el valor especificado es mayor que el valor actual.
				- `db.collection.updateOne({ _id: 1 }, { $max: { age: 30 } });`
	- **options**: Opcionalmente, puedes pasar un conjunto de opciones como `upsert` (para insertar el documento si no existe) o `arrayFilters` (para filtrar elementos en matrices al realizar operaciones de matriz).
		- *Opciones más Comunes:*
			- **upsert**: Si se establece en `true`, y no se encuentra ningún documento que coincida con el filtro, se insertará un nuevo documento con los valores proporcionados en la actualización.
				- `db.collection.updateOne({ name: "Alice" }, { $set: { age: 25 } }, { upsert: true });`
			- **arrayFilters**: Se utiliza para especificar filtros en elementos de matrices. Esto es útil cuando quieres actualizar elementos específicos dentro de un arreglo.
				- `db.collection.updateOne({ _id: 1 },{ $set: {"items.$[element].quantity": 2 } }, { arrayFilters: [ { "element.name": "itemName" } ] });`
			- **writeConcern**: Esta opción permite definir el nivel de confirmación de escritura requerido para la operación. Puede ser útil en aplicaciones críticas donde necesitas garantizar que la escritura se haya replicado en un cierto número de nodos.
				- `db.collection.updateOne({ _id: 1 }, { $set: { status: "active" } }, { writeConcern: { w: "majority", wtimeout: 5000 } });`
			- **collation**: Define reglas de comparación específicas para operaciones de texto. Por ejemplo, se puede usar para realizar actualizaciones sin distinguir entre mayúsculas y minúsculas lo que se pase como filter.
				- `db.collection.updateOne({ name: "alice" }, { $set: { age: 25 } }, { collation: { locale: "en", strength: 2 } });`
			- **hint**: Especifica el índice que se debe usar para realizar la consulta, lo que puede mejorar el rendimiento en ciertas operaciones.
				- `db.collection.updateOne({ name: "Alice" }, { $set: { age: 25 } }, { hint: { name: 1 } });`
``` js
use sample_mflix

db.movies.updateOne( 
	{ title: "Twilight" },
	{
		$set: { plot: "A teenage girl risks everything–including her life–when she falls in love with a vampire."}, 
		$currentDate: { lastUpdated: true }
	}
)
```

- Para actualizar varios documentos, utilice `db.collection.updateMany(filter, update, options)`. 
	- Los operadores y las opciones que hemos discutido anteriormente también aplican al método `updateMany`. La principal diferencia entre `updateOne` y `updateMany` es que `updateMany` actualiza todos los documentos que coinciden con el filtro especificado, mientras que `updateOne` actualiza solo el primer documento que coincide.
``` js
db.collection.updateMany(
  { status: "active" },
  { 
    $set: { status: "inactive" },
    $inc: { loginAttempts: 1 }
  },
  {
    upsert: false,
    collation: { locale: "en", strength: 2 },
    hint: { status: 1 }
  }
);

```

- Para reemplazar un documento, utilice `db.collection.replaceOne(filter, update, options)`.
	- El método `replaceOne` en MongoDB se utiliza para reemplazar un documento entero en una colección con un nuevo documento. A diferencia de `updateOne`, que solo actualiza campos específicos, `replaceOne` reemplaza completamente el documento existente con el nuevo documento proporcionado.
``` js
db.collection.replaceOne(
  { filter },
  { replacement },
  { options }
);
```
``` js
db.movies.replaceOne(
  { title: "Twilight" },
  {
    title: "Twilight",
    director: "Catherine Hardwicke",
    releaseYear: 2008,
    plot: "A teenage girl risks everything–including her life–when she falls in love with a vampire."
  },
  { upsert: true }
);

```

#### Delete:
La Shell de MongoDB proporciona los siguientes métodos para eliminar documentos de una colección:
- Para eliminar un único documentos, utilice: `db.collection.deleteOne(filter, options)`
	- Se utiliza para eliminar un único documento o con el primero de la colección que coincida con el filtro especificado.
	- **filter**: Especifica el criterio de selección para encontrar el documento que deseas eliminar.
	- **options**: Opcionalmente, puedes pasar un conjunto de opciones como `collation`.
``` js
db.movies.deleteOne(
  { title: "Twilight" }
);
```
``` shell
db.collection.deleteOne(
  { title: "twilight" },
  { collation: { locale: "en", strength: 2 } }
);
```

- Para eliminar múltiples documentos, utilice: `db.collection.deleteMany(filter, options)`
	- Se utiliza para eliminar múltiples documentos en una colección que coincidan con el filtro especificado.
	- **filter**: Especifica el criterio de selección para encontrar el documento que deseas eliminar.
	- **options**: Opcionalmente, puedes pasar un conjunto de opciones como `collation`.
``` js
db.movies.deleteMany(
  { genre: "Horror" }
);
```
```shell
db.collection.deleteMany(
  { genre: "horror" },
  { collation: { locale: "en", strength: 2 } }
);
```
