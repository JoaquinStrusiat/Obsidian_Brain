### Contexto:
Como mencionamos en [[4_Diseño de APIs RESTful y Formatos|Diseño de APIs RESTful y Formatos]] los métodos HTTP y como su nombre lo indican son los métodos accesores o de comunicación entre una aplicación del lado del cliente y nuestro servidor, y los más utilizados son los siguientes:
- **GET**: Solicita datos de un recurso específico. Es idempotente, lo que significa que múltiples solicitudes tendrán el mismo efecto que una sola.
- **POST**: Envía datos al servidor para crear o actualizar un recurso. A diferencia de GET, no es idempotente.
- **PUT**: Actualiza un recurso existente o lo crea si no existe. Es idempotente.
- **DELETE**: Elimina un recurso específico. También es idempotente.

#### Ejemplo de GET
Supongamos que tienes un blog y quieres obtener una lista de artículos:
``` js
app.get('/articulos', (req, res) => {
  const articulos = [
    { id: 1, titulo: 'Primer Artículo', contenido: 'Contenido del primer artículo' },
    { id: 2, titulo: 'Segundo Artículo', contenido: 'Contenido del segundo artículo' },
  ];
  res.json(articulos);
});
```

#### Ejemplo de POST
Para añadir un nuevo artículo a tu blog:
``` js
app.post('/articulos', (req, res) => {
  const nuevoArticulo = req.body;
  // Aquí puedes agregar lógica para guardar el nuevo artículo en una base de datos
  res.status(201).json(nuevoArticulo);
});
```

#### Ejemplo de PUT
Para actualizar un artículo existente:
``` js
app.put('/articulos/:id', (req, res) => {
  const { id } = req.params;
  const articuloActualizado = req.body;
  // Aquí puedes agregar lógica para actualizar el artículo en la base de datos
  res.json({ id, ...articuloActualizado });
});
```

### Ejemplo de DELETE
Para eliminar un artículo:
``` js
app.delete('/articulos/:id', (req, res) => {
  const { id } = req.params;
  // Aquí puedes agregar lógica para eliminar el artículo de la base de datos
  res.status(204).send();
});
```