## `Definición`:
En TypeScript, los **tipos personalizados** te permiten definir estructuras de datos propias, más allá de los tipos básicos como `string`, `number` o `boolean`. Son una herramienta poderosa para hacer tu código más claro, seguro y fácil de mantener.

###### 🧩 **Tipos (type)**: 
- Sirve para crear un nombre personalizado para un tipo de dato, ya sea simple o complejo.
``` ts
type ID = number;
type User = {
  id: ID;
  name: string;
  isAdmin: boolean;
};
```

###### 🧱 **Interfaces (interface)**: 
- Definen la forma de un objeto. Son similares a los `types`, pero más orientadas a la programación orientada a objetos.
``` ts
interface Product {
  name: string;
  price: number;
  inStock: boolean;
}
```

###### 🔗 **Uniones ( | )**:
- Permiten que una variable pueda tener más de un tipo.
``` ts
type Status = "success" | "error" | "loading";
let currentStatus: Status = "loading";
```

###### 🧬 **Intersecciones ( & )**:
- Combinan múltiples tipos en uno solo.
``` ts
type Admin = { role: "admin" };
type User = { name: string };
type AdminUser = Admin & User;
```

###### 🎯 **Tipos literales**:
Restringen una variable a un conjunto específico de valores.
``` ts
type Direction = "up" | "down" | "left" | "right";
```
######  🧮 **Tuplas**:
Definen un arreglo con un número fijo de elementos y tipos específicos
``` ts
let person: [string, number] = ["Joaquín", 30];
```

###### 🧾 **Enumeraciones (enum)**:
Definen un conjunto de constantes con nombres legibles
``` ts
enum Color {
  Red,
  Green,
  Blue
}
let favoriteColor: Color = Color.Green;
```

