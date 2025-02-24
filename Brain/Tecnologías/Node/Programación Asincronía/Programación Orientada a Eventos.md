### Eventos
#eventos

La programación orientada a eventos (event-driven programming) es un paradigma en el que el flujo del programa está determinado por eventos, como acciones del usuario, mensajes de otros programas o cambios en el estado del sistema. Node.js es particularmente conocido por su arquitectura orientada a eventos, lo que lo hace ideal para aplicaciones que requieren operaciones asíncronas y manejo eficiente de múltiples conexiones simultáneas.

#### Conceptos Clave:
1. **Eventos**: Las acciones o cambios que ocurren en el sistema.
2. **Event Emitter**: Un objeto que emite eventos. Otros objetos pueden escuchar estos eventos y responder a ellos.
3. **Callbacks**: Funciones que se ejecutan en respuesta a eventos.

#### Ejemplo Básico:

**1) Creación de un Event Emitter:**
``` js
const EventEmitter = require('events');
const eventEmitter = new EventEmitter();

// Definimos un evento 'saludo' y su callback
eventEmitter.on('saludo', () => {
  console.log('Hola, ¡este es un saludo!');
});

// Emitimos el evento 'saludo'
eventEmitter.emit('saludo');
```
Descripción:
- Importamos el módulo `events` y creamos un nuevo `EventEmitter`.
- Registramos un oyente para el evento `saludo`.
- Emitimos el evento `saludo`, lo que desencadena la ejecución del callback y muestra el mensaje en la consola.

**2) Evento con Argumentos:** Podemos también pasar argumentos a los eventos.
``` js
eventEmitter.on('despedida', (nombre) => {
  console.log(`Adiós, ${nombre}. ¡Hasta la próxima!`);
});

// Emitimos el evento 'despedida' con un argumento
eventEmitter.emit('despedida', 'Juan');
```
Descripción:
- Registramos un oyente para el evento `despedida` que toma un argumento `nombre`.
- Emitimos el evento `despedida` y pasamos el argumento `Juan`.

#### Ejemplo más Complejo:

amos a extender la clase `EventEmitter` para agregar métodos personalizados que manejen eventos específicos.

Primero, importamos el módulo `events` y creamos nuestra clase que extiende `EventEmitter`.

``` js
const EventEmitter = require('events');

class MiEmisorEventos extends EventEmitter {
  // Método personalizado para emitir un saludo
  saludar(nombre) {
    console.log(`Emitiendo saludo a ${nombre}`);
    this.emit('saludo', nombre);
  }

  // Método personalizado para emitir una despedida
  despedir(nombre) {
    console.log(`Emitiendo despedida a ${nombre}`);
    this.emit('despedida', nombre);
  }
}

const miEmisor = new MiEmisorEventos();

// Registro de los eventos personalizados
miEmisor.on('saludo', (nombre) => {
  console.log(`Hola, ${nombre}. ¡Encantado de verte!`);
});

miEmisor.on('despedida', (nombre) => {
  console.log(`Adiós, ${nombre}. ¡Nos vemos pronto!`);
});

// Utilización de los métodos personalizados
miEmisor.saludar('Ana');
miEmisor.despedir('Ana');
```

###### En este ejemplo:
1. **Extendemos** `EventEmitter`: Creamos una clase llamada `MiEmisorEventos` que extiende `EventEmitter`.
2. **Métodos Personalizados**: Agregamos métodos personalizados `saludar` y `despedir` que emiten eventos correspondientes.
3. **Registro de Eventos**: Registramos oyentes para los eventos `saludo` y `despedida`.
4. **Emisión de Eventos**: Utilizamos los métodos personalizados para emitir eventos.

###### Explicación del Código:
- **Clase Extendida**: La clase `MiEmisorEventos` extiende `EventEmitter` para incluir métodos personalizados.
- **Métodos Personalizados**: `saludar` y `despedir` son métodos que emiten eventos `saludo` y `despedida` respectivamente.
- **Registro de Oyentes**: Se registran oyentes que responden a los eventos y ejecutan los callbacks correspondientes.
- **Emisión de Eventos**: Los métodos personalizados son llamados con el nombre "Ana", lo que desencadena los eventos y ejecuta los callbacks registrados.

Este enfoque te permite encapsular la lógica de emisión de eventos dentro de métodos personalizados, lo que puede ser útil para organizar mejor tu código y mantener la lógica de manejo de eventos en un solo lugar.


#### Ejemplo de Eventos en caso Real:
Supongamos que estamos creando un servidor HTTP básico usando Node.js que responde a eventos de solicitud.
```js
const http = require('http');

const server = http.createServer((req, res) => {
  if (req.url === '/') {
    res.writeHead(200, {'Content-Type': 'text/plain'});
    res.end('Hola, Mundo!\n');
  }
});

server.listen(3000, '127.0.0.1', () => {
  console.log('Servidor escuchando en http://127.0.0.1:3000/');
});
```

En este ejemplo:
- Utilizamos el módulo `http` para crear un servidor.
- Registramos un evento de solicitud que responde con "Hola, Mundo!" cuando se visita la URL raíz.
- El servidor escucha en el puerto 3000.