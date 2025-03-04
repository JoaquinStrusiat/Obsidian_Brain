## Operadores de comparación:
Algunos operadores comunes en las consultas de MongoDB son:
`$eq | ==`: Igual a.
``` js
db.users.find({ age: { $eq: 30 } })
```
Esto busca todos los documentos donde la edad (`age`) es exactamente 30.

`$ne | !==`: No igual a.
``` js
db.users.find({ status: { $ne: "active" } })
```
Esto busca todos los documentos donde el estado (`status`) no es "active".

`$gt | >`: Mayor que.
``` js
db.users.find({ age: { $gt: 25 } })
```
Esto busca todos los documentos donde la edad (`age`) es mayor que 25.

`$lt | <`: Menor que.
``` js
db.users.find({ age: { $lt: 18 } })
```
Esto busca todos los documentos donde la edad (`age`) es menor que 18.

`$gte | >=`: Mayor o igual que.
``` js
db.users.find({ age: { $gte: 21 } })
```
Esto busca todos los documentos donde la edad (`age`) es mayor o igual que 21.

`$lte| <=`: Menor o igual que.
``` js
db.users.find({ age: { $lte: 30 } })
```
Esto busca todos los documentos donde la edad (`age`) es menor o igual que 30.

`$in`: Dentro de un conjunto.
``` js
db.users.find({ age: { $in: [20, 25, 30] } })
```
Esto busca todos los documentos donde la edad (`age`) es 20, 25 o 30.

`$nin`: No dentro de un conjunto.
``` js
db.users.find({ age: { $nin: [20, 25, 30] } })
```
Esto busca todos los documentos donde la edad (`age`) no es 20, 25 o 30.

`$exists`: si el atributo existe
``` js
// Caso A
db.users.find({ email: { $exists: true } })

// Caso B
db.users.find({ email: { $exists: false } })
```
En el **Caso A** devuelve todos aquellos usuarios que tienen el atributo  *email*.
En el **Caso B** devuelve todos aquellos usuarios que no tienen el atributo  *email*.

---
## Operadores Lógicos:
Los filtros son básicamente las condiciones de la consulta. Puedes combinar múltiples filtros usando operadores lógicos como `$and`, `$or`, `$not` y `$nor`.

 `$and | &&`: Conjunción, en la mayoría de los casos no es necesario utilizarlo ya que con la notación de clave valor en secuencia es suficiente.
 - Esto busca todos los documentos donde la edad (`age`) es mayor que 25 y el estado (`status`) es "active".
``` js
db.users.find({
  $and: [
    { age: { $gt: 25 } },
    { status: "active" }
  ]
})
```

`$or | ||`: Disyunción.
- Esto busca todos los documentos donde la edad (`age`) es menor que 18 o el estado (`status`) es "inactive".
``` js
db.users.find({
  $or: [
    { age: { $lt: 18 } },
    { status: "inactive" }
  ]
})
```

`$not | !` : Negación
- Esto busca todos los documentos donde la edad (`age`) no es mayor que 30.
``` js
db.users.find({ age: { $not: { $gt: 30 } } })
```

`$nor | !== && !==`: Conjunción de negaciones
- Esto busca todos los documentos donde la edad (`age`) no es menor que 18 ni el estado (`status`) es "active".
``` js
db.users.find({
  $nor: [
    { age: { $lt: 18 } },
    { status: "active" }
  ]
})
```

---
## Operadores de Arrays:
Los **operadores de arrays** son herramientas poderosas que te permiten realizar consultas sobre campos que contienen arreglos. Estos operadores son especialmente útiles cuando trabajas con documentos que tienen estructuras de datos complejas. A continuación, te explico los operadores más comunes con ejemplos y explicaciones.

`$elemMatch`: Este operador se utiliza para encontrar documentos donde al menos un elemento de un array cumple con **todas** las condiciones especificadas.
``` js
db.productos.find({
    detalles: {
        $elemMatch: { tamaño: "M", color: "rojo" }
    }
});
```
- **Explicación**: Busca documentos en la colección `productos` donde el array `detalles` contenga al menos un elemento que tenga `tamaño: "M"` **y** `color: "rojo"`.
- **Nota**: Sin `$elemMatch`, MongoDB aplicaría las condiciones por separado a diferentes elementos del array.

`$size`: Este operador se utiliza para encontrar documentos donde un array tiene un tamaño específico.
``` js
db.usuarios.find({
    intereses: { $size: 3 }
});
```
- **Explicación**: Busca documentos en la colección `usuarios` donde el array `intereses` tenga exactamente 3 elementos.

`$all`: Este operador se utiliza para encontrar documentos donde un array contiene **todos** los elementos especificados, sin importar el orden.
``` js
db.usuarios.find({
    habilidades: { $all: ["JavaScript", "Node.js"] }
});
```
- **Explicación**: Busca documentos en la colección `usuarios` donde el array `habilidades` contenga tanto `"JavaScript"` como `"Node.js"`.

`$in`: Este operador se utiliza para encontrar documentos donde un array contiene **al menos uno** de los elementos especificados.
``` js
db.usuarios.find({
    intereses: { $in: ["deportes", "música"] }
});
```
- **Explicación**: Busca documentos en la colección `usuarios` donde el array `intereses` contenga al menos uno de los valores `"deportes"` o `"música"`.

`$nin`:Este operador es el opuesto de `$in`. Se utiliza para encontrar documentos donde un array **no contiene ninguno** de los elementos especificados.
``` js
db.usuarios.find({
    intereses: { $nin: ["deportes", "música"] }
});
```
- **Explicación**: Busca documentos en la colección `usuarios` donde el array `intereses` no contenga ni `"deportes"` ni `"música"`.

`$push`:  (en actualizaciones) : Este operador se utiliza para agregar un elemento a un array en un documento.
``` js
db.usuarios.updateOne(
    { _id: 1 },
    { $push: { intereses: "viajes" } }
);
```
- **Explicación**: Agrega `"viajes"` al array `intereses` del usuario con `_id: 1`.

`$pull`: (en actualización) : Este operador se utiliza para eliminar un elemento de un array en un documento.
``` js
db.usuarios.updateOne(
    { _id: 1 },
    { $pull: { intereses: "deportes" } }
);
```
- **Explicación**: Elimina `"deportes"` del array `intereses` del usuario con `_id: 1`.

`$adToSet`: (en actualización) : Este operador agrega un elemento a un array solo si no existe ya en el array.
``` js
db.usuarios.updateOne(
    { _id: 1 },
    { $addToSet: { intereses: "viajes" } }
);
```
- **Explicación**: Agrega `"viajes"` al array `intereses` del usuario con `_id: 1` solo si no está ya presente.

`$pop:` (en actualización) : Este operador elimina el primer o último elemento de un array.
``` js
db.usuarios.updateOne(
    { _id: 1 },
    { $pop: { intereses: 1 } } // 1 para el último elemento, -1 para el primero
);
```
- **Explicación**: Elimina el último elemento del array `intereses` del usuario con `_id: 1`.

---
## Operadores de existencia:
De esta forma podemos filtrar por documentos que tienen o no algún atributo especificado en dicho filtro mediante la palabra `$exists`, mediante el valor de `true` expresamos que el atributo debe existir para satisfacer con la consulta y con el valor de `false` expresamos que el atributo no debe existir parta cumplir con la consulta.

Un ejemplo preguntando en la coleción de usuarios estos tienen una propiedad email:
``` js
db.users.find(
	{
		email: {
			$exists: true
		}
	}
)
```
En este caso la consulta devolverá todos aquellos documentos que tengan el atributo de `email`.

---
## Operadores por tipo:
De esta forma podemos podemos filtrar los documentos pasando como condición que un atributo debe ser del tipo de dato especificado en la consulta. Esto lo hacemos mediante la palabra reservada `$type`, agregan como valor el tipo de dato que se busca como coincidencia: 

| **Tipo**           | **Número** | **Alías**   |
| ------------------ | ---------- | ----------- |
| Double             | 1          | 'double'    |
| String             | 2          | 'string'    |
| Object             | 3          | 'Object'    |
| Array              | 4          | 'array'     |
| ObjectId           | 7          | 'objectId'  |
| Boolean            | 8          | 'boolean'   |
| Date               | 9          | 'date'      |
| Null               | 10         | 'null'      |
| Regular Expression | 11         | 'regex'     |
| Timestamp          | 17         | 'timestamp' |
Ejemplo:
``` js
db.users.find(
	{
		updateTime: {
			$type: "date"
		}
	}
)
```
En este ejemplo la consulta devolverá a todos los documento que tengan un atributo llamado `updateTime` y su valor sea de tipo `date`

---
## Expresiones regulares:
Una de las mayores ventajas que tiene MongoDB es que nos permite trabajar con expresiones regulares directamente sobre los atributos que deseamos filtrar, un ejemplo es el siguiente:
``` js
db.users.find({name: /^J/})
```
En este caso filtra a todos los usuarios cuyos nombres comiencen por la letra A mayúscula.
De esta misma manera podríamos definir diferentes expresiones regulares para filtrar cualquier campo que sea del tipo `String`.

---
## Cursor:
En MongoDB, un **cursor** es un puntero o referencia a un conjunto de resultados de una consulta
Cuando realizas una consulta en una colección de MongoDB con el método `find()`, la base de datos no devuelve todos los documentos de una sola vez, sino que devuelve un cursor que te permite iterar sobre los resultados.
#### Métodos comunes de un cursor:
- **`.next()`**: Devuelve el siguiente documento en el cursor.
- **`.hasNext()`**: Verifica si hay más documentos disponibles en el cursor.
- **`.limit(n)`**: Limita el número de documentos devueltos por el cursor.
- **`.skip(n)`**: Omite los primeros `n` documentos.
- **`.sort({ campo: 1 })`**: Ordena los documentos según el campo especificado (1 para ascendente, -1 para descendente).
- **`.forEach(función)`**: Ejecuta una función para cada documento en el cursor.
- **.count()** : Devuelve el número de documentos que coinciden con la búsqueda

Ejemplo de uso: ee esta manera estamos diciendo a mongo que nos devuelva los primeros 50 usuarios de la colección.
``` js
db.users.find({}).limit(50)
```

También se pueden utilizar combinaciones de ellos: en este caso nos devuelve solo 10 documentos salteando los 40 primeros y deteniéndose en el número documento que se encuentra en la posición 50
``` js
db.users.find({}).skip(40).limit(50)
```