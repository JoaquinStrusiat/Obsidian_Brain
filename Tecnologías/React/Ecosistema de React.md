Para trabajar con react vamos a trabajar con una serie de de herramientas que nos ayudarán a desarrollar el código de una forma más limpia y simple a lo largo de nuestro proyecto:

### Complementos:
##### **Vite:**
Vite es una herramienta de compilación diseñada para proporcionar una experiencia de desarrollo rápida y eficiente en proyectos web modernos. En el contexto de React, Vite se usa como alternativa a herramientas como Webpack para configurar y ejecutar aplicaciones de manera más ágil.

**Algunas ventajas de Vite en React incluyen:**
- **Inicio rápido**: Usa módulos ES nativos para evitar procesos de empaquetado innecesarios.
- **Hot Module Replacement (HMR) ultrarrápido**: Permite ver cambios en tiempo real sin recargar toda la aplicación.
- **Compilación optimizada**: Utiliza Rollup para generar archivos de producción altamente optimizados.
- **Compatibilidad con TypeScript y JSX**: Facilita el desarrollo con tecnologías modernas.

*Página web y documentación:* https://vite.dev 

#### **Redux:**
Redux es una biblioteca de gestión de estado para aplicaciones JavaScript, especialmente útil en proyectos con React. Su propósito es hacer que el estado de la aplicación sea más predecible y fácil de manejar.

**¿Por qué usar Redux?**
- **Estado centralizado**: Toda la información de la aplicación se almacena en un único lugar llamado _store_.
- **Flujo de datos unidireccional**: Los cambios en el estado ocurren de manera controlada mediante _acciones_ y _reducers_.
- **Depuración sencilla**: Gracias a herramientas como Redux DevTools, puedes ver cómo cambia el estado en cada acción.
- **Escalabilidad**: Ideal para aplicaciones grandes con múltiples componentes que necesitan compartir datos.

*Página web y documentación:* https://redux.js.org 

#### **Zustand:**
Es una biblioteca de gestión de estado para React que es ligera, rápida y fácil de usar. Es una alternativa a Redux que permite manejar el estado global sin necesidad de un proveedor ni configuraciones complejas.

**¿Por qué usar Zustand?**
- **Simplicidad**: Usa una API basada en hooks, lo que facilita su implementación.
- **Menos código**: No requiere acciones ni reducers como Redux.
- **Eficiencia**: Solo vuelve a renderizar los componentes cuando el estado cambia.
- **Flexibilidad**: Compatible con TypeScript y otras tecnologías.

**Ejemplo de uso:**
``` js
import { create } from 'zustand';

const useStore = create((set) => ({
  count: 0,
  increase: () => set((state) => ({ count: state.count + 1 })),
  decrease: () => set((state) => ({ count: state.count - 1 })),
}));

//componente
const Counter = () => {
  const { count, increase, decrease } = useStore();
  return (
    <div>
      <p>Contador: {count}</p>
      <button onClick={increase}>Incrementar</button>
      <button onClick={decrease}>Disminuir</button>
    </div>
  );
};

```

*Página web y documentación:* https://zustand-demo.pmnd.rs

#### **React Router:**
**React Router** es una biblioteca de enrutamiento para aplicaciones React que permite la navegación entre diferentes páginas sin recargar la aplicación. Es la solución más popular para manejar rutas en React.

**Características principales:**
- **Enrutamiento dinámico**: Define rutas de manera declarativa dentro de tu aplicación.
- **Navegación sin recarga**: Usa el historial del navegador para cambiar de página sin recargar.
- **Protección de rutas**: Permite restringir el acceso a ciertas páginas según condiciones.
- **Soporte para parámetros**: Puedes pasar datos en la URL y acceder a ellos fácilmente.

**Ejemplo de uso:**
``` js
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Home from "./Home";
import About from "./About";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

*Página web y documentación:* https://reactrouter.com

#### **SWR:**
Sí, **SWR** es una biblioteca de React desarrollada por Vercel para la obtención eficiente de datos. Su nombre proviene de _Stale-While-Revalidate_, una estrategia de invalidación de caché que primero muestra datos almacenados (_stale_), luego realiza una solicitud para actualizar la información (_revalidate_) y finalmente devuelve los datos más recientes.

**¿Por qué usar SWR?**
- **Carga rápida**: Muestra datos almacenados antes de hacer una nueva solicitud.
- **Revalidación automática**: Actualiza los datos en segundo plano sin afectar la experiencia del usuario.
- **Soporte para paginación y mutación**: Permite modificar datos sin necesidad de recargar la página.
- **Optimización del rendimiento**: Reduce el número de solicitudes innecesarias al servidor.

**Ejemplo de uso:**
``` js
import useSWR from 'swr';

const fetcher = (url) => fetch(url).then((res) => res.json());

function Profile() {
  const { data, error } = useSWR('/api/user', fetcher);

  if (error) return <div>Error al cargar los datos</div>;
  if (!data) return <div>Cargando...</div>;

  return <div>Usuario: {data.name}</div>;
}
```


También tenemos una nueva herramienta; la nueva API **useSWRMutation** de SWR está diseñada específicamente para manejar mutaciones de datos, como solicitudes **POST**, **PUT** y **DELETE**, de manera eficiente. A diferencia de `useSWR`, que se usa para obtener datos, `useSWRMutation` permite realizar cambios en el servidor sin afectar el rendimiento de la aplicación.

**Ejemplo de uso:**
``` js
import useSWRMutation from 'swr/mutation';

async function sendRequest(url, { arg }) {
  try {
    const response = await fetch(url, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(arg),
    });

    if (!response.ok) {
      throw new Error('Error en la solicitud');
    }

    return response.json();
  } catch (error) {
    throw new Error(error.message);
  }
}

function App() {
  const { trigger, error, isMutating } = useSWRMutation('/api/user', sendRequest);

  return (
    <div>
      {isMutating && <p>Enviando datos...</p>}
      {error && <p>Error: {error.message}</p>}
      <button onClick={() => trigger({ username: 'johndoe' })}>Actualizar Usuario</button>
    </div>
  );
}
```

**Explicación:**
- `isMutating`: Indica si la mutación está en proceso.
- `error`: Captura cualquier error ocurrido durante la mutación.
- `trigger()`: Ejecuta la mutación y actualiza el estado.

*Página web y documentación:* https://swr.vercel.app
#### **# React Hook Form:**
**React Hook Form** es una biblioteca de formularios para React que optimiza el rendimiento y simplifica la validación. Su enfoque basado en hooks permite manejar formularios de manera eficiente sin necesidad de controladores de estado adicionales.

**Características principales:**
- **Menos re-renderizados**: Minimiza actualizaciones innecesarias en los componentes.
- **Validación integrada**: Compatible con validaciones nativas de HTML y librerías como Yup o Zod.
- **Manejo de errores automático**: Captura errores de validación sin necesidad de lógica extra.
- **Soporte para formularios dinámicos**: Permite agregar y eliminar campos fácilmente.

**Ejemplo de uso:**
``` js
import { useForm } from "react-hook-form";

function MyForm() {
  const { register, handleSubmit, formState: { errors } } = useForm();
  
  const onSubmit = (data) => console.log(data);

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register("name", { required: true })} placeholder="Nombre" />
      {errors.name && <p>Este campo es obligatorio</p>}
      <button type="submit">Enviar</button>
    </form>
  );
}
```

*Página web y documentación:* https://react-hook-form.com

