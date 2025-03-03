Antes de meternos de lleno con el funcionamiento de esta gran herramienta debemos hacer una ruta de repaso de conocimientos previos que son muy importantes a tener en cuenta a la hora de  

#### **Conceptos Básicos del Desarrollo Backend**
- **¿Qué es el backend?**
    - Diferencias entre frontend y backend.
    - Rol del backend en una aplicación web.

---
#### **1. Introducción a la Arquitectura REST**
- **Protocolos de comunicación:** [[1_Protocolos de comunicación|Leer más]]
    - HTTP/HTTPS.
    - Métodos HTTP (GET, POST, PUT, DELETE, etc.).
    - Códigos de estado HTTP (200, 404, 500, etc.).
- **Clientes y servidores: [[2_Cliente y Servidor|Leer más]]
    - Cómo interactúan el cliente (navegador) y el servidor.
    - Peticiones (requests) y respuestas (responses).
- **¿Qué es REST?:** [[3_REST|Leer más]]
    - Principios de REST (Stateless, recursos, representaciones, etc.).
    - Diferencias entre REST y otros enfoques (SOAP, GraphQL).
- **Diseño de APIs RESTful:** [[4_Diseño de APIs RESTful y Formatos|Leer más]]
    - Estructura de URLs (endpoints).
    - Uso correcto de métodos HTTP.
    - Buenas prácticas para diseñar APIs REST.
- **Formatos de datos comunes:** [[4_Diseño de APIs RESTful y Formatos|Leer más]]
    - JSON (JavaScript Object Notation).
    - XML (menos común en REST moderno).

---
#### **2. Fundamentos de Node.js**
- **¿Qué es Node.js?**
    - Entorno de ejecución de JavaScript del lado del servidor.
    - Event loop y modelo no bloqueante.
- **Módulos y NPM:**
    - Uso de módulos en Node.js.
    - Gestión de dependencias con NPM (Node Package Manager).
- **Conceptos básicos de JavaScript para backend:**
    - Asincronía (callbacks, promesas, async/await).
    - Manejo de errores.

---
#### **3. Introducción a Express.js**
- **¿Qué es Express.js?
    - Framework minimalista para Node.js.
    - Ventajas de usar Express.
- **Estructura básica de una aplicación en Express:**
    - Creación de un servidor básico.
    - Manejo de rutas (routes).
    - Middlewares: concepto y uso común (ej: análisis de cuerpos de solicitud, manejo de CORS).
- **Manejo de peticiones y respuestas:**
    - Acceso a parámetros de URL, cuerpos de solicitud y cabeceras.
    - Envío de respuestas (JSON, HTML, etc.).

---
#### **4. Bases de Datos y Persistencia de Datos**
- **Introducción a las bases de datos:**
    - Diferencias entre bases de datos relacionales (SQL) y no relacionales (NoSQL).
    - Uso de ORMs (Object-Relational Mapping) como Sequelize o Mongoose.
- **Conexión a bases de datos desde Express:**
    - Configuración de conexión.
    - Operaciones CRUD (Crear, Leer, Actualizar, Eliminar).

---
#### **5. Autenticación y Autorización**
- **Conceptos básicos:**
    - Diferencias entre autenticación y autorización.
    - Uso de tokens (JWT - JSON Web Tokens).
- **Implementación en Express:**
    - Middlewares para autenticación.
    - Manejo de sesiones y cookies.

---
#### **6. Manejo de Errores y Seguridad**
- **Manejo de errores en Express:**
    - Middlewares para manejo de errores.
    - Buenas prácticas para devolver errores al cliente.
- **Seguridad en aplicaciones backend:**
    - Prevención de ataques comunes (SQL injection, XSS, CSRF).
    - Uso de HTTPS y validación de datos.

---
#### **7. Despliegue y Optimización**
- **Despliegue de aplicaciones backend:**
    - Entornos de producción vs desarrollo.
    - Uso de herramientas como PM2 o Docker.
- **Optimización de APIs:**
    - Caching.
    - Compresión de respuestas.
    - Load balancing.

---

#### **8. Pruebas y Documentación**
- **Pruebas en el backend:**
    - Pruebas unitarias y de integración.
    - Uso de herramientas como Mocha, Chai o Jest.
- **Documentación de APIs:**
    - Herramientas como Swagger/OpenAPI.
    - Buenas prácticas para documentar endpoints.

---
#### **9. Proyecto Práctico**
- **Desarrollo de una API RESTful completa:**
    - Diseño de endpoints.
    - Implementación de operaciones CRUD.
    - Integración con base de datos.
    - Autenticación y manejo de errores.
    - Despliegue en un entorno de producción.