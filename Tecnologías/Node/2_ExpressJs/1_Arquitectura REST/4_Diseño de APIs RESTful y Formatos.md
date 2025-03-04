### **Estructura de URLs (Endpoints)**
Un **endpoint** es una URL donde se accede a un recurso. Debe ser **claro y coherente**.
Ejemplo de una API para gestionar productos:

|Método HTTP|Endpoint|Acción|
|---|---|---|
|`GET`|`/productos`|Obtener todos los productos|
|`GET`|`/productos/1`|Obtener un producto específico|
|`POST`|`/productos`|Crear un nuevo producto|
|`PUT`|`/productos/1`|Actualizar un producto|
|`DELETE`|`/productos/1`|Eliminar un producto|

**Buenas prácticas:**
- Usar **nombres en plural** (`/usuarios`, `/productos`).
- **No incluir verbos en la URL** (`/crearProducto` ❌, `/productos` ✅).
- Utilizar **códigos de estado HTTP adecuados** (`201 Created` para nuevos recursos).

### **Formatos de Datos Comunes**

#### **JSON (JavaScript Object Notation)**
JSON es el formato más utilizado en APIs REST debido a su **simplicidad** y **compatibilidad** con múltiples lenguajes.
Ejemplo de un objeto JSON:
``` js
{
  "id": 1,
  "nombre": "Laptop",
  "precio": 799.99
}
```
Ventajas: ✔ Ligero y fácil de leer.  
✔ Compatible con múltiples lenguajes.  
✔ Soporta estructuras anidadas.

#### **XML (Extensible Markup Language)**
Antes era popular, pero hoy se usa menos en REST debido a su complejidad.
Ejemplo de XML:
``` xml
<producto>
  <id>1</id>
  <nombre>Laptop</nombre>
  <precio>799.99</precio>
</producto>
```
Comparación JSON vs. XML:
- **JSON** es más ligero y fácil de manejar.
- **XML** tiene una estructura más formal y es usado en **SOAP**.