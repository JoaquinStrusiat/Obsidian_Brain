## Funciones
#funciones
Las funciones son una serie de instrucciones encapsuladas que se llaman o ejecutan cuando estas son llamadas o instanciadas en nuestro programa con la finalidad de poder dividir un problema en subproblemas más pequeños. 

``` js
function unaFuncion(){
	/**
		Bloque de código
		# etc
		# etc
	*/
}
```


Estas pueden recibir valores (variables, constantes, primitivos, datos compuestos (arreglos u objetos) e incluso otras funciones) los cuales se llaman `argumentos` o `parámetros`de una función.
``` js
const argumento1 = 3,1415516;
let argumento2 = ["Hola Mundo", 15];
var argumentoN = false;

function otraFuncion(argumento1, argumento2, argumentoN){
	//Bloque de código
}
```
En JavaScript, los tipos de datos que se pasan como argumentos no están definidos implícitamente en su definición, solo es necesario pasar el nombre de la constante, variable o función a la que hace referencia. 
#### **Formas de declarar una función:** 
##### Declaración de función
Cuando definimos una función `declarada` javascript lo pone al principio en el scope del programa, lo cual nos permite llamar a dicha función incluso por encima o antes de su definición en nuestro código para ser ejecutada sin ningún problema.
``` js
const nombre = "Joaquin"
function saludar(unNombre){
	console.log(`Hola ${unNombre}`);
}

saludar(nombre); //Salida: "Hola Joaquin"
```

##### Expresión de función
En funciones expresadas, solamente podemos llamarlas por debajo o posterior a su definición para que javascript  reconozca su implementación; en caso de llamarla en por encima de su definición nuestro programa podría retornar un error del tipo "función undefined".
``` js
const nombre = "Joaquin"
const saludar = function func (unNombre){
	console.log(`Hola ${unNombre}`);
}
saludar(nombre); //Salida: "Hola Joaquin"
```

``` js
// Función anónima
const num1 = 5;
const num2 = 10;

const funcAnonima = function (a, b){
	return a + b;
}
funcAnonima(num1, num2); //Salida: 15
```

#### **El scope o alcance**
En términos generales el `scope` o `alcance` es una colección de variables, constantes, funciones y objetos que están a tu alcance en tu código. En javascript existen dos tipos de ellos el `scope global` y el `scope local`

**Scope Global** : son todas aquellas variables, constantes, funciones y objetos que son accesibles en cualquier parte del código y por lo general son todas aquellas que se definen en la raíz de nuestro código; por fuera de bloques de código como funciones, bucles.
``` js
cosnt saludo = "Hola"
function unaFuncion(){
	console.log(saludo);
}

unaFuncion(); //Salida: Hola
console.log(saludo);//Salida: Hola
```

**Scope Local** : son todas aquellas variables, constantes, funciones y objetos que solo son accesibles dentro de una función o bloque de código en el cual las hemos declarado, como funciones o bucles.

``` js
function unaFuncion(){
	cosnt saludo = "Hola"
	console.log(saludo);
}

unaFuncion(); //Salida: Hola
console.log(saludo);//Salida: saludo is not defined
```

Dentro del scope local, podemos mencionar otros dos alcances internos que ya mencionamos anteriormente, el alcance [[2_Sintaxis#`var `|funcional]] (variables declaradas con `var`) y el alcance de [[2_Sintaxis#`let `|bloque]] (variables declaradas con `let`).

**Alcance funcional con var**
``` js
const nombre = "Joaquin"
function saludar (unNombre){
	if(unNombre){
		var res = `Hola ${unNombre}`
	}
	console.log(res);
}
saludar(nombre); //Salida: "Hola Joaquin"
```
como podemos observar en el siguiente fragmento de código, estamos mostrando la respuesta por consola por fuera de la declaración del `if` ya que la constante declarada con *var* puede ser accedida desde cualquier parte de la función.

**Alcance de bloque con let**
``` js
const nombre = "Joaquin"
function saludar (unNombre){
	if(unNombre){
		let res = `Hola ${unNombre}`
	}
	console.log(res);
}
saludar(nombre); //Salida: res is not defined
```
En este caso, al declarar la respuesta con *let* solo podemos acceder a esa variable dentro del bloque que fue definido; en este caso el bloque `if`

``` js
//correcta implementación
const nombre = "Joaquin"
function saludar (unNombre){
	if(unNombre){
		let res = `Hola ${unNombre}`
		console.log(res);
	}
}
saludar(nombre); //Salida: "Hola Joaquin"
```


#### **Arguments en funciones**
El objeto `arguments` es una colección de todos los argumentos pasados a una función. Puedes utilizar `arguments` para acceder a los parámetros de una función sin referenciar explícitamente sus nombres.

``` js
function sumarTodos() {
    let suma = 0;
    for (let i = 0; i < arguments.length; i++) {
        suma += arguments[i];
    }
    return suma;
}

console.log(sumarTodos(1, 2, 3, 4)); // Salida: 10
```

Aunque `arguments` se comporta como un arreglo, no tiene acceso a los métodos de un arreglo como `forEach`, `map`, etc. Puedes convertir `arguments` en un verdadero arreglo usando `Array.from(arguments)` o utilizando el operador de propagación (`...`).

``` js
//Primer ejemplo ----------------------------------
function sumarTodos() {
    const args = Array.from(arguments); 
    return args.reduce((acc, val) => acc + val, 0);
}
console.log(sumarTodos(1, 2, 3, 4)); // Salida: 10

//Segundo ejemplo ---------------------------------
function sumarTodos() {
    const args = [...arguments]
    return args.reduce((acc, val) => acc + val, 0);
}
console.log(sumarTodos(1, 2, 3, 4)); // Salida: 10

//Tercer ejemplo ----------------------------------
function sumarTodos(...args) {
    return args.reduce((acc, val) => acc + val, 0);
}
console.log(sumarTodos(1, 2, 3, 4)); // Salida: 10
```

#### **Funciones puras**
#funciones_puras
Antes de introducirnos en la explicación de que es una función pura, vamos a comentar un comportamiento muy común que puede tender a errores cuando trabajamos con javascript.
Al pasar parámetros o argumentos tenemos que tener en cuenta la diferencia de pasarlos por `valor` y por `referencia`. 
###### Pasaje por Valor:
- **Definición**: Se pasa una copia del valor del argumento a la función. Cualquier cambio hecho al argumento dentro de la función no afecta el valor original fuera de la función.
    
- **Uso**: Los tipos primitivos en JavaScript (números, cadenas, booleanos, `null`, y `undefined`) se pasan por valor.
``` js
let num = 20
function suma(val){
	val = val + 10;
}

suma(num);
console.log(num) // Salida: 20
```
###### Pasaje por Referencia:
- **Definición**: Se pasa una referencia (una dirección en memoria) del argumento a la función. Cualquier cambio hecho al argumento dentro de la función afecta el valor original fuera de la función.
    
- **Uso**: Los objetos y arreglos en JavaScript se pasan por referencia.
``` js
function cambiarPropiedad(obj) {
    obj.propiedad = "nuevo valor";
}

let objeto = { propiedad: "valor original" };
cambiarPropiedad(objeto);
console.log(objeto.propiedad); // Output: "nuevo valor"

```

Bajo este concepto decimos que una **función es pura** cuando no produce efectos secundarios como lo son las mutaciones (afectar a variables por fuera del alcance de scope de la función).
Para crear funciones puras debemos intentar evitar estos comportamientos mencionados anteriormente mediante algunas técnicas o reglas de escritura. En este caso mencionaremos una de ellas: 
- Una de las técnicas que podemos utilizar para no mutar arreglos u objetos que son pasados por referencia a nuestra función, es crear una copia de estos y de ser necesario retornarlo como un valor nuevo:
``` js
function cambiarPropiedad(obj) {
	let copia = {...obj}; //Usando operador de propagación generamos una copia...
    copia.propiedad = "nuevo valor";
    return copia
}

let objeto = { propiedad: "valor original" };
let nuevoObjeto = cambiarPropiedad(objeto);
console.log(nuevoObjeto.propiedad); // Output: "nuevo valor"
console.log(objeto.propiedad); // Output: "valor original"
```