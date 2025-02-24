## Tipo de dato **Boolean**
En JavaScript, un booleano es un tipo de dato primitivo que puede tener uno de dos valores: `true` o `false`. Los booleanos se utilizan comúnmente para representar valores de verdad y son esenciales en las estructuras de control, como las declaraciones `if`, bucles y otras operaciones lógicas.

#### Declaración de Booleanos
``` js
let esVerdadero = true;
let esFalso = false;

console.log(esVerdadero); // true
console.log(esFalso); // false
```

#### Uso de booleanos:
Los valores booleanos son los principales responsables al momento de programar [[Condicionales]] y [[Ciclos o Bucles]] los cuales a su vez utilizan [[Operadores Lógicos]] y [[Operadores de Comparación]] para su ejecución o flujo de trabajo.

Algunos ejemplos de ellos son los siguientes:

**Uso en Condicionales:**
``` js
let esMayor = 10 > 5;

if (esMayor) {
    console.log("10 es mayor que 5");
} else {
    console.log("10 no es mayor que 5");
}
// Salida: "10 es mayor que 5"
```

**Uso en Ciclos o Bucles:**
``` js
let contador = 0;
let seguirContando = true;

while (seguirContando) {
    console.log(contador);
    contador++;
    if (contador >= 5) {
        seguirContando = false;
    }
}
// Salida: 0, 1, 2, 3, 4
```

#### Valores Truthy y Falsy
#truthy #falsy
En JavaScript, ciertos valores se consideran `falsy` (evaluados como `false` en un contexto booleano), mientras que otros se consideran `truthy` (evaluados como `true` en un contexto booleano).

###### ***Valores Falsy:***
- `false`
- `0`
- `""` (cadena vacía)
- `null`
- `undefined`
- `NaN`
``` JS
let falsyValores = [false, 0, "", null, undefined, NaN];

falsyValores.forEach(valor => {
    if (valor) {
        console.log(`${valor} es truthy`);
    } else {
        console.log(`${valor} es falsy`);
    }
});
// Salida: 
// "false es falsy"
// "0 es falsy"
// " es falsy"
// "null es falsy"
// "undefined es falsy"
// "NaN es falsy"
```

###### ***Valores Truthy:*** 
- Cualquier valor que no sea `falsy` se considera `truthy`.
``` js
let truthyValores = [true, 1, "texto", {}, [], function() {}];

truthyValores.forEach(valor => {
    if (valor) {
        console.log(`${valor} es truthy`);
    } else {
        console.log(`${valor} es falsy`);
    }
});
// Salida: 
// "true es truthy"
// "1 es truthy"
// "texto es truthy"
// "[object Object] es truthy"
// "" es truthy"
// "function() {} es truthy"
```