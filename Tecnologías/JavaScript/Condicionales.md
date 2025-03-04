## Condicionales en JavaScript
#condicionales
Los condicionales en JavaScript se utilizan para tomar decisiones en el flujo del programa basadas en condiciones. 

Entre ellos podríamos destacar los principales 3 tipos de ellos:
1) [[Condicionales#Caso 1 `if`|if]] : Evalúa una condición y ejecuta código si es verdadera.
2) [[Condicionales#Caso 2 `if...else`|if...else]] : Evalúa una condición y elige entre dos bloques de código.
	1) [[Condicionales#Caso 2.1 `if...else if...else`|if...else if...else]] : Evalúa múltiples condiciones en secuencia.
3) [[Condicionales#Caso 3 `switch`|witch]] : Evalúa una expresión y ejecuta el bloque de código correspondiente a su valor.

#### Ejemplos:
##### Caso 1: `if`:
#condicional_if
Evalúa una condición y ejecuta un bloque de código si la condición es verdadera.
``` js
let edad = 18;

if (edad >= 18) {
    console.log("Eres mayor de edad.");
}
// Salida: "Eres mayor de edad."
```

##### Caso 2: `if...else`:
#condicional_if_else
Evalúa una condición y ejecuta un bloque de código si la condición es verdadera, y otro bloque si es falsa.
``` js
let edad = 16;

if (edad >= 18) {
    console.log("Eres mayor de edad.");
} else {
    console.log("Eres menor de edad.");
}
// Salida: "Eres menor de edad."

```

##### Caso 2.1: `if...else if...else`:
#condicional_if_else_if_else
Permite evaluar múltiples condiciones en secuencia, ejecutando bloques de código para la primera condición que sea verdadera.
```js
let nota = 85;

if (nota >= 90) {
    console.log("Calificación: A");
} else if (nota >= 80) {
    console.log("Calificación: B");
} else if (nota >= 70) {
    console.log("Calificación: C");
} else {
    console.log("Calificación: F");
}
// Salida: "Calificación: B"
```

##### Caso 3: `switch`:
#condicional_switch
Evalúa una expresión y ejecuta bloques de código basados en el valor de la expresión. Es útil cuando tienes múltiples posibles valores para una sola expresión.
``` js
let dia = 3;
let nombreDia;

switch (dia) {
    case 1:
        nombreDia = "Lunes";
        break;
    case 2:
        nombreDia = "Martes";
        break;
    case 3:
        nombreDia = "Miércoles";
        break;
    case 4:
        nombreDia = "Jueves";
        break;
    case 5:
        nombreDia = "Viernes";
        break;
    case 6:
        nombreDia = "Sábado";
        break;
    case 7:
        nombreDia = "Domingo";
        break;
    default:
        nombreDia = "Día inválido";
}
console.log(nombreDia); // "Miércoles"

```