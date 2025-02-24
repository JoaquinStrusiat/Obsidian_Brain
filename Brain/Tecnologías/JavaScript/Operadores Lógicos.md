## Operadores Lógicos
#operadores #lógicos
Los operadores lógicos se utilizan para combinar múltiples expresiones booleanas y devuelven un valor booleano.

### Tipos de operadores y sus ejemplos:
##### **AND** 
- `&&` : Devuelve `true` si ambas expresiones son `true`.
``` js
console.log(true && true); // true
console.log(true && false); // false
```
 
##### **OR** 
- `||` : Devuelve `true` si al menos una de las expresiones es `true`.
``` js
console.log(true || false); // true
console.log(false || false); // false
```

##### **NOT** 
- `!` : Invierte el valor de la expresión. Si la expresión es `true`, devuelve `false` y viceversa.
``` js
console.log(!true); // false
console.log(!false); // true
```

##### **Nullish coalescing** 
- `??` :  El operador nullish coalescing (fusión de nulos u unión nulosa)  evalúa el valor booleano del lado izquierdo de los signos de interrogación; devuelve el operando de la izquierda si no es `null` ni `undefined`; de lo contrario, devuelve el operando de la derecha.

**Ejemplo N°1:**
``` js
let nombre = null;
let nombrePredeterminado = "Usuario";

let saludo = nombre ?? nombrePredeterminado;
console.log(saludo); // "Usuario"
```
En este ejemplo, como *nombre* es *null*, el operador `??` devuelve *nombrePredeterminado*.

**Ejemplo N°2:**
``` js
let cantidad = 0;
let cantidadPredeterminada = 10;

let resultado = cantidad ?? cantidadPredeterminada;
console.log(resultado); // 0
```
En este caso, aunque *cantidad* es 0 (un valor "falso"), el operador `??` lo acepta porque no es *null* ni *undefined*.