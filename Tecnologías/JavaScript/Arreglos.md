## Arreglos / Arrays
#arreglos #array
- **Definición**: Un arreglo es una estructura de datos que almacena una colección de elementos, como números, cadenas u objetos.
- **Índices**: Cada elemento en un arreglo tiene un índice numérico, comenzando en 0 para el primer elemento.

#### Ejemplos básicos:
**Definición**: definición de arreglos
``` js
// Definición de un arreglo
let frutas = ["manzana", "banana", "cereza"];
let numeros = [1,2,3,4,5,6,7,8,9,10];
let booleans = [true, false, true];
```

**Acceso a elementos**: Para acceder a un elemento de nuestro arreglo, lo hacemos mediante el índice (posición en la que se encuentra el elemento que deseamos recuperar), hay que tener en cuenta que los índices en los arreglos no comienzan por la posición número 1 como contamos tradicionalmente, sino que el índice del primer elemento de nuestro arreglo es el 0 hasta el n elemento: 
``` js
// Acceder a un elemento del arreglo
console.log(frutas[0]); // Imprime: manzana
console.log(numeros[1]); // Imprime: 2
console.log(booleans[3]); // Imprime: true
```

**Modificación de Elementos**: Puedes cambiar el valor de un elemento mediante la reasignación del valor al que se accede mediante el índice al que se hace referencia:
``` js
console.log(frutas); // Imprime: ["manzana", "banana", "cereza"]
// Modificar un elemento del arreglo
frutas[1] = "naranja";
console.log(frutas); // Imprime: ["manzana", "naranja", "cereza"]
```

**Agregar Elementos**: Usa `push` para añadir un nuevo elemento al final
``` js
// Agregar un nuevo elemento al final del arreglo
frutas.push("pera");
console.log(frutas); // Imprime: ["manzana", "naranja", "cereza", "pera"]
```

#### Métodos para manipular arreglos:
#metodos #arreglos #array 

`length()`: La propiedad **`length`** de un objeto que es una instancia de tipo Array establece o devuelve la cantidad de elementos en esa matriz
``` js
let frutas = ["manzana", "banana", "cereza"];
const val = frutas.length(); 
console.log(val); // Imprime: 3
```

`pop()`: Elimina el último elemento del arreglo y lo devuelve.
``` js
let frutas = ["manzana", "banana", "cereza"];
const val = frutas.pop(); // ["manzana", "banana"]
console.log(val); // Imprime: "cereza"
```

`push()`: Agrega uno o más elementos al final del arreglo.
``` js
let frutas = ["manzana", "banana"];
frutas.push("naranja"); // ["manzana", "banana", "naranja"]
```

`shift()`: Elimina el primer elemento del arreglo.
``` js
let frutas = ["manzana", "banana", "cereza"];
const val = frutas.shift(); // ["banana", "cereza"]
console.log(val); // Imprime: "manzana"
```

`unshift()`: Agrega uno o más elementos al inicio del arreglo.
``` js
let frutas = ["manzana", "banana", "cereza"];
frutas.unshift("fresa"); // ["fresa", "manzana", "banana", "cereza"]
```

`slice()`: Devuelve una copia de una porción del arreglo.
``` js
let frutas = ["manzana", "banana", "cereza", "naranja"];
let nuevasFrutas = frutas.slice(1, 2); // ["banana", "cereza"]
```

`indexOf()`:  busca un valor dentro del arreglo y devuelve la posición en la que fue encontrado, en caso de no ser encontrado devuelve *-1*
``` js
let frutas = ["manzana", "banana", "cereza", "naranja"];
console.log(frutas.indexOf("banana")); //1
console.log(frutas.includes("fresa")); //-1 
```

`includes()`: determina si una matriz incluye un determinado elemento, devuelve *true* o *false* según corresponda.
``` js
let frutas = ["manzana", "banana", "cereza", "naranja"];
console.log(frutas.includes("manzana")); //true
console.log(frutas.includes("fresa")); //false
```

`find()`: devuelve el *valor* del  *primer elemento* del array que cumple la función de prueba proporcionada.
``` js
const array1 = [5, 12, 8, 130, 44];

const found = array1.find((element) => element > 10);

console.log(found); // Expected output: 12
```

`join()`: une todos los elementos de una matriz (o un objeto similar a una matriz) en una cadena y devuelve esta cadena.
``` js
const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join()); // Expected output: "Fire,Air,Water"

console.log(elements.join('')); // Expected output: "FireAirWater"

console.log(elements.join('-')); // Expected output: "Fire-Air-Water"
```

`reverse()`: invierte el orden de los elementos de un array. El primer elemento pasa a ser el último y el último pasa a ser el primero.
``` js
const elements = ['Fire', 'Air', 'Water'];
const reverse = elements.reverse():
console.log(reverse); // ['Water', 'Air', 'Fire']
```

#### Métodos para recorrer arreglos:
![[Ciclos o Bucles#Caso 1.1 `for...of`]]
![[Ciclos o Bucles#Caso 4 `Métodos funcionales en arreglos`]]

#### Spread y rest syntax
En javascript, cualquier objeto que puede ser separados en elementos se denominan `iterables`; por ejemplo, una cadena es un iterable en el que cada elemento (letra o carácter) es un elemento que componen la cadena; un arreglo es un iterable cuyos elementos componen el arreglo y de igual manera ocurre con los elementos que componen a un objeto.
La sintaxis de expansión (Spread syntax) nos permite obtener estos elementos y enviarlos a una expresión individualmente.
**Ejemplo:**
``` js
const arreglo = [1,2,3];
console.log(arreglo); //[1,2,3]

// Spread operator (...)
console.log(...arreglo); 
/** Salida: 
1
2
3
*/

// Esto es igual que hacer lo siguiente:
console.log(1,2,3); 
/** Salida: 
1
2
3
*/
```

Algo similar ocurre con *rest params* 
