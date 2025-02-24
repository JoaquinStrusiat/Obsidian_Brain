## Prototipos en JavaScript
#prototipos

En JavaScript, los prototipos son la base del sistema de herencia. Cada objeto tiene una referencia interna llamada `[[Prototype]]`, que apunta a otro objeto del que puede heredar propiedades y métodos. Este mecanismo permite reutilizar comportamientos sin copiar código.

**Resumen:**
- **Prototype chain (Cadena de prototipos):** Si un objeto no tiene una propiedad o método solicitado, JavaScript busca en su prototipo y continúa subiendo en la cadena hasta llegar a `null`.
- **Propiedad `prototype`:** Es una propiedad específica de las funciones constructoras. Define el prototipo que se asignará a los objetos creados con `new`.
- **Propiedad `__proto__`:** Es una referencia al prototipo de un objeto, aunque su uso es desalentado en favor de métodos como `Object.getPrototypeOf()`.

*Ejemplo básico de prototipos:*
``` js 
function Persona(nombre) {
  this.nombre = nombre;
}

Persona.prototype.saludar = function() {
  console.log(`Hola, soy ${this.nombre}`);
};

const juan = new Persona('Juan');
juan.saludar(); // "Hola, soy Juan"
```

#### Programación Orientada a Prototipos

Es un paradigma que utiliza objetos como bloques principales en lugar de clases. JavaScript no tiene clases "reales" (aunque la sintaxis `class` simplifica su uso) y se basa completamente en prototipos.

1. **Creación de objetos:**
    - Usando funciones constructoras.
    - Con el método `Object.create()`.
2. **Delegación prototípica:**
    - Objetos pueden delegar funcionalidad a través de la cadena de prototipos, lo que permite una herencia más flexible.
    - Es posible modificar el prototipo en tiempo de ejecución para cambiar el comportamiento de múltiples objetos.

*Ejemplo:*
``` js
const animal = {
  hacerSonido: function() {
    console.log("Sonido genérico");
  },
};

const perro = Object.create(animal);
perro.hacerSonido = function() {
  console.log("Guau");
};

const gato = Object.create(animal);
gato.hacerSonido = function() {
  console.log("Miau");
};

perro.hacerSonido(); // "Guau"
gato.hacerSonido();  // "Miau"
```

3. **Ventajas:**
    - Herencia dinámica: los cambios en el prototipo se reflejan automáticamente en los objetos que lo usan.
    - Flexibilidad para extender y modificar comportamientos.
4. **Desventajas:**
    - La programación basada en prototipos puede ser confusa para quienes provienen de lenguajes orientados a clases.
    - El uso ineficiente de la cadena de prototipos puede impactar el rendimiento en casos complejos.
