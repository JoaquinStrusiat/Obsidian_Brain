##  **Resumen de Tipos de Datos en TypeScript** 📌
TypeScript agrega **tipos estáticos** a JavaScript para mejorar la seguridad y mantenibilidad del código. Aquí tienes una explicación detallada de los tipos básicos y avanzados:

### **Tipos Primitivos**
Son los tipos fundamentales que representan valores simples.

1. **string** - Texto
```ts
let nombre: string = "Ana";
let mensaje: string = `Hola, ${nombre}`; // Template literals
```

2. **number** - Números (enteros, decimales, hexadecimales, etc.)
``` ts
let edad: number = 25;
let precio: number = 9.99;
let hex: number = 0xff; // Hexadecimal
```

3. **boolean** - Verdadero o falso
```ts
let esActivo: boolean = true;
let tienePermiso: boolean = false;
```

4. **null y undefined** - Representan la ausencia de valor.
```ts
let vacio: null = null;
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

2. **`tuple`** - Arreglo con tipos fijos en posiciones específicas
```ts
let persona: [string, number] = ["Juan", 30]; // [nombre, edad]
```

3. **`object`** - Estructuras clave-valor (no primitivos)
```ts
let person: Object = {};
let usuario: { nombre: string; edad: number } = {
  nombre: "Carlos",
  edad: 28,
};
``` 

4. **`any`** - Desactiva el tipado (evitar su uso)
```ts
let variableFlexible: any = "puede ser cualquier cosa";
variableFlexible = 42; // No hay error
```

5. **`unknown`** - Similar a `any`, pero más seguro (requiere verificación)
```ts
let valorDesconocido: unknown = "Hola";
if (typeof valorDesconocido === "string") {
  console.log(valorDesconocido.toUpperCase()); // Ahora es seguro
}
```

6. **`void`** - Para funciones que no retornan nada
```ts
function saludar(): void {
  console.log("Hola!");
}
```

7. **`never`** - Para funciones que nunca terminan (ej: lanzan errores)
```ts
function error(mensaje: string): never {
  throw new Error(mensaje);
}
```

### **Tipos Personalizados**

1. **`type`** - Alias para tipos complejos
``` ts
type ID = string | number;
let userId: ID = "abc123";
```

2. **`interface`** - Define la forma de un objeto
```ts
interface Persona {
  nombre: string;
  edad: number;
  opcional?: string; // Propiedad opcional
}
```

3. **Uniones (`|`) e Intersecciones (`&`)**
```ts
type NumeroOTexto = number | string;
type UsuarioYAdmin = Persona & { esAdmin: boolean };
```

### **Ejemplo Integrado**

```ts
type Rol = "admin" | "usuario" | "invitado";

interface Usuario {
  id: number;
  nombre: string;
  rol: Rol;
  habilidades: string[];
}

const juan: Usuario = {
  id: 1,
  nombre: "Juan Pérez",
  rol: "admin",
  habilidades: ["TypeScript", "React"],
};
```