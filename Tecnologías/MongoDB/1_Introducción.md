### **¿Qué es MongoDB?**
MongoDB es un sistema de base de datos `NoSQL` orientado a documentos. En lugar de utilizar tablas y filas como en las bases de datos relacionales, MongoDB almacena datos en documentos de tipo `JSON` (JavaScript Object Notation), llamados **BSON** (Binary JSON), que son más flexibles y fáciles de escalar.

#### Características principales de MongoDB:
1. **Modelo orientado a documentos:**
    - Los datos se almacenan como documentos BSON (similar a JSON).
    - Cada documento puede tener una estructura única, lo que facilita almacenar datos no estructurados o semi-estructurados.
2. **No requiere esquema fijo:**
    - MongoDB es "esquema flexible", lo que significa que los documentos en una colección pueden tener diferentes campos y estructuras.
3. **Alta escalabilidad:**
    - Compatible con **sharding**, una técnica que distribuye datos entre múltiples servidores para manejar grandes volúmenes de datos y cargas de trabajo.
4. **Consultas avanzadas:**
    - Admite consultas basadas en documentos, búsquedas por campos específicos, filtros complejos y agregaciones.
    - También permite búsquedas geoespaciales y texto completo.
5. **Integración nativa con JSON:**
    - MongoDB usa JSON en las interacciones con la base de datos, lo que facilita su integración con aplicaciones modernas.
6. **Alta disponibilidad:**
    - Utiliza **replicación** mediante un conjunto de réplicas (Replica Set), lo que garantiza que siempre haya copias de los datos disponibles.
7. **Rendimiento y velocidad:**
    - Diseñado para manejar grandes volúmenes de datos con alto rendimiento, ideal para aplicaciones de big data y tiempo real.

#### Conceptos clave en MongoDB:
1. **Base de datos:**
    - Contenedor de colecciones, similar a una base de datos en sistemas relacionales.
2. **Colección:**
    - Similar a una tabla en sistemas relacionales, pero no exige un esquema fijo.
3. **Documento:**
    - Unidad básica de datos en MongoDB, análogo a una fila en bases de datos relacionales, pero en formato JSON/BSON. El tamaño máximo de un documento es de `16 MB`.
4. **BSON:**
    - Es una representación binaria de JSON, optimizada para almacenamiento y consultas rápidas.
5. **Consulta:**
    - Las consultas en MongoDB utilizan una sintaxis basada en JSON para buscar y manipular documentos.
6. **Índices:**
    - MongoDB permite crear índices para acelerar las consultas, incluyendo índices compuestos, geoespaciales y de texto.
7. **Agregación:**
    - Funcionalidad poderosa para procesar y transformar datos mediante pipelines, similar a las funciones `GROUP BY` y `HAVING` de SQL.

#### Ventajas y Desventajas de MongoDB:
###### **Ventajas:**
- Flexibilidad al modelar datos.
- Fácil escalado horizontal (sharding).
- Excelente soporte para aplicaciones modernas (cloud-native, IoT, Big Data).
- Compatible con múltiples lenguajes de programación.
Cuando necesitamos trabajar con grandes volúmenes de datos los cuales pueden ser almacenados de forma inconsistentes (campos no completados, nulos, datos redundantes o incluso sin formato o fuera de estándar) al trabajar con bases de datos sql se vuelve un poco más complejo el tratado de los datos; es acá donde las bases de datos NoSQL brillas, ya que su alta flexibilidad favorecen al almacenamiento manipulación y obtención de los mismos. 
###### **Desventajas:**
- No es ideal para aplicaciones que requieran transacciones complejas (aunque admite transacciones ACID desde MongoDB 4.0).
- Requiere más planificación para implementar la escalabilidad y el rendimiento óptimo.

#### Cuándo usar MongoDB?
- Aplicaciones que manejan grandes cantidades de datos no estructurados o semi-estructurados.
- Sistemas que necesitan alta disponibilidad y escalabilidad.
- Aplicaciones en tiempo real, como análisis de datos, catálogos en línea, redes sociales o aplicaciones IoT.