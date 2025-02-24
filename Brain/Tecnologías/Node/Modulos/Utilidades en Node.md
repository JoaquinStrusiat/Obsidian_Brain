### ¿Qué son los módulos en JavaScript?
#modulos  

En Node.js, los módulos son bloques de código que encapsulan funcionalidad específica y pueden ser importados y utilizados en otros archivos. Esto permite organizar el código de manera más modular y reutilizable, facilitando el mantenimiento y la colaboración en proyectos grandes. En Node.js, cada archivo es un módulo y se pueden importar otros módulos utilizando `require`.

#### Ejemplos de módulos nativos de Node.js

###### **1) http:**
**Descripción**: El módulo `http` permite crear servidores web y manejar solicitudes y respuestas HTTP. Es fundamental para desarrollar aplicaciones web en Node.js.

**Ejemplo:** En este ejemplo, creamos un servidor HTTP que escucha en el puerto 3000. Cuando el servidor recibe una solicitud, responde con un mensaje de "Hola, Mundo!".

``` js
const http = require('http');

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hola, Mundo!\n');
});

server.listen(3000, '127.0.0.1', () => {
  console.log('Servidor funcionando en http://127.0.0.1:3000/');
});
```

###### **2) fs:**
**Descripción**: El módulo `fs` proporciona una API para interactuar con el sistema de archivos, permitiendo leer, escribir, eliminar y manipular archivos y directorios. Para más información [[Módulo File System|click acá]]

**Ejemplo**: En este ejemplo, usamos `fs.readFile` para leer el contenido de un archivo llamado `archivo.txt` y lo mostramos en la consola. Si ocurre un error, se maneja en el bloque `if (err)`. 


``` js
const fs = require('fs');

fs.readFile('archivo.txt', 'utf8', (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});
```

###### **3) path:**
 **Descripción**: El módulo `path` proporciona utilidades para trabajar con rutas de archivos y directorios de manera independiente del sistema operativo. 
 
 **Ejemplo**: En este ejemplo, utilizamos `path.join` para unir varias partes de una ruta y crear una ruta completa a un archivo `index.html` en el directorio `public`. El resultado se muestra en la consola.
 
``` js
const path = require('path');

const directorio = path.join(__dirname, 'public', 'index.html');
console.log(directorio);
```

###### **4) os:**
**Descripción**: El módulo `os` proporciona información sobre el sistema operativo, como la plataforma, arquitectura, memoria libre, etc. 

**Ejemplo**: En este ejemplo, usamos `os.platform` para obtener el sistema operativo, `os.arch` para obtener la arquitectura del CPU y `os.freemem` para obtener la cantidad de memoria libre. La información se muestra en la consola.

``` js
const os = require('os');

console.log('Sistema operativo:', os.platform());
console.log('Arquitectura del CPU:', os.arch());
console.log('Memoria libre:', os.freemem());
```

###### **5) util:**
**Descripción**: El módulo `util` proporciona varias funciones de utilidad que no están disponibles en otros módulos. 

**Ejemplo**: En este ejemplo, usamos `util.format` para formatear una cadena de texto, reemplazando `%s` con `Mundo`. El resultado se muestra en la consola.
``` js
const util = require('util');

const texto = 'Hola, %s!';
const resultado = util.format(texto, 'Mundo');
console.log(resultado);
```

###### **6) crypto:**

**Descripción**: El módulo `crypto` proporciona funcionalidades de cifrado y descifrado, como la creación de hashes y cifrados. 

**Ejemplo**: En este ejemplo, usamos `crypto.createHash` para crear un hash SHA-256 del texto `'texto'` y lo mostramos en la consola.
```js
const crypto = require('crypto');

const hash = crypto.createHash('sha256').update('texto').digest('hex');
console.log('Hash:', hash);
```
