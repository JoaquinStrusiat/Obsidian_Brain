## Introducción
En la arquitectura cliente-servidor, dos entidades principales interactúan:

### **1. Cliente**
El cliente es la aplicación que solicita datos. Puede ser:
- Un **navegador web** (Google Chrome, Firefox).
- Una **aplicación móvil** (Android, iOS).
- Una **herramienta de línea de comandos** (`curl`, Postman).

### **2. Servidor**
El servidor procesa las solicitudes del cliente y devuelve respuestas. Un servidor puede estar construido con tecnologías como:
- Node.js (JavaScript)
- Django (Python)
- Spring Boot (Java)
- Express.js (JavaScript)

### **Peticiones (Requests) y Respuestas (Responses)**
- **Request (Petición)**: El cliente envía una solicitud al servidor con datos como:
    - **Método HTTP** (`GET`, `POST`, etc.).
    - **Encabezados** (información sobre la solicitud).
    - **Cuerpo** (datos en JSON o XML, si es necesario).
- **Response (Respuesta)**: El servidor devuelve una respuesta con:
    - **Código de estado HTTP** (`200 OK`, `404 Not Found`).
    - **Encabezados** (tipo de contenido, cookies, etc.).
    - **Cuerpo** (datos en formato JSON, HTML, etc.).

Ejemplo de solicitud y respuesta en JSON:
🔹 **Request (Cliente)**:
``` sh
POST /api/usuarios HTTP/1.1
Host: api.ejemplo.com
Content-Type: application/json

{
  "nombre": "Juan",
  "email": "juan@email.com"
}
```

🔹 **Response (Servidor)**:
``` sh
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": 1,
  "nombre": "Juan",
  "email": "juan@email.com"
}
```