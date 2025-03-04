### **HTTP y HTTPS**
El protocolo HTTP (**Hypertext Transfer Protocol**) es la base de la comunicación en la web. Define cómo se transmiten los datos entre un cliente (navegador, aplicación) y un servidor.
- **HTTP (Hypertext Transfer Protocol)**: Protocolo sin cifrado, usado para transferir datos en la web.
- **HTTPS (Hypertext Transfer Protocol Secure)**: Versión segura de HTTP que utiliza **TLS (Transport Layer Security)** para cifrar la comunicación y proteger los datos de ataques como "man-in-the-middle".

Ejemplo de una URL con HTTPS:
``` sh
https://www.ejemplo.com/api/productos
```
El prefijo `https://` indica que la comunicación está cifrada.

---
### **Métodos HTTP**
Los métodos HTTP son acciones que se pueden realizar sobre los recursos de un servidor:

- **GET**: Solicita datos del servidor (Ejemplo: obtener un listado de productos).
- **POST**: Envía datos al servidor para crear un nuevo recurso (Ejemplo: registrar un usuario).
- **PUT**: Actualiza un recurso existente en el servidor (Ejemplo: modificar datos de un producto).
- **DELETE**: Elimina un recurso en el servidor (Ejemplo: borrar un usuario).
- **PATCH**: Similar a PUT, pero solo actualiza ciertos campos de un recurso.

Ejemplo de una solicitud `GET` en la terminal con `curl`:

``` sh
curl -X GET https://api.ejemplo.com/productos
```

### **Códigos de Estado HTTP**
Los códigos de estado informan al cliente sobre el resultado de su solicitud:
- **2xx (Éxito)**
    - `200 OK`: La solicitud fue exitosa.
    - `201 Created`: Un nuevo recurso fue creado.
- **3xx (Redirección)**
    - `301 Moved Permanently`: El recurso fue movido a otra URL.
    - `304 Not Modified`: Indica que el recurso no cambió desde la última solicitud.
- **4xx (Errores del Cliente)**
    - `400 Bad Request`: La solicitud tiene un formato incorrecto.
    - `401 Unauthorized`: No tiene autorización para acceder al recurso.
    - `403 Forbidden`: Acceso prohibido.
    - `404 Not Found`: El recurso no existe.
- **5xx (Errores del Servidor)**
    - `500 Internal Server Error`: Error inesperado en el servidor.
    - `503 Service Unavailable`: El servidor está sobrecargado o en mantenimiento.
