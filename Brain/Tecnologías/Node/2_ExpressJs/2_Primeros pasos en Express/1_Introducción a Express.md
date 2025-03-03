## **¿Qué es Express.js?**
**Express.js** es un framework web minimalista y flexible para **Node.js** que facilita la creación de aplicaciones web y APIs RESTful. En lugar de trabajar directamente con los módulos básicos de HTTP de Node.js, Express proporciona una capa de abstracción que simplifica la gestión de peticiones, respuestas, middleware y enrutamiento.

### **Ventajas de usar Express.js**
✔ **Minimalista y ligero**: No impone una estructura rígida, lo que permite flexibilidad.  
✔ **Fácil de aprender y usar**: Su sintaxis es sencilla y cercana a las funciones nativas de Node.js.  
✔ **Soporte para middlewares**: Facilita la manipulación de solicitudes y respuestas.  
✔ **Gran comunidad y ecosistema**: Hay muchas librerías y módulos compatibles.  
✔ **Escalabilidad**: Se puede usar tanto para pequeñas aplicaciones como para grandes arquitecturas de microservicios.


## **Estructura básica de una aplicación en Express**
Antes de empezar, es necesario instalar Express en un proyecto de Node.js. Para hacerlo, se ejecuta el siguiente comando en la terminal:
``` sh
npm init -y  # Crea un package.json
npm install express
```
Luego, se crea un archivo `index.js` con la configuración básica de un servidor Express.

### **Creación de un servidor básico con Express**
Un servidor en Express.js puede crearse con pocas líneas de código:
``` js
const express = require('express');  // Importar Express
const app = express();  // Crear una instancia de la aplicación

const PORT = 3000;  

// Ruta principal
app.get('/', (req, res) => {
    res.send('¡Hola, Express!');
});

// Iniciar el servidor
app.listen(PORT, () => {
    console.log(`Servidor corriendo en http://localhost:${PORT}`);
});
```
**Explicación:**
- Se importa Express y se crea una instancia `app`.
- Se define una ruta (`/`) que responde con un mensaje de texto.
- Se inicia el servidor en el puerto `3000` y se muestra un mensaje en la consola.


Ejecuta el script con:
``` sh
node index.js
```
Visita `http://localhost:3000` en el navegador y verás el mensaje **"¡Hola, Express!"**.

