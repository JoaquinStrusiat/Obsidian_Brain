En Express.js, los objetos `Request` y `Response` son fundamentales para el manejo de solicitudes y respuestas HTTP. Aquí tienes una descripción de algunos atributos importantes de cada uno:

### Objeto Request (`req`)

- `req.params`: Contiene los parámetros de ruta (por ejemplo, `/users/:id`).
- `req.query`: Contiene los parámetros de consulta (por ejemplo, `?q=valor`).
- `req.body`: Contiene los datos del cuerpo de la solicitud (útil para manejar datos enviados en solicitudes `POST`).
- `req.headers`: Contiene los encabezados HTTP enviados por el cliente.
- `req.method`: Contiene el método HTTP utilizado en la solicitud (por ejemplo, `GET`, `POST`).
- `req.url`: Contiene la URL completa de la solicitud.
- `req.path`: Contiene solo la ruta de la solicitud (sin la cadena de consulta).
- `req.cookies`: Contiene las cookies enviadas por el cliente (requiere middleware adicional).

### Objeto Response (`res`)
- `res.send()`: Envía una respuesta al cliente. Puede enviar texto, HTML, JSON, etc.
- `res.json()`: Envía una respuesta en formato JSON.
- `res.status()`: Establece el código de estado HTTP para la respuesta (por ejemplo, `res.status(404)`).
- `res.sendFile()`: Envía un archivo como respuesta (por ejemplo, `res.sendFile('/ruta/al/archivo')`).
- `res.redirect()`: Redirige la solicitud a una URL diferente (por ejemplo, `res.redirect('/otra-ruta')`).
- `res.set()`: Establece los encabezados HTTP de la respuesta (por ejemplo, `res.set('Content-Type', 'text/html')`).
- `res.cookie()`: Establece una cookie en la respuesta (requiere middleware adicional).
- `res.end()`: Finaliza la respuesta sin enviar ningún dato adicional.

### Ejemplo:
``` js
const express = require('express');
const app = express();

app.get('/users/:id', (req, res) => {
  const userId = req.params.id;
  res.status(200).json({ message: `El ID del usuario es: ${userId}` });
});

app.post('/data', (req, res) => {
  const data = req.body;
  res.send(`Datos recibidos: ${JSON.stringify(data)}`);
});

app.listen(3000, () => {
  console.log('Servidor escuchando en el puerto 3000');
});
```
