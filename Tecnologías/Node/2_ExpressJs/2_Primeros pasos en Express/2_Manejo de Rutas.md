### Rutas en Express
Como pudimos observar en el caso anterior, para crear un servidor `http`básico con Express debemos instanciar este módulo bajo una variable con el nombre de `app` en este caso y posteriormente definir una método el cual recibe una ruta de acceso y una función la cual se ejecutará cuando se acceda a dicha dirección:
![[1_Introducción a Express#**Creación de un servidor básico con Express**]]

### Direccionamiento básico
El _direccionamiento_ hace referencia a la determinación de cómo responde una aplicación a una solicitud de cliente en un determinado punto final, que es un URI (o una vía de acceso) y un método de solicitud HTTP específico (GET, POST, etc.).

Cada ruta puede tener una o varias funciones de manejador, que se excluyen cuando se correlaciona la ruta.

La definición de ruta tiene la siguiente estructura:
``` js
app.METHOD(PATH, HANDLER)
```
Donde:
- `app` es una instancia de `express`.
- `METHOD` es un [[3_Métodos HTTP en Express|método de solicitud HTTP]].
- `PATH` es una vía de acceso en el servidor.
- `HANDLER` es la función que se ejecuta cuando se correlaciona la ruta.

#### Ejemplos básicos de Rutas:
``` js
const express = require('express'); // Importar Express 
const app = express(); // Crear una instancia de la aplicación 
const PORT = 3000;

// Esta vía de acceso de ruta coincidirá con las solicitudes a la ruta raíz, `/`.
app.get('/', (req, res) => {
  res.send('root')
})

// Esta vía de acceso de ruta coincidirá con las solicitudes a `/about`.
app.get('/about', (req, res) => {
  res.send('about')
})

// Responda a la solicitud POST en la ruta raíz (`/`), la página de inicio de la aplicación:
app.post('/', (req, res) => {
  res.send('Got a POST request')
})

//Responda a una solicitud PUT en la ruta `/user`:
app.put('/user', (req, res) => {
  res.send('Got a PUT request at /user')
})

//Responda a una solicitud DELETE en la ruta `/user`:
app.delete('/user', (req, res) => {
  res.send('Got a DELETE request at /user')
})

// Iniciar el servidor 
app.listen(PORT, () => { console.log(`Servidor corriendo en http://localhost:${PORT}`); });
```

#### Rutas parametrizadas:
Se llama `parámetro` cuando se pasa un valor a través de una ruta de API. Podemos acceder a estos parámetros mediante mediante el objeto [[4_Request y Response Objects| Request]].

En particular, se pueden usar dos tipos de parámetros en las rutas de API: parámetros de ruta y parámetros de consulta.

###### **Parámetros de ruta**: 
- Son parte de la URL y se definen en la propia ruta. Por ejemplo, en una API de Express.
- En este caso, el `:id` es el parámetro de ruta, y se puede acceder a él mediante `req.params.id`:
``` js
// Definimos una ruta con un parámetro "id"
app.get('/users/:id', (req, res) => {
  const userId = req.params.id; // Accedemos al parámetro
  res.send(`El ID del usuario es: ${userId}`);
});
```


###### **Parámetros de consulta**: 
- Son valores que se pasan en la URL después de un signo de interrogación (?). Por ejemplo, en una API de Express
- En este ejemplo, el parámetro de consulta `q` se pasa en la URL como `/search?q=valor`:
``` js
// Definimos una ruta que maneje parámetros de consulta
app.get('/search', (req, res) => {
  const query = req.query.q; // Accedemos al parámetro de consulta
  res.send(`La consulta de búsqueda es: ${query}`);
});
```

- En este caso, la URL podría verse así: 
	- `http://miApi/search?q=valor&page=2&sort=asc
``` js
// Definimos una ruta que maneje múltiples parámetros de consulta
app.get('/search', (req, res) => {
  const query = req.query.q;
  const page = req.query.page;
  const sort = req.query.sort;

  res.send(`Consulta: ${query}, Página: ${page}, Orden: ${sort}`);
});
```








