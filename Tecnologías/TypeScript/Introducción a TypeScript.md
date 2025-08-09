 🔥 TypeScript es un **lenguaje de programación de código abierto** desarrollado por Microsoft que **extiende JavaScript** agregando tipos estáticos y otras características avanzadas. Es un **superset** de JavaScript, lo que significa que cualquier código JavaScript válido también es código TypeScript válido.

### **Características principales de TypeScript:**

1. **Tipado estático**: Permite definir tipos para variables, parámetros y funciones, lo que ayuda a detectar errores durante el desarrollo.
```ts
let nombre: string = "Juan";
let edad: number = 25;
```

2. **Compilación a JavaScript**: TypeScript se compila a JavaScript puro (ES3, ES5, ES6, etc.) para ser ejecutado en cualquier navegador o entorno Node.js.

3. **Autocompletado y herramientas avanzadas**: Mejora la experiencia de desarrollo con sugerencias de código y detección temprana de errores.

4. **Interfaces y tipos personalizados**: Permite definir estructuras de datos complejas.
``` ts
interface Persona {
  nombre: string;
  edad: number;
}
```

5. **Compatibilidad con JS**: Puedes usar librerías de JavaScript existentes y migrar gradualmente a TypeScript.

6. **Soporte para POO**: Clases, herencia, modificadores de acceso (`public`, `private`, `protected`), etc.
``` ts
class Animal {
  constructor(public nombre: string) {}
}
```

### **¿Por qué usar TypeScript?**

- **Menos errores en tiempo de ejecución**: Los tipos ayudan a detectar problemas antes de ejecutar el código.
    
- **Mejor mantenibilidad**: El código es más legible y fácil de refactorizar.
    
- **Escalabilidad**: Ideal para proyectos grandes y equipos de desarrollo.

### **Ejemplo comparativo (TypeScript vs JavaScript):**

**JavaScript (sin tipos)**
``` js
function sumar(a, b) {
  return a + b;
}
sumar(10, "20"); // Resultado: "1020" (error no detectado)
```

**TypeScript (con tipos)**
```ts
function sumar(a: number, b: number): number {
  return a + b;
}
sumar(10, "20"); // ¡Error detectado en tiempo de compilación!
```