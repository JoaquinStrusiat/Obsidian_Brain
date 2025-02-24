### Introducción:
Un _Readable Stream_ es un tipo de _stream_ en el que los datos pueden ser leídos de forma secuencial. Es como una tubería por la que los datos fluyen y se pueden consumir en porciones manejables. Los _Readable Streams_ son muy útiles para procesar grandes cantidades de datos sin necesidad de cargar todo en la memoria.

#### Cómo Funcionan
- **Data Events:** Un _Readable Stream_ emite eventos que indican cuándo hay datos disponibles para ser leídos.
- **Consumo de Datos:** Los datos se pueden leer en porciones, conocidas como "chunks", lo que permite un procesamiento eficiente.
- **Modos de Consumo:** Pueden ser consumidos de dos maneras: **modo de lectura explícita** (manual) y **modo de flujo** (automático).

#### Ejemplos Comunes
- **Lectura de Archivos:** Al leer un archivo grande, un _Readable Stream_ permite procesar el archivo en pequeñas porciones sin cargar todo en la memoria.
- **Entradas de Red:** Cuando se reciben datos de una red, un _Readable Stream_ permite procesar esos datos a medida que llegan.

### Métodos de un Readable Streams
En los _Readable Streams_, hay varios métodos y propiedades que te permiten trabajar de manera eficiente con la lectura de datos. Aquí te menciono algunos de los más importantes:

#### Métodos
1. `readable.read([size])`
    - Lee y devuelve datos del _stream_. El parámetro `size` es opcional y especifica la cantidad de datos a leer.
2. `readable.pipe(destination[, options])`
    - Envía automáticamente los datos del _stream_ a otro _stream_ de escritura. Ideal para pasar datos de un _stream_ a otro sin necesidad de manejar manualmente los eventos `data`.
3. `readable.unpipe([destination])`
    - Deja de enviar automáticamente datos al _stream_ de destino especificado.
4. `readable.resume()`
    - Reanuda la emisión de eventos `data`. Útil cuando se ha llamado a `readable.pause()`.
5. `readable.pause()`
    - Pausa la emisión de eventos `data`. Útil para controlar el flujo de datos y evitar el desbordamiento del _buffer_.
6. `readable.destroy([error])`
    - Destruye el _stream_ y emite el evento `close`. Puede pasarse un error opcional para indicar la razón de la destrucción.

#### Propiedades
1. `readable.readableFlowing`
    - Indica si el _stream_ está en modo de flujo (`true`) o no (`false`).
2. `readable.readableHighWaterMark`
    - El tamaño de _buffer_ máximo en bytes que el _stream_ intenta alcanzar antes de detener la lectura. Configurado durante la creación del _stream_.
3. `readable.readableLength`
    - La cantidad de datos almacenados en el _buffer_ y listos para ser leídos.

#### Eventos
1. `data`
    - Emitido cuando hay datos disponibles para leer.
2. `end`
    - Emitido cuando no hay más datos para leer.
3. `error`
    - Emitido cuando ocurre un error durante la lectura.
4. `close`
    - Emitido cuando el _stream_ se cierra.
5. `readable`
    - Emitido cuando hay datos disponibles para ser leídos usando `readable.read()`.

#### Ejemplo
Aquí tienes un ejemplo que usa algunos de estos métodos y propiedades:
``` js
const fs = require('fs');

const readableStream = fs.createReadStream('archivo.txt', { encoding: 'utf8' });

readableStream.on('data', (chunk) => {
    console.log('Datos recibidos:', chunk);
});

readableStream.on('end', () => {
    console.log('Lectura del archivo completada.');
});

readableStream.on('error', (error) => {
    console.error('Error durante la lectura:', error);
});
```