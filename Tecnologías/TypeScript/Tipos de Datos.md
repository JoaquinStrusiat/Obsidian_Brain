##  **Resumen de Tipos de Datos en TypeScript** 📌
TypeScript agrega **tipos estáticos** a JavaScript para mejorar la seguridad y mantenibilidad del código. Aquí tienes una explicación detallada de los tipos básicos y avanzados:

### **Tipos Primitivos**
Son los tipos fundamentales que representan valores simples.

1. **string** - Texto
```ts
//string -----------------------------------
let nombre: string = "Ana";
let mensaje: string = `Hola, ${nombre}`; 

//number -----------------------------------
let edad: number = 25;
let precio: number = 9.99;
let hex: number = 0xff; // Hexadecimal

// boolean ---------------------------------
let esActivo: boolean = true;
let tienePermiso: boolean = false;

//null -------------------------------------
let vacio: null = null;

//undefined --------------------------------
let sinDefinir: undefined = undefined;
```

### **Tipos Compuestos o complejos** 
1. **`array`** - Listas de elementos
```ts
let numeros: number[] = [1, 2, 3];
let lugares: strings[] = ["plaza", "ciudad"];
let frutas: Array<string> = ["manzana", "banana"]; // Sintaxis genérica
let objetos: Object[] = [{},{}];
```

2. **`object`** - Estructuras clave-valor (no primitivos)
```ts
let person: Object = {};
let usuario: { nombre: string; edad: number } = {
  nombre: "Carlos",
  edad: 28,
};
``` 

3. **`any`** - Desactiva el tipado (evitar su uso)
```ts
let variableFlexible: any = "puede ser cualquier cosa";
variableFlexible = 42; // No hay error
```

4. **`unknown`** - Similar a `any`, pero más seguro (requiere verificación)
```ts
let valorDesconocido: unknown = "Hola";
if (typeof valorDesconocido === "string") {
  console.log(valorDesconocido.toUpperCase()); // Ahora es seguro
}
```

5. **`void`** - Para funciones que no retornan nada
```ts
function saludar(): void {
  console.log("Hola!");
}
```

6. **`never`** - Para funciones que nunca terminan (ej: lanzan errores)
```ts
function error(mensaje: string): never {
  throw new Error(mensaje);
}
```

###  **Type Assertion (aserción de tipo)**:
En TypeScript, el **Type Assertion** (o _aserción de tipo_) es una forma de decirle al compilador: “confía en mí, sé exactamente qué tipo tiene esta variable”. Es útil cuando el sistema de inferencia de TypeScript no puede determinar el tipo con precisión, pero vos sí.

🧠 ¿Para qué sirve?
- Evita errores de tipo cuando estás seguro del valor.
- Mejora el autocompletado y validación en el editor.
- Es común al trabajar con datos externos (APIs, DOM, librerías JS).

🧰 Sintaxis
Hay **dos formas** de hacer una aserción de tipo:
1. Usando `as`:
``` ts
let valor: any = "Hola TypeScript";
let longitud: number = (valor as string).length;
```

2. Usando `<Tipo>` (no recomendado en JSX)
``` ts
let valor: any = "Hola TypeScript";
let longitud: number = (<string>valor).length;
```

>  En proyectos con JSX (como React), usa `as` porque los `< >` pueden causar conflictos con el parser

🧬 Ejemplo con datos de APis:
``` ts
interface Usuario {
  id: number;
  nombre: string;
}

const respuesta: any = obtenerDatos();
const usuario = respuesta as Usuario;
console.log(usuario.nombre);
```

