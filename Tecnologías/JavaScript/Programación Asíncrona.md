## Introducción
#asincronía

JavaScript es un lenguaje de **hilo único**, lo que significa que solo puede ejecutar una tarea a la vez. Sin embargo, para evitar bloqueos en operaciones que toman tiempo (como llamadas a APIs o lectura de archivos), utiliza la **programación asíncrona** y un mecanismo llamado **event loop**.

### **Conceptos Clave**
1. **Hilo único:**
    - JavaScript ejecuta las tareas de una en una.
    - Las tareas lentas pueden bloquear el flujo si no se manejan de forma asíncrona.
2. **Event Loop (Ciclo de eventos):**
    - Es el mecanismo que permite que JavaScript administre tareas asíncronas.
    - Se compone de:
        - **Cola de mensajes:** Donde se almacenan tareas asíncronas para ser procesadas.
        - **Ciclo:** Itera constantemente verificando si hay tareas en la cola que se puedan ejecutar.
3. **Delegación de tareas:**
    - Algunas operaciones se envían a la cola de mensajes para no bloquear el hilo principal.
    - Cuando la tarea termina, el event loop reanuda su ejecución.
4. **Herramientas para manejar la asincronía:**
    - **Callbacks:** Funciones que se ejecutan cuando una operación asíncrona finaliza.
    - **Promesas:** Representan un valor que estará disponible ahora o en el futuro.
    - **Funciones asíncronas (`async/await`):** Sintaxis moderna que facilita escribir código asíncrono de manera más legible.

*Ejemplo práctico:*
``` js
console.log("Inicio");

setTimeout(() => {
  console.log("Tarea asíncrona terminada");
}, 2000); // Simula una operación que toma 2 segundos

console.log("Fin");
```
Salida
``` bash
Inicio
Fin
Tarea asíncrona terminada
```
En este ejemplo:
- `setTimeout` delega la tarea a la cola de mensajes.
- El código principal sigue ejecutándose sin esperar los 2 segundos.
- Cuando el tiempo termina, el event loop recupera la tarea y la ejecuta.

### **Ejemplos con Callbacks, Promesas y async/await**

#### **Callbacks**
#callbacks

En JavaScript, un **callback** es una función que se pasa como argumento a otra función y se ejecuta después de que la función principal haya terminado su ejecución. Los callbacks se utilizan para manejar operaciones asíncronas, como la lectura de archivos, consultas a bases de datos, o solicitudes HTTP, de manera que el código no se bloquee mientras espera que estas operaciones se completen.

###### Resumen de Callbacks:
- **Propósito:** Manejar operaciones asíncronas.
- **Funcionamiento:** Pasar una función como argumento a otra función.
- **Beneficios:** Permite continuar la ejecución del código mientras se espera el resultado de una operación asíncrona.
``` js
// Función que simula una operación asíncrona utilizando setTimeout
function fetchData(callback) {
  setTimeout(() => {
    const data = { id: 1, name: 'John Doe' };
    callback(data);
  }, 2000);
}

// Función de callback que maneja los datos obtenidos
function handleData(data) {
  console.log('Datos recibidos:', data);
}

// Llamada a la función asíncrona con la función de callback
fetchData(handleData);

```
En este ejemplo, `fetchData` es una función que simula una operación asíncrona utilizando `setTimeout`. Cuando la operación se completa después de 2 segundos, se llama a la función `handleData`, que se pasó como argumento, con los datos obtenidos.

###### Ventajas de los Callbacks:
- **No Bloqueante:** Permite que el código continúe ejecutándose mientras se espera que una operación asíncrona se complete.
- **Flexible:** Puedes definir diferentes funciones de callback para manejar diferentes resultados o situaciones.

###### Desventajas de los Callbacks:
- **Callback Hell:** El anidamiento excesivo de callbacks puede hacer que el código sea difícil de leer y mantener. Esto se conoce como "Callback Hell" o "Pyramid of Doom".
``` js
firstFunction(args, function() {
  secondFunction(args, function() {
    thirdFunction(args, function() {
      // ...
    });
  });
});

```

#### **Promesas**
#promesas

Las **promesas** son una forma de manejar operaciones asíncronas en JavaScript de manera más limpia y estructurada que los callbacks. Una promesa es un objeto que representa la finalización (o el fracaso) eventual de una operación asíncrona y su valor resultante. 
###### Resumen de Promesas:
- **Propósito:** Manejar operaciones asíncronas de manera más limpia y estructurada.
- **Estados de una Promesa:**
    - `Pending` (pendiente): La operación asíncrona no ha terminado.
    - `Fulfilled` (cumplida): La operación asíncrona se completó con éxito.
    - `Rejected` (rechazada): La operación asíncrona falló.
- **Métodos de resolución:**
	- `.then()`: si la promesa fue exitosa
	- `.catch()`: atrapar el error en caso de una falla.
``` js
function fetchDataPromise() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const success = true; // Cambia a `false` para simular un error
      if (success) {
        resolve("Datos obtenidos");
      } else {
        reject("Error al obtener los datos");
      }
    }, 2000);
  });
}

console.log("Inicio");
fetchDataPromise()
  .then((data) => {
    console.log(data); // "Datos obtenidos"
  })
  .catch((error) => {
    console.error(error); // "Error al obtener los datos"
  });
console.log("Fin");
```
Salida:
``` bash
Inicio
Fin
Datos obtenidos
```

#### **async/await**
#async/await

Cuando programamos en JavaScript, frecuentemente trabajamos con operaciones asíncronas, como solicitudes a servicios web, cálculos y eventos. La dificultad radica en que no sabemos cuándo terminarán estas operaciones, así que necesitamos un mecanismo para saber si se han completado, qué resultado produjeron y si hubo errores.

Inicialmente, utilizábamos callbacks, funciones asignadas que se llamaban cuando la operación asíncrona finalizaba. Luego, surgieron las promesas, que ofrecieron mejoras significativas sobre los callbacks, aunque su sintaxis puede ser confusa y desafiante para los nuevos desarrolladores.

Finalmente, se introdujeron las funciones asíncronas que permite trabajar con promesas de una manera más sencilla y legible. Estas funciones se declaran utilizando la palabra clave `async` antes de la palabra `function`. Dentro de una función asíncrona, puedes usar la palabra clave `await` para pausar la ejecución de la función hasta que una promesa se resuelva.

*Definición:*
La diferencia de principal entre una función y una función asíncrona es que esta siempre devuelve una promesa independientemente de si se está retornando una promesa explícitamente dentro del bloque de la función
``` js
async function suma(a, b){
	return a + b;
}

async function suma(a, b){
	return new Promise(res, rej) => {
		setTimeout(resolve, 500, a + b);
	}
}
```
En estos dos casos las funciones retornan una promesa pero a diferencia de la segunda, la primera no devuelve explícitamente la promesa sino que al ser una función asíncrona, por detrás si que transforma esa respuesta en una promesa que la devuelve resuelta en este caso.

También tenemos la posibilidad de utilizar la palabra reservada `await` que es conocida como una sintaxis dulce o Syntactic Sugar. Ya que muchas veces se interpreta como una pausa en la ejecución del código (esperar a resolver una promesa y luego seguir con la ejecución del código), lo que realmente nos aporta esta sintaxis es la posibilidad de resolver las promesas sin la necesidad de utilizar funciones anidadas ni de concatenar los `.then` y `.catch`, sin embargo esto solo es una abstracción al funcionamiento ya que por detrás javascript sigue funcionando como mencionamos en los casos anteriores.

Algo muy importante a tener en cuenta: la palabra reservada `await` solo se puede ejecutar dentro de una función asíncrona `async`.
``` js
async function fetchData() {
  try {
    let response = await fetch('https://api.example.com/data');
    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}
fetchData();
```

### **Comparación**
1. **Callbacks:** Son útiles pero pueden ser difíciles de leer y mantener cuando se encadenan ("callback hell").
2. **Promesas:** Mejoran la legibilidad y permiten manejar errores más claramente con `.catch()`.
3. **Async/await:** Facilitan aún más la lectura y son ideales para trabajar con promesas, especialmente en código complejo.

