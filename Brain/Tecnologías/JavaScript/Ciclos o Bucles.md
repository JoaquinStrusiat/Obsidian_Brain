## Ciclos o Bucles en JavaScript
#ciclos #bucles
Los ciclos se utilizan para ejecutar repetidamente un bloque de código mientras se cumple una condición específica. 

Los ciclos más comunes en JavaScript son 
1) [[Ciclos o Bucles#Caso 1 `for`| for]] : Usado para iterar un número específico de veces.
	1)  [[Ciclos o Bucles#Caso 1.1 `for...of`| for...of]] : Se utiliza para iterar sobre valores de objetos iterables como arreglos, cadenas, mapas, conjuntos, etc.
	2) [[Ciclos o Bucles#Caso 1.2 `for...in`|for...in]] : Se utiliza para iterar sobre las propiedades enumerables de un objeto.
2)  [[Ciclos o Bucles#Caso 2 `while`|while]] : Útil cuando no sabes cuántas veces necesitas iterar, pero dependes de una condición.
3)  [[Ciclos o Bucles#Caso 2 `do..while`|do...while]] : Igual que `while`, pero garantiza al menos una ejecución del bloque de código.
4) [[Ciclos o Bucles#Caso 4 `Métodos funcionales en arreglos`|Métodos funcionales en arreglos]] : Aunque no son estrictamente bucles, estos métodos proporcionan una forma declarativa de iterar.
	1) `forEach` : Ejecuta una función para cada elemento de un arreglo.
	2) `map` : Crea un nuevo arreglo aplicando una función a cada elemento.
	3) `filter`: Filtra elementos según una condición.
	4) `reduce`: Reduce los elementos a un único valor.

#### Ejemplos:
##### Caso 1: `for`:
#bucle_for
Usado para iterar un número específico de veces.
```js
for (let i = 0; i < 10; i++) {
    console.log(`Iteración número ${i}`);
}
```

##### Caso 1.1: `for...of`:
#bucle_for_of
Se utiliza para iterar sobre valores de objetos iterables como arreglos, cadenas, mapas, conjuntos, etc.
```js
const array = ['JavaScript', 'Python', 'Java'];
for (const lenguaje of array) {
    console.log(lenguaje);
}
/** Salida:
JavaScript
Python
Java
*/
```

##### Caso 1.2: `for...in`:
#bucle_for_in
Se utiliza para iterar sobre las propiedades enumerables de un objeto.
```js
const objeto = { nombre: 'Juan', edad: 25, ciudad: 'Madrid' };
for (const clave in objeto) {
    console.log(`${clave}: ${objeto[clave]}`);
}
```

##### Caso 2: `while`:
#bucle_while
Útil cuando no sabes cuántas veces necesitas iterar, pero dependes de una condición.
```js
let contador = 0;
while (contador < 5) {
    console.log(`Contador: ${contador}`);
    contador++;
}
```

##### Caso 3: `do..while`:
#bucle_do_while
Igual que `while`, pero garantiza al menos una ejecución del bloque de código.
```js
let contador = 0;
do {
    console.log(`Contador: ${contador}`);
    contador++;
} while (contador < 5);
```

##### Caso 4: `Métodos funcionales en arreglos`
Aunque no son estrictamente bucles, estos métodos proporcionan una forma declarativa de iterar.

#forHeach
- **forEach**: Ejecuta una función para cada elemento de un arreglo.
``` js
const numeros = [1, 2, 3, 4, 5]; 
numeros.forEach(numero => console.log(numero)); 
/** Salida:
1
2
3
4
5
*/
```

#map
- **map**: devuelve un nuevo arreglo aplicando una función a cada elemento.
``` js
const numeros = [1, 2, 3]; 
const cuadrados = numeros.map(numero => numero ** 2); 
console.log(cuadrados);
/** Salida:
1
4
9
*/
```

#filter
- **`filter`**: Filtra elementos según una condición y lo devuelve en un nuevo arreglo.
``` js
const numeros = [1, 2, 3, 4, 5]; 
const pares = numeros.filter(numero => numero % 2 === 0); 
console.log(pares);
/** Salida:
2
4
*/
```

#reduce
- **`reduce`**: Reduce los elementos a un único valor, este método recibe una función con dos parámetros inicialmente, en primer lugar un acumulador(valor que se retorna por cada iteración) y en segundo lugar el arreglo que se quiere reducir
``` js
const numeros = [1, 2, 3, 4]; 
const suma = numeros.reduce((acumulador, numero) => acumulador + numero, 0);
console.log(suma);
// Salida: 10
```

#### Palabras reservadas:
Dentro de los ciclos podemos encontrar el uso de dos palabra reservadas; la palabra `break` y `continue`.

##### **break**: 
Lo que hace el uso de esta palabra reservada es terminar con el bucle de iteración en cualquiera de los ciclos anteriormente mencionados.
``` js
for (let i = 0; i < 5; i++) {
    if (i = 3){
		break;
    }  
    console.log(`Iteración número ${i}`);
}
/** Salida: 
Iteración número 0
Iteración número 1
Iteración número 2
*/
```

##### **continue**: 
Al usar esta palabra reservada lo que hacemos es saltearnos esa iteración en el momento que es leída y por ende también nos salteamos la ejecución del bloque de código que podamos tener por debajo de esta misma
``` js
for (let i = 0; i < 5; i++) {
    if (i = 3){
		continue;
    }  
    console.log(`Iteración número ${i}`);
}
/** Salida: 
Iteración número 0
Iteración número 1
Iteración número 3
Iteración número 4
*/
```