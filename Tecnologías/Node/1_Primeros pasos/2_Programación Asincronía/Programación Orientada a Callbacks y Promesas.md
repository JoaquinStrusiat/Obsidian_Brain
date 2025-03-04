### Introducción a los callbacks
![[Programación Asíncrona#**Callbacks**]]

#### Callbacks en Node
Un caso muy típico de uso de `callbacks` en Node.js es cuando queremos leer archivos mediante el módulo de filesystem (`fs`):
``` js
const fs = require('fs');

function callback(error, data){
	if (err) {
    console.error('Error leyendo el archivo:', err);
  } else {
	  console.log('Contenido del archivo:', data);
  }
}

// Leer un archivo de forma asíncrona
fs.readFile('ruta/al/archivo.txt', 'utf8', callback);
```
En este ejemplo, `fs.readFile` se usa para leer un archivo de forma asíncrona. La función de callback recibe dos argumentos: `err` (para manejar errores) y `data` (el contenido del archivo).

Cuando queremos ejecutar varias funciones asíncronas se ve de la siguiente manera:
``` js
const fs = require('fs');

function callback(error, data){
	if (err) {
    console.error('Error leyendo el archivo:', err);
  } else {
	  console.log('Contenido del archivo:', data);
  }
}

// Leer un archivo de forma asíncrona
fs.readFile('ruta/al/archivo1.txt', 'utf8', callback);
fs.readFile('ruta/al/archivo2.txt', 'utf8', callback);
fs.readFile('ruta/al/archivo3.txt', 'utf8', callback);
```
El problema de esto es que la lectura de los archivos se ejecutan por separado en la línea de ejecución, lo que podría desencadenar en que el orden en el que se ejecuta la lectura sea distinta a la salida, ya que los archivos más pesados podrían tardar más en ser leídos.

Una solución a esto es encadenar los callbacks; a esto lo llamamos `Callbacks Hell`:
``` js
fs.readFile('ruta/al/archivo1.txt', 'utf8', (err, data) => {
	if (err) {
    console.error('Error leyendo el archivo:', err);
  } else {
	console.log('Contenido del archivo:', data);
	fs.readFile('ruta/al/archivo2.txt', 'utf8', (err, data) => {
		if (err) {
		    console.error('Error leyendo el archivo:', err);
		} else {
			console.log('Contenido del archivo:', data);
			fs.readFile('ruta/al/archivo2.txt', 'utf8', callback);
		}
	});
}
});
```
Uno de los problemas principales de usar callbacks encadenados para controlar el flujo de tareas asíncronas es que vuelve al código más complejo y menos legible ya que crea una estructura anidada y piramidal hacia la derecha.

Para esto mismo es que se implementa el uso de las promesas...

### Promesas:

![[Programación Asíncrona#**Promesas**]]


De todas formas esto no resuelve la problemática de que que para controlar el flujo de datos obtenidos a través de promesas, debemos encadenar esta implementación mediante `Promise Hell`:
``` js
const fs = require('fs').promises;

// Función para leer un archivo
function readFile(filePath) {
  return fs.readFile(filePath, 'utf8');
}

// Función para escribir en un archivo
function writeFile(filePath, data) {
  return fs.writeFile(filePath, data);
}

// Función para eliminar un archivo
function deleteFile(filePath) {
  return fs.unlink(filePath);
}

// Ruta de los archivos
const originalFile = 'ruta/al/archivo_original.txt';
const newFile = 'ruta/al/nuevo_archivo.txt';

// Encadenamiento de promesas
readFile(originalFile)
  .then(data => {
    console.log('Contenido leído:', data);
    return writeFile(newFile, data);
  })
  .then(() => {
    console.log('Contenido escrito en el nuevo archivo.');
    return deleteFile(originalFile);
  })
  .then(() => {
    console.log('Archivo original eliminado.');
  })
  .catch(err => {
    console.error('Error:', err);
  });
```

Para evitar recaer en el uso del encadenamiento de los `Hell`, es que se incluye esta *Syntactic Sugar*, a la que llamaremos `async/await`:

### Async/await
![[Programación Asíncrona#**async/await**]]
