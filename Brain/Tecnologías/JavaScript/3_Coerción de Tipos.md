## **Coerción de Tipos en JavaScript**
La coerción de tipos es un mecanismo en JavaScript que permite convertir automáticamente valores de un tipo a otro cuando es necesario. Hay dos tipos principales de coerción de tipos: **implícita** y **explícita**. 

### **Coerción Implícita**
La `coerción implícita` ocurre cuando JavaScript convierte automáticamente un tipo de dato en otro durante la ejecución del código. Puede ser útil pero también puede llevar a comportamientos inesperados si no se comprende bien.

**Ejemplos de coerción implícita:**
- **Número a Cadena:**
``` js
let resultado = 5 + "5"; // "55" (el número 5 se convierte a cadena)
```

- **Cadena a Número:**
``` js
let resultado = "5" * 2; // 10 (la cadena "5" se convierte a número)
```

- **Booleano a Número:**
``` js
let resultado = true + 1; // 2 (true se convierte a 1)
```
  
- **Falsy Values:**
``` js
let resultado = 0 == false; // true (0 se convierte a false)
```

### **Coerción explícita**
La `coerción explícita` en JavaScript es el proceso de convertir manualmente un valor de un tipo de datos a otro utilizando funciones o métodos específicos. A diferencia de la coerción implícita, que es automática y a veces puede resultar confusa, la coerción explícita es intencional y controlada por el desarrollador. Aquí tienes una explicación y algunos ejemplos comunes:

#### Conversión a Número
Para convertir un valor a [[Number|número]], puedes usar la función `Number()`, `parseInt()`, o `parseFloat()`.

- *Number()*
``` js
let cadena = "123";
let numero = Number(cadena);
console.log(numero); // 123
console.log(typeof numero); // "number"
```

- *parseInt()*
``` js
let cadena = "123.45";
let numeroEntero = parseInt(cadena);
console.log(numeroEntero); // 123
console.log(typeof numeroEntero); // "number"
```

- *parseFloat()*
``` js
let cadena = "123.45";
let numeroDecimal = parseFloat(cadena);
console.log(numeroDecimal); // 123.45
console.log(typeof numeroDecimal); // "number"
```

#### Conversión a Cadena
Para convertir un valor a cadena, puedes usar la función `String()` o el método `toString()`.

- *String()*
``` js
let numero = 123;
let cadena = String(numero);
console.log(cadena); // "123"
console.log(typeof cadena); // "string"
```

- *toString()*
``` js
let numero = 123;
let cadena = numero.toString();
console.log(cadena); // "123"
console.log(typeof cadena); // "string"
```

#### Conversión a Booleano
Para convertir un valor a [[Boolean|booleano]], puedes usar la función `Boolean()`.

- *Boolean()*
``` js
let cadenaVacia = "";
let numeroCero = 0;
let objetoNulo = null;
let objetoIndefinido;
let valorTrue = "Hola";

console.log(Boolean(cadenaVacia)); // false
console.log(Boolean(numeroCero)); // false
console.log(Boolean(objetoNulo)); // false
console.log(Boolean(objetoIndefinido)); // false
console.log(Boolean(valorTrue)); // true
```
