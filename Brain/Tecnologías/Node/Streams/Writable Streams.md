### Introducción:
Un _Writable Stream_ es un tipo de _stream_ que permite escribir datos de manera secuencial. Imagina un _Writable Stream_ como una tubería a la que puedes enviar datos en pequeñas porciones, y esos datos se escriben en el destino final, como un archivo o una conexión de red.
#### Cómo Funcionan
- **Data Sink:** Los datos se envían al _stream_ y se "escriben" en el destino especificado.
- **Control de Flujo:** Los _Writable Streams_ permiten controlar el flujo de datos, asegurando que no se envíen datos más rápido de lo que pueden ser procesados.

#### Métodos
1. `writable.write(chunk[, encoding][, callback])
    - Escribe datos en el _stream_. `chunk` es la porción de datos a escribir, `encoding` es el formato (opcional), y `callback` es una función que se llama cuando la escritura ha sido completada.
2. `writable.end([chunk][, encoding][, callback])`
    - Finaliza la escritura en el _stream_. Puedes pasar un último `chunk` de datos para escribir, seguido del `encoding` y un `callback` opcionales.
3. `writable.cork()`
    - Suspende temporalmente la escritura en el _stream_. Esto es útil cuando se quieren agrupar varias operaciones de escritura y enviarlas en un solo bloque.
4. `writable.uncork()
    - Reanuda la escritura en el _stream_ después de haber sido suspendida con `writable.cork()`.
5. `writable.setDefaultEncoding(encoding)
    - Establece el valor predeterminado del `encoding` para las operaciones de escritura.
6. `writable.destroy([error])
    - Destruye el _stream_ y emite el evento `close`. Puedes pasar un error opcional para indicar la razón de la destrucción.

#### Propiedades
1. `writable.writableFinished`
    - Indica si todas las operaciones de escritura en el _stream_ han sido completadas.
2. `writable.writableHighWaterMark`
    - El tamaño de _buffer_ máximo en bytes que el _stream_ intenta alcanzar antes de detener la escritura. Configurado durante la creación del _stream_.
3. `writable.writableLength`
    - La cantidad de datos almacenados en el _buffer_ y listos para ser escritos.

#### Eventos
1. `drain`
    - Emitido cuando el _buffer_ del _stream_ está vacío y se pueden escribir más datos.
2. `finish`
    - Emitido cuando se completa la escritura en el _stream_.
3. `error`
    - Emitido cuando ocurre un error durante la escritura.
4. `close`
    - Emitido cuando el _stream_ se cierra.

#### Ejemplo
Aquí tienes un ejemplo que usa algunos de estos métodos y propiedades:
``` js
const fs = require('fs');

const writableStream = fs.createWriteStream('archivo.txt');

writableStream.write('Hola, mundo!\n', 'utf8', () => {
    console.log('Datos escritos.');
});

writableStream.end('¡Adiós, mundo!\n', 'utf8', () => {
    console.log('Escritura completada.');
});

writableStream.on('finish', () => {
    console.log('Todos los datos han sido escritos.');
});

writableStream.on('error', (error) => {
    console.error('Error durante la escritura:', error);
});
```

En este ejemplo:
- `fs.createWriteStream('archivo.txt')`**:** Crea un _Writable Stream_ para el archivo `archivo.txt`.
- **Eventos** `finish` **y** `error`**:** Se manejan los eventos para detectar cuando se completa la escritura y para manejar errores.