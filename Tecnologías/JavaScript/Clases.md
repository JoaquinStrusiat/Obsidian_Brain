## Introducción a Clases
En javascript no existen las clases como tal, este lenguaje es orientado a [[Objetos]] pero basado en [[Prototipos|prototipos]]. Con las últimas actualizaciones se introdujo la posibilidad sintáctica (`Syntactic Sugar`) de definir objetos a través de clases, pero esto sin modificar el funcionamiento ni el comportamiento original del lenguaje el cual son los prototipos.

#### **Definición de Clases:**
#clases

Para definir clases javascript nos proporciona la clase reservada `class`, la cual la implementamos de la siguiente manera: 
``` js
// Declaración de clase | class declaration
class Curso {
	constructor(titulo){
		this.titulo = titulo;
	}
	inscribir(){
		console.log("Incripto al curso")
	}
};

//Instanciamos un objeto
let js = new Curso("Curso de Javascript");

console.log(js.titulo); // Salida: Curso de Javascript
js.inscribir(); // Salida: Incripto al curso
```

``` js
// Expreción de clase | class exprecion 
const CursoExpresado = class {
	constructor(titulo){
		this.titulo = titulo;
	}
	inscribir(){
		console.log("Incripto al curso")
	}
}
```

#### **Método Constructor**
#constructor #clases

El método constructor es la función principal que se ejecuta por defecto al momento de instanciar un nuevo objeto y da la posibilidad de asignar valores a las propiedades definidas en la clase en el momento de su instancia. Para esto usamos la palabra reservada `contructor` la cual solo será tomada como tal en el contexto de una clase a la que anteriormente le hayamos definido dicho método:
``` js
// Expreción de clase | class exprecion 
class Curso{
	constructor(titulo){
		this.titulo = titulo;
	}
}
let javascript = new Curso("Curso de Javascript");
```

Otra característica del método constructor es que nos provee de un objeto `arguments` con todos los valores que recibe el método constructor por parámetro
``` js
// Expreción de clase | class exprecion 
class Curso{
	constructor(titulo){
		this.titulo = titulo;
		console.log(arguments);
	}
}
let javascript = new Curso("Curso de Javascript", 10, true);
/* Salida:
{
	0 : "Curso de Javascript",
	1 : 10,
	2 : true,
}
*/
```


#### **Definir propiedades y métodos:**
#propiedades #metodos #clases

En javascript a día de hoy (2025) existen tres maneras de definir propiedades en una clase pero no todas de ellas o por lo menos no la primera que voy a mostrar está soportada por todos los navegadores a día de hoy:

##### *Asignación de propiedad por defecto (disponible solo en las nuevas versiones de ECMA):*
``` js
class Curso {
	titulo = "Javascript";
}

let js = new Curso();
console.log(js.titulo); // Salida: Javascript
```

##### *Asignación de propiedad por método constructor:*
El método constructor permite pasar valores por parámetros y asignarlos a un atributo del objeto mediante la palabra reservada `this`:
``` js
class Curso {
	constructor(title){
		this.titulo = title;
	}
}

let js = new Curso("Javascript para principiantes");
console.log(js.titulo); // Salida: Javascript para principiantes
```

##### *Asignación de propiedad por métodos de instancia:*
También podemos instanciar atributos dentro de nuestro objeto mediante algún método de instancia:
``` js
class Curso {
	titularCurso(title){
		this.titulo = title;
	};
	nombrarCurso  = (name) => this.nombre = name;  
}

let js = new Curso();
js.titularCurso("JS para principiantes")
console.log(js.titulo); // Salida: JS para principiantes
```

#### **Alcance de propiedades**
#alcance #clases

Como mencionamos anteriormente javascript no maneja las clases como otros lenguajes ya que por detrás esta realmente está funcionando mediante prototipos, pero si nos proveen de algunas ayudas sintácticas para declarar este paradigma (paradigma orientado a objetos). Para limitar el alcance de las propiedades (volverlas publicas o privadas), javascript nos provee de la sintaxis de `#value`, en la cual agregamos un asterisco delante del nombre de la propiedad que vamos a definir en la clase para especificar que esta es de naturaleza `privado`.

Cuando hablamos de propiedades públicas y privadas, solo hacemos referencia al comportamiento que pueden tener las propiedades a la hora de instanciarlas o mutarlas, por defecto javascript nos permite mutar o cambiar el valor de cualquiera de de sus propiedades una vez que el objeto ya fue instanciado, y podemos acceder a sus valores mediante la sintaxis "`objeto.propiedad = valor`" , pero en ocasiones y por integridad de nuestro código necesitamos que las propiedades de nuestro objeto solo puedan ser accedidas o mutadas desde dentro del mismo objeto a través de algún método, esto nos da la posibilidad de poder tener control total del tipo de valor que queremos que sea almacenado en dicha propiedad:
``` js
// PROPIEDADES DE ALCANCE PÚBLICO --------------------
class Curso{
	this.titulo = "JavaScript"
}
// en este caso podemos acceder a la propiedad título de cualquier objeto del tipo curso desde cualquier parte del código ya que esta es de alcance global o público
const nuevoCurso = new Curso();
console.log(nuevoCurso.titulo);// Salida: JavaScript

// PROPIEDADES DE ALCANCE PRIVADO --------------------
class Curso{
	#titulo = "JavaScript"
}
// en este caso no poríamos acceder a  a la propiedad titulo por fuera del objeto ya que su alcance es local o privado
const nuevoCurso = new Curso();
console.log(nuevoCurso.titulo);// Salida: error, Privated filed
```

Como dijimos anteriormente para poder mutar una propiedad del objeto en cuestión solo podríamos hacerlo a través de algún método publico que definamos en nuestra clase:
``` js
class Curso{
	constructor(title){
		this.#titulo = title;
	}
	getTitle(){
		return this.#titulo;
	}
}
const nuevoCurso = new Curso("Curso de JS");
console.log(nuevoCurso.getTitle()); // Salida: Curso de JS
```

#### **Métodos accesores**
#metodos_accesores #clases

En JavaScript, los métodos accesores se usan para obtener y establecer el valor de propiedades de un objeto de manera controlada. Estos métodos suelen implementarse utilizando `getters` y `setters`. A continuación, te explico cómo funcionan y un ejemplo práctico.
- **Getters**
	- Permiten acceder al valor de una propiedad como si fuera un atributo.
	- Se definen usando la palabra clave `get`.

- **Setters**
	- Permiten modificar el valor de una propiedad mientras controlas cómo se establece.
	- Se definen usando la palabra clave `set`.

*Ejemplos de métodos accesores:*
``` js
class Persona {
  // Declaración de atributos privados
  #nombre;
  #edad;

  constructor(nombre, edad) {
    this.#nombre = nombre; // Inicialización de atributos privados
    this.#edad = edad;
  }

  // Getter para el nombre
  get nombre() {
    return this.#nombre;
  }

  // Setter para el nombre
  set nombre(nuevoNombre) {
    if (typeof nuevoNombre === 'string' && nuevoNombre.trim() !== '') {
      this.#nombre = nuevoNombre;
    } else {
      console.error('Nombre inválido');
    }
  }

  // Getter para la edad
  get edad() {
    return this.#edad;
  }

  // Setter para la edad
  set edad(nuevaEdad) {
    if (Number.isInteger(nuevaEdad) && nuevaEdad > 0) {
      this.#edad = nuevaEdad;
    } else {
      console.error('Edad inválida');
    }
  }
}

// Uso de la clase
const persona = new Persona('Juan', 25);

console.log(persona.nombre); // Juan
persona.nombre = 'Ana';
console.log(persona.nombre); // Ana

console.log(persona.edad); // 25
persona.edad = 30;
console.log(persona.edad); // 30

// Intentar acceder a los atributos privados directamente
console.log(persona.#nombre); // Error: Private field '#nombre' must be declared in an enclosing class
```
#### **Herencia de clases**
#herencia #clases

La herencia es la capacidad que tiene un objeto de heredar u obtener los atributos o métodos de otro objeto al que llamamos padre. 
Esto nos permite reutilizar mucho código a la hora de desarrollar nuestros programas y aplicaciones ya que en muchas ocasiones tenderemos que definir clases y objetos que comparten atributos y solo se diferencian en un par de propiedad o método. 
Para solucionar este problema recurrimos a la utilización de herencia, en la que procedemos a crear una clase padre con los atributos comunes a los demás y clases particulares (hijas), que extiendan las propiedades de esta anterior y solo agregando propiedades y métodos relacionados a ella mima: 

*Ejemplo de Herencia:*
``` js
class Animal {
    constructor(nombre) {
        this.nombre = nombre;
    }
    
    getNombre(){
	    console.log(this.nombre);
    }
    
    hacerSonido() {
        console.log("Este animal hace un sonido.");
    }
}

class Perro extends Animal {
	// Sobre escritura de un método
    hacerSonido() {
        console.log("¡Guau, guau!");
    }
}

class Gato extends Animal {
	// Sobre escritura de un método
    hacerSonido() {
        console.log("¡Miauuu!");
    }
}

const perro = new Perro("Firulais");
perro.getNombre(); // Output: Firulais
perro.hacerSonido(); // Output: ¡Guau, guau!

const gato = new Gato("Michi");
gato.getNombre(); // Output: Michi
gato.hacerSonido(); // Output: ¡Miauuu!
```

*Método super:*
``` js
class Animal {
    constructor(nombre) {
        this.nombre = nombre;
    }

    presentarse() {
        console.log(`Soy un animal llamado ${this.nombre}.`);
    }
}

class Perro extends Animal {
    constructor(nombre, raza) {
        super(nombre); // Llama al constructor de la clase padre (Animal)
        this.raza = raza; // Agrega atributos específicos de la clase hija
    }

    ladrar() {
        console.log("¡Guau, guau!");
    }
}

const miPerro = new Perro("Firulais", "Labrador");
miPerro.presentarse(); // Output: Soy un animal llamado Firulais.
miPerro.ladrar(); // Output: ¡Guau, guau!
```

#### **Métodos y propiedades estáticas**
#propiedades_estáticas #clases

*Propiedades estáticas:* Las propiedades estáticas son variables asociadas a la clase, no a sus instancias.
*Métodos estáticos:* Los métodos estáticos son funciones que no dependen de las instancias de la clase. Son útiles para operaciones generales o utilidades relacionadas con la clase.

*Ejemplos:*
``` js
class Calculadora {
  // Propiedad estática
  static PI = 3.14159;

  // Método estático
  static sumar(a, b) {
    return a + b;
  }

  static restar(a, b) {
    return a - b;
  }

  // Método no estático
  multiplicar(a, b) {
    return a * b;
  }
}

// Uso de métodos y propiedades estáticas
console.log(Calculadora.PI); // 3.14159
console.log(Calculadora.sumar(10, 5)); // 15
console.log(Calculadora.restar(10, 5)); // 5

// Intentar usar un método estático desde una instancia
const calc = new Calculadora();
console.log(calc.multiplicar(2, 3)); // 6
// console.log(calc.sumar(2, 3)); // Error: sumar no es una función de la instancia
```

**Cuando usar métodos y propiedades estáticas**

1. **Métodos compartidos:** Operaciones independientes de una instancia, como funciones matemáticas o validaciones.
2. **Propiedades globales:** Constantes o configuraciones que no necesitan ser replicadas en cada instancia.

