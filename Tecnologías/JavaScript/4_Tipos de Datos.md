## **Tipos de datos en JavaScript**
#tipos_de_datos

Los tipos de datos son anotaciones que agregamos a la información de nuestro programa para que el intérprete o compilador usen esta información como por ejemplo la asignación de espacio en memoria en función del tipo de dato que se quiera almacenar.

#### _Primitivos:_ 
- Se acceden directamente al valor

| **String**    | Cadenas de texto (`"Hola, mundo!"`).                   |                                                 |  #string   |
| ------------- | :----------------------------------------------------- | ----------------------------------------------- | :--------: |
| **Number**    | Números, tanto enteros como decimales (`42`, `3.14`).  | [[Number\| Más Info.]]                          |  #number   |
| **Boolean**   | Valores verdadero o falso (`true`, `false`).           | [[Boolean\| Más Info.]]                         |  #boolean  |
| **Undefined** | Variable declarada pero no asignada (`undefined`).     | [[Null, Undefined y NaN#undefined\| Más Info.]] | #undefined |
| **Null**      | Ausencia intencional de valor (`null`).                | [[Null, Undefined y NaN#null\| Más Info.]]      |   #null    |
| **NaN**       | Resultado de una operación matemática inválida (`NaN`) | [[Null, Undefined y NaN#NaN\| Más Info.]]       |    #NaN    |

#### _Compuestos:_ 
- Se accede a la referencia del valor.

| **Object**   | Colección de pares clave-valor: `{ nombre: "Juan", edad: 30 }`                                          | [[Objetos\|Más Info.]]   | `{}` |
| ------------ | ------------------------------------------------------------------------------------------------------- | ------------------------ | ---- |
| **Array**    | Lista ordenada de elementos: `[ 1, 2, 3, 4, 5 ]`                                                        |                          | `[]` |
| **Function** | Bloque de código diseñado para realizar una tarea específica: `function saludar() { … }`                | [[Funciones\|Más Info.]] | `()` |
| **Class**    | Plantilla para crear objetos que encapsulan datos y comportamientos relacionados: `class Persona { … }` | [[Clases\|Más Info.]]    |      |
___

#### **Primitivos y Objetos**
En javascript cada primitivo tiene su equivalente en objeto, que nos permite declarar primitivos de las siguiente manera:
```js
// Cadenas de texto
let primitivoString = "Hola, mundo!"; // Primitivo -> String
let objetoString = new String("Hola, mundo!"); // Objeto del tipo String

// Valores numéricos
let primitivoNumber = 42; // Primitivo -> Number
let objetoNumber = new Number(42); // Objeto del tipo Number

// Valores buleanos
let primitivoBoolean = true; // Primitivo -> Boolean
let objetoBoolean = new Boolean(true); // Objeto del tipo Boolean
```

##### Resumen:
- **Primitivos**:
	- Almacenamiento directo.
	- Inmutables.
	- No tienen métodos ni propiedades (excepto mediante autoboxing).

- **Objetos**:
    - Almacenados por referencia.
    - Mutables.
    - Tienen métodos y propiedades.
	    - `.constructor`: Devuelve la referencia a la función que creó la instancia del objeto.
		- `.hasOwnProperty(property)`: Indica si el objeto tiene la propiedad especificada como una propiedad directa.
		- `.isPrototypeOf(object)`: Indica si el objeto es el prototipo de otro objeto.
		- `.propertyIsEnumerable(property)`: Indica si la propiedad especificada es enumerable.
		- `.toString()`: Devuelve una cadena que representa el objeto.
		- `.valueOf()`: Devuelve el valor primitivo del objeto.
		- `.toLocaleString()`: Devuelve una cadena que representa el objeto, sensible a la localización.

##### Ejemplos Comparativos: Primitivo vs Objeto
``` js
let primitivoString = "Hola";
let objetoString = new String("Hola");

console.log(typeof primitivoString); // "string"
console.log(typeof objetoString); // "object"

console.log(primitivoString === "Hola"); // true
console.log(objetoString === "Hola"); // false
console.log(objetoString == "Hola"); // true (por comparación de valor)


/* Ejemplos de métodos de objetos */
let numStr = "220"; // String
let num = new Number(numStr);

console.log(typeof num); // "object"
console.log(num) // [Number: 220]

// como vemos <num> es un objeto
console.log(num.valueOf()); // 220
console.log(num.toString()); // "220"
```