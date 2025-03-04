## **Variables y Constantes**
En JavaScript las `variables` son nombres que apuntan a un lugar de la memoria virtual (memoria que almacena información en tiempo de ejecución y la borra una vez finalizada la misma). Hablamos de punteros porque eventualmente estas pueden apuntar a un espacio de memoria nuevo/diferente y cambiar el valor al que anteriormente hacían referencia.

Por otra parte, las `constantes` son también son un tipo de puntero, generalmente llamadas _etiquetas_ los cuales también apuntan a un espacio de la memoria virtual,  con la diferencia que a estas no se les puede reasignar un nuevo valor (referencia en memoria virtual).
___
#### ***Variables:***
#variables

En JavaScript, `var` y `let` son utilizados para declarar variables, pero tienen diferencias clave en términos de alcance y comportamiento:

###### `var:`
1. **Alcance de Función**: Las variables declaradas con `var` tienen alcance de función. Esto significa que si declaras una variable con `var` dentro de una función, estará disponible en toda la función.
    
2. **Hoisting**: Las variables declaradas con `var` son "hoisted" (elevadas) al principio de su contexto de ejecución. Esto significa que puedes usar la variable antes de su declaración, aunque estará indefinida.
    
3. **Problemas de Reasignación**: `var` permite la redeclaración de la misma variable dentro del mismo ámbito, lo que puede llevar a errores inesperados.

```js
function ejemploVar() {
    console.log(x); // undefined
    var x = 10;
    console.log(x); // 10
}
ejemploVar();
```

###### `let:`
1. **Alcance de Bloque**: Las variables declaradas con `let` tienen alcance de bloque. Esto significa que sólo están disponibles dentro del bloque (`{}`) donde se declaran.
    
2. **No Hoisting**: Aunque `let` también es "hoisted", no puedes usar la variable antes de su declaración dentro del bloque.
    
3. **No Permite Redeclaración**: `let` no permite la redeclaración de la misma variable dentro del mismo ámbito, lo que ayuda a evitar errores.

``` js
function ejemploLet() {
    console.log(y); // ReferenceError: y is not defined
    let y = 10;
    console.log(y); // 10
}

ejemploLet();

```

Utilizar `let` es generalmente recomendado debido a su comportamiento más predecible y seguro, especialmente en entornos de desarrollo modernos.


#### ***Constantes:***
#constantes
En JavaScript, `const` se utiliza para declarar variables cuyo valor no debe cambiar. Aquí tienes una comparación entre `const`, `let`, y `var`:

###### `const:`
1. **Inmutabilidad**: Las variables declaradas con `const` no pueden ser reasignadas. Sin embargo, los objetos y arreglos declarados con `const` pueden ser modificados (sus propiedades o elementos pueden cambiar).
    
2. **Alcance de Bloque**: Similar a `let`, las variables declaradas con `const` tienen alcance de bloque.
    
3. **No Hoisting Utilizable**: Aunque `const` es "hoisted", no puedes usar la variable antes de su declaración.
``` js
/* Ejemplo N1 */
const PI = 3.14159;
console.log(PI); // 3.14159

PI = 3.14; // Esto lanzaría un error: TypeError: Assignment to constant variable.

/* Ejemplo N2 */
const obj = { nombre: "Juan" };
obj.nombre = "Pedro"; // Esto es válido
console.log(obj.nombre); // Pedro

obj = { nombre: "Carlos" }; // Esto lanzaría un error: TypeError: Assignment to constant variable.
```

Estas se pueden declarar siguiendo algunos [[4_Tipos de Datos#***Escritura de Código***| criterios]], estas forma de declarar variables, constantes, funciones, entre otras, no son obligatorias pero si son importante intentar de respetarlas ya que estas formas son convenciones o acuerdos a los que se llegaron con la intención de estandarizar el código y volverlo más legible.

## ***Convención de Sintaxis*** 
#sintaxis 

Los **identificadores** deben comenzar con: una letra (a-z, A-Z), signo de dolar ($), guión bajo... nunca con números o caracteres especiales.

Usa **snake_case**:
```js
mi_archivo_javascript.js // usado generalmente para definir nombre de archivos
```

#### **UPPER_CASE:**
Se utiliza para definir el nombre de las constantes
```js
const OTRA_CONSTANTE = "soy otra constante" 

const PI = 3.14159265358979
```

#### **UpperCamelCase**:
Se utiliza para definir clases
```js
class SerHumano {  
  constructor(nombre, genero) {
    this.nombre = nombre;
    this.genero = genero;
  }

  miNombreEs() {
    return `Mi nombre es ${this.nombre}`;
  }
}
```

#### **lowerCamelCase** :
Se utiliza para declarar primitivos, objetos, funciones e instancias
```js
let unaCadena = "Hola Mundo",

let unNumero = 19,

let unBoolean = true;

const unObjeto = {
  nombre: "Jonathan",
  email: "jonmircha@gmail.com",
};

function holaMundo(nombre) {
  alert(`Hola mundo ${nombre}`);
}
holaMundo("Jonathan");

const ajax = new XMLHttpRequest(),
  jon = new SerHumano("Jonathan", "Hombre");
```
