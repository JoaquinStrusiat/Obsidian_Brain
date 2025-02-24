### $match:
Filtra los documentos que cumplen con ciertos criterios, reduciendo la cantidad de datos que pasan a la siguiente etapa.

Ejemplo: Filtrar ventas mayores a 100
``` js
db.ventas.aggregate([
  { $match: { total: { $gt: 100 } } }
]);
```

### $group:
Agrupa documentos por un campo específico y aplica operaciones de agregación, como suma, promedio, conteo, etc.

Ejemplo: Calcular el total de ventas por categoría
``` js
db.ventas.aggregate([
  { $group: { _id: "$categoria", totalVentas: { $sum: "$total" } } }
]);
```

### $sort:
Ordena los documentos según un campo especificado, en orden ascendente (`1`) o descendente (`-1`).

Ejemplo: Ordenar ventas por fecha descendente
``` js
db.ventas.aggregate([
  { $sort: { fecha: -1 } }
]);
```

### $project:
Selecciona o transforma campos en los documentos. Puedes incluir, excluir o crear nuevos campos.

Ejemplo: Seleccionar solo el nombre y el precio de los productos
``` js
db.productos.aggregate([
  { $project: { nombre: 1, precio: 1, _id: 0 } }
]);
```

### $lookup:
Realiza una operación de unión (join) entre dos colecciones, similar a un `LEFT JOIN` en SQL.

Ejemplo: Unir la colección `ventas` con `clientes` para obtener información del cliente
``` js
db.ventas.aggregate([
  {
    $lookup: {
      from: "clientes",       // Colección a unir
      localField: "cliente_id",// Campo en la colección actual
      foreignField: "_id",    // Campo en la colección "clientes"
      as: "info_cliente"      // Nombre del nuevo campo con los datos unidos
    }
  }
]);
```

### $unwind:
Descompone un array en documentos individuales, creando un documento por cada elemento del array.

Ejemplo: Descomponer un array de tags en documentos separados
``` js
db.productos.aggregate([
  { $unwind: "$tags" }
]);
```

### $addFields:
Agrega nuevos campos a los documentos sin modificar los campos existentes.

Ejemplo: Agregar un campo que calcule el total con impuestos
``` js
db.ventas.aggregate([
  { $addFields: { totalConImpuestos: { $multiply: ["$total", 1.16] } } }
]);
```

### $limit:
Limita el número de documentos que pasan a la siguiente etapa.

Ejemplo: Obtener las primeras 5 ventas
``` js
db.ventas.aggregate([
  { $limit: 5 }
]);
```

### $skip:
Omite un número específico de documentos antes de pasar a la siguiente etapa.

Ejemplo: Omitir las primeras 10 ventas
``` js
db.ventas.aggregate([
  { $skip: 10 }
]);
```

### $count:
Cuenta el número de documentos que llegan a esta etapa.

Ejemplo: Contar el número de ventas
``` js
db.ventas.aggregate([
  { $count: "totalVentas" }
]);
```

### $facet:
Permite ejecutar múltiples pipelines en paralelo sobre los mismos documentos, generando resultados separados.

Ejemplo: Calcular el total de ventas y el promedio de ventas en una sola consulta
``` js
db.ventas.aggregate([
  {
    $facet: {
      totalVentas: [{ $group: { _id: null, total: { $sum: "$total" } } }],
      promedioVentas: [{ $group: { _id: null, promedio: { $avg: "$total" } } }]
    }
  }
]);
```

### $replaceRoot:
Reemplaza el documento actual con un nuevo documento especificado.

Ejemplo: Reemplazar el documento con el campo `info_cliente` obtenido de un `$lookup`:
``` js
db.ventas.aggregate([
  {
    $lookup: {
      from: "clientes",
      localField: "cliente_id",
      foreignField: "_id",
      as: "info_cliente"
    }
  },
  { $replaceRoot: { newRoot: { $arrayElemAt: ["$info_cliente", 0] } } }
]);
```

### $out:
Escribe los resultados del pipeline en una nueva colección.

Ejemplo: Guardar el resultado de una consulta en una colección llamada `ventas_totales`
``` js
db.ventas.aggregate([
  { $group: { _id: "$categoria", totalVentas: { $sum: "$total" } } },
  { $out: "ventas_totales" }
]);
```

### Ejemplo completo combinando varias etapas:
Supongamos que queremos:
1. Filtrar ventas mayores a 100.
2. Agrupar por categoría y calcular el total de ventas.
3. Ordenar por el total de ventas en orden descendente.
4. Limitar el resultado a las 5 categorías con mayores ventas.
``` js
db.ventas.aggregate([
  { $match: { total: { $gt: 100 } } },     // Filtra ventas > 100
  { $group: { _id: "$categoria", total: { $sum: "$total" } } }, // Agrupa por categoría
  { $sort: { total: -1 } },                // Ordena por total descendente
  { $limit: 5 }                            // Limita a 5 resultados
]);
```

### Conclusión:
El Aggregate Framework de MongoDB es una herramienta extremadamente poderosa para el análisis y transformación de datos. Cada etapa tiene un propósito específico, y al combinarlas, puedes realizar consultas complejas y eficientes directamente en la base de datos. ¡Es ideal para tareas como reportes, análisis de datos y transformaciones avanzadas!