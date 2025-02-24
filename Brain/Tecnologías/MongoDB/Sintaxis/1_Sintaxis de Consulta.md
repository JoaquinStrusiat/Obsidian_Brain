## **Consultas en MongoDB**
MongoDB es una base de datos NoSQL que usa una estructura de datos flexible basada en documentos. La sintaxis de consultas y filtros en MongoDB es muy poderosa y permite una variedad de operaciones que se utilizan para recuperar datos de una colección.

---
## **Consultas básicas**
La sintaxis básica es se compone de la siguiente manera:
``` js
db.collection.find(query, projection)
```
### *Query*:
Es un documento que define los criterios de búsqueda. se componen de pares de campos y valores y tienen la siguiente estructura:
``` js
{
   field1: value1,
   field2: value2,
   field3: value3,
   ...   : ...   ,
   fieldN: valueN
}
```

###### Operadores de Búsqueda:
Para poder realizar consultas mucho más poderosas MongoDB incluye una sintaxis de filtros como: 
1. **Operadores de comparación**:
    - `$eq`, `$ne`, `$gt`, `$gte`, `$lt`, `$lte`, `$in`, `$nin`.
    - Ejemplo: `{ precio: { $gt: 100 } }`.
    - Mas: [[Operadores de Búsqueda#Operadores de comparación|Operadores de comparación]]
2. **Operadores lógicos**:
    - `$and`, `$or`, `$not`, `$nor`.
    - Ejemplo: `{ $or: [ { categoria: "Electrónica" }, { precio: { $lt: 50 } } ] }`.
    - Más: [[Operadores de Búsqueda#Operadores Lógicos|Operadores Lógicos]]
3. **Operadores de arrays**:
    - `$all`, `$elemMatch`, `$size`.
    - Ejemplo: `{ tags: { $all: ["oferta", "nuevo"] } }`.
    - Más: [[Operadores de Búsqueda#Operadores de Arrays|Operadores de Arrays]]
4. **Operadores de existencia**:
    - `$exists`.
    - Ejemplo: `{ descripción: { $exists: true } }`.
    - Más: [[Operadores de Búsqueda#Operadores de existencia|Operadores de existencia]]
5. **Expresiones regulares**:
    - `$regex`.
    - Ejemplo: `{ nombre: { $regex: /^smart/i } }`.
    - Más: [[Operadores de Búsqueda#Expresiones regulares|Expresiones regulares]]
6. **Operadores de tipo**:
    - `$type`.
    - Ejemplo: `{ precio: { $type: "number" } }`.
    - Más: [[Operadores de Búsqueda#Operadores por tipo|Operadores de tipos]]
7. **Operadores geográficos** (si trabajas con datos geoespaciales):
    - `$geoWithin`, `$geoIntersects`, `$near`, `$nearSphere`.

### *Projection* 
La proyección define qué campos incluir o excluir en los resultados. Por defecto si se pasa este argumento vacío y no se lo incluye como parámetro de búsqueda devuelve todos los elementos de cada documento, si se desea especificar que elementos se queremos recuperar utilizamos `1` O `true` para incluir un campo y `0` o `false`para excluirlo.

Ejemplo:
``` js
db.users.find({}, { name: 1, email: 1 })
```
Esto devuelve solo los campos `name` y `email` de todos los documentos en la colección `users`.

---
## **Aggregate Framework**
El **Aggregate Framework** en MongoDB es una potente herramienta que permite realizar operaciones avanzadas de procesamiento y transformación de datos directamente en la base de datos. Está diseñado para trabajar con pipelines, donde los datos fluyen a través de una serie de etapas (stages) que aplican operaciones específicas, como filtrado, agrupación, ordenamiento, proyección, y más.

### Características principales:
8. **Pipeline de etapas**: Las operaciones se organizan en etapas secuenciales, donde cada etapa procesa los datos y pasa el resultado a la siguiente.
9. **Flexibilidad**: Permite realizar consultas complejas que serían difíciles o ineficientes con consultas simples.
10. **Optimización**: Ejecuta las operaciones en el servidor, reduciendo la cantidad de datos transferidos entre la base de datos y la aplicación.
11. **Operaciones avanzadas**: Incluye funciones como agrupación (group), unión de colecciones (lookup), cálculo de campos (project), y más.

### Etapas comunes en el Aggregate Framework:
- [[Etapas de Aggregate Framework#$match|$match]]: Filtra los documentos que cumplen con ciertos criterios.
- [[Etapas de Aggregate Framework#$group|$group]]: Agrupa documentos por un campo específico y aplica operaciones de agregación (suma, promedio, etc.).
- [[Etapas de Aggregate Framework#$sort|$sort]]: Ordena los documentos según un campo especificado.
- [[Etapas de Aggregate Framework#$project|$project]]: Selecciona o transforma campos en los documentos.
- [[Etapas de Aggregate Framework#$lookup|$lookup]]: Realiza una operación de unión (join) entre colecciones.
- [[Etapas de Aggregate Framework#$unwind|$unwind]]: Descompone un array en documentos individuales.
- [[Etapas de Aggregate Framework#$addFields|$addFields]]: Agrega nuevos campos a los documentos sin modificar los campos existentes.
- [[Etapas de Aggregate Framework#$limit|$limit]]: Limita el número de documentos en el resultado.
- [[Etapas de Aggregate Framework#$skip|$skip]]: Omite un número específico de documentos.
- [[Etapas de Aggregate Framework|Más ejemplos de Aggregate Framework]]