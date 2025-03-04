## Objetos y JSON
#objetos
En JavaScript podemos definir objetos utilizando `JavaScript Object Notation` o mejor conocido como `JSON`.

#### Definición y manipulación
*Ejemplo de definición:* Para definir un objeto en JavaScript utilizamos llaves `{}` en las cuales dentro de ellas definimos los atributos de nuestro objeto mediante notaciones del tipo clave valor separados por dos puntos. En javascript podemos almacenar cualquier valor que sea objeto de primera clase como string, number, boolean, valores nulos, arreglos, funciones y otros objetos.
``` js
let curso = {
	título: "Curso de js",
	formato: "texto",
	bloque: ["un", "arreglo"],
	autor: {
		nombre: "joaquin",
		edad: 21
	},
	estado: true,
	guardar: function () {
		console.log("Guardando clase")
	} 
}
```

*Ejemplo de obtención de un valor:* para obtener un valor del objeto, podemos acceder a uno de sus atributos mediante la notación de puntos `.` o la de llaves `[]`.
``` js
console.log(curso.titulo); // Salida: Curso de js
console.log(curso[formato]); // Salida: texto
```

*Ejecución de métodos:* los métodos son todas aquellas funciones que se almacenan dentro de un objeto y se los llaman de la siguiente manera
``` js
curso.guardar(); // Salida: Guardando clase
```


*Ejemplo de mutación/modificación:* para mutar o cambiar el valor de uno de los atributos de nuestro objeto podemos utilizar la notación de asignación para reasignar un nuevo valor a nuestro objeto.
``` js
console.log(curso.estado); // Salida: true
curso.estado = false;
console.log(curso.estado); // Salida: false
```

#### Shorthand properties / syntax
A partir de ECMAScript 2015 se implemento una nueva sintaxis para declarar propiedades y funciones llamadas `shorthand properties y shorthand syntax`, el cual nos permite declarar atributos en nuestro objeto pasando solamente el nombre de la variable que previamente definimos; luego de eso javascript se encarga de tomar como nombre de la propiedad al nombre de nuestra variable y como valor al valor que tenía esta variable al momento de ser declarada como atributo del objeto. Es importante aclarar esta última parte porque al implementar esta sintaxis javascript solo guarda la copia de la variable que se pasa como atributo al objeto, por lo que cualquier mutación o modificación que hagamos posterior a su definición no va a afectar al estado del objeto.

``` js
// Forma tradicional
let nombre = "Joaquin";
let persona = {nombre: nombre};
console.log(persona.nombre) // Salida: Joaquin

// Shorthand properties
let nombre = "Joaquin";
let persona = {nombre};
console.log(persona.nombre) // Salida: Joaquin

// Shorthand syntax
let saludar = () {console.log("Hola")};
let persona = {saludar};
console.log(persona.saludar()) // Salida: Hola
```

#### Duplicar o combinar objetos
Para copiar objetos podemos hacerlo de la misma manera que lo hacíamos con los arreglos utilizando el `spread operator`:
*Ejemplo duplicado de arreglo:*
``` js
let user = {
	nombre: "joaquin",
	edad: 21
}

let copia = {...user, lenguaje: "español"}
conole.log(copia) 
/* Salida:
{
	nombre: "joaquin",
	edad: 21,
	lenguaje: "español"
}
*/
```

*Ejemplo combinación de arreglo:*
``` js
const user = {
	nombre: "joaquin",
	edad: 21
};

const tec = {
	technologies: ["javascript", "html", "css"]
};

const adds = { ...user, ...tec};
console.log(adds); /* Salida:
{
	nombre: "joaquin",
	edad: 21
	technologies: ["javascript", "html", "css"]
}
*/
```

#### Destructuring assignment
La destructuración es un método que nos permite obtener varias atributos de un objeto a la vez, guardándolas en una nueva variable mediante la siguiente sintaxis:

*Ejemplo de destructuring:* 
``` js
let user = {nombre: "joaquin", edad: 21, lenguaje: "español"};

//Destructuring
let { nombre, lenguaje} = user;

console.log(nombre); // Salida: joaquin
console.log(lenguaje); // Salida: español
```

*Ejemplo de destructuring usando spread operator:*
También podemos usar el operador de propagación para obtener todos los atributos de un objeto mediante la destructuración. A continuación mostraré como obtener un atributo y el resto del objeto mediante este método:
``` js
let user = {nombre: "joaquin", edad: 21, lenguaje: "español"};

//Destructuring
let { edad, ...resto} = user;

console.log(edad); // Salida: 21
console.log(resto); // Salida: {nombre: "joaquin", lenguaje: "español"}
```

*Ejemplo de asignación y reasignación de atributos usando destructuring:*
Podemos usar la sintaxis de asignación dentro de la destructuración para reasignar un valor al atributo al que se hace referencia, en el caso de no ser encontrado el valor al que se hace referencia se agrega como nuevo atributo del objeto:

``` js
let user = {nombre: "joaquin", edad: 21, lenguaje: "español"};

let { edad = 22, userType = "root"} = user

console.log(user.edad) // Salida: 22

console.log(user) /* Salida: 
{
	nombre: "joaquin", 
	edad: 21, 
	lenguaje: "español", 
	userType = "root"	
}
*/
```
