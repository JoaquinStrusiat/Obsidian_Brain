En JavaScript, `null`, `undefined` y `NaN` son tres valores distintos que se utilizan para representar diferentes estados de datos. Aquí tienes una explicación detallada de cada uno de ellos y ejemplos para entender mejor sus diferencias y usos:

#### null
#null
- **Definición**: `null` es un valor asignado intencionalmente para indicar la ausencia de cualquier valor o un valor nulo.
    
- **Tipo**: `object` (aunque históricamente esto es un error en JavaScript).
    
- **Uso Común**: Se utiliza cuando quieres intencionalmente asignar un valor nulo a una variable.

**Ejemplo:**
``` js
let valorNulo = null;
console.log(valorNulo); // null
console.log(typeof valorNulo); // "object"
```

#### undefined
#undefined
- **Definición**: `undefined` significa que una variable ha sido declarada pero no se le ha asignado ningún valor.
    
- **Tipo**: `undefined`.
    
- **Uso Común**: Se asigna automáticamente a variables que han sido declaradas pero no inicializadas, y también es el valor de retorno de funciones que no devuelven explícitamente un valor.

**Ejemplo:**
``` js
let valorIndefinido;
console.log(valorIndefinido); // undefined
console.log(typeof valorIndefinido); // "undefined"

// Otra forma de obtener undefined
function sinRetorno() {}
console.log(sinRetorno()); // undefined
```

#### NaN
#NaN
- **Definición**: `NaN` significa "Not-a-Number" y representa un valor que no es un número válido.
    
- **Tipo**: `number`.
    
- **Uso Común**: Se produce cuando una operación matemática no tiene como resultado un número válido.

**Ejemplo:**
``` js
let resultado = "texto" / 2;
console.log(resultado); // NaN
console.log(typeof resultado); // "number"

// Comprobando si un valor es NaN
console.log(isNaN(resultado)); // true
```

##### Diferencias Claves
1) `null`:
    - Representa una ausencia intencional de valor.
    - Se asigna explícitamente por el programador.
2) `undefined`:
    - Indica que una variable ha sido declarada pero no inicializada.
    - Se asigna automáticamente por JavaScript.
3) `NaN`:
    - Representa un resultado no numérico de una operación matemática.
    - Se produce en cálculos matemáticos inválidos.