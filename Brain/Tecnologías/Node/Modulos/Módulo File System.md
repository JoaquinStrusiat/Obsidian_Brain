## **File System**
El módulo `fs` de Node.js proporciona una amplia variedad de métodos para interactuar con el sistema de archivos. Aquí tienes algunos de los métodos más comunes además de los que ya hemos visto:

###### Métodos de Lectura
- `fs.readFile(path, options)`: Lee el contenido de un archivo.
- `fs.readdir(path, options)`: Lee el contenido de un directorio.

###### Métodos de Escritura
- `fs.writeFile(file, data, options)`: Escribe datos en un archivo, reemplazando el archivo si ya existe.
- `fs.appendFile(file, data, options)`: Añade datos al final de un archivo.

###### Métodos de Manipulación de Archivos
- `fs.rename(oldPath, newPath)`: Cambia el nombre o mueve un archivo.
- `fs.unlink(path)`: Elimina un archivo.

###### Métodos de Manipulación de Directorios
- `fs.mkdir(path, options)`: Crea un nuevo directorio.
- `fs.rmdir(path)`: Elimina un directorio vacío.

###### Métodos de Información
- `fs.stat(path)`: Devuelve información sobre el archivo o directorio especificado.
	- **stats.isFile()**: Devuelve `true` si el objeto es un archivo.
	- **stats.isDirectory()**: Devuelve `true` si el objeto es un directorio.
	- **stats.size**: Tamaño del archivo en bytes.
	- **stats.atime**: Fecha de último acceso.
	- **stats.mtime**: Fecha de última modificación.
	- **stats.ctime**: Fecha de cambio del estado del archivo.
	- **stats.birthtime**: Fecha de creación del archivo.
- `fs.lstat(path)`: Similar a `fs.stat`, pero no sigue enlaces simbólicos.

###### Métodos de Enlaces Simbólicos y Duros
- `fs.symlink(target, path)`: Crea un enlace simbólico.
- `fs.link(existingPath, newPath)`: Crea un enlace duro.

###### Otros Métodos
- `fs.copyFile(src, dest)`: Copia un archivo de una ruta a otra.
- `fs.access(path, mode)`: Comprueba los permisos de un archivo o directorio.
- `fs.readlink(path)`: Lee el valor de un enlace simbólico.
- `fs.realpath(path)`: Devuelve la ruta absoluta de un archivo o directorio.

### *File System para Archivos*
#modulo #file_system #archivos
El módulo de file system `'fs'` te permite trabajar con archivos del sistema de tu computadora o servidor.
Para incluir este modulo, debemos usar el método `require()`:
``` js
const fs = require('fs');
```

Los usos más comunes para leer y modificar archivos con el módulo File System:
- Read files
- Create files
- Update files
- Delete files
- Rename files

#### Read files:
- El módulo File System nos provee de un método para *leer* archivos:
	- `fs.readFile()`: lee archivos en tu computadora.
``` js
const fs = require('fs').promises;

async function leerArchivo(ruta) {
  try {
    const datos = await fs.readFile(ruta, 'utf8');
    console.log(datos);
  } catch (error) {
    console.error('Error al leer el archivo:', error);
  }
}

leerArchivo('archivo.txt');
```

#### Create files:
- El módulo File System tiene un par de métodos para *crear* nuevos archivos:
	- `fs.appendFile()`: agrega contenido especificado a un archivo. Si el archivo no existe, se creará el archivo.
	- `fs.open()`: El método toma un "flag" como segundo argumento; si el flag es "w" para "escritura", el archivo especificado se abre para escribir. Si el archivo no existe, se crea un archivo vacío.
	- `fs.writeFile()`:  reemplaza el archivo y el contenido especificados si existen. Si el archivo no existe, se creará un nuevo archivo que contendrá el contenido especificado.
``` js
const fs = require('fs').promises;

async function crearArchivo(ruta, contenido) {
  try {
    await fs.writeFile(ruta, contenido, 'utf8');
    console.log('Archivo creado');
  } catch (error) {
    console.error('Error al crear el archivo:', error);
  }
}

crearArchivo('nuevoArchivo.txt', 'Este es el contenido del nuevo archivo');
```

#### Update files:
- Para *actualizar* un archivo tenemos dos opciones:
	- -`fs.appendFile()`: agrega el contenido especificado al final del archivo.
	- `fs.writeFile()`: reemplaza el archivo especificado.
``` js
const fs = require('fs').promises;

async function actualizarArchivo(ruta, contenido) {
  try {
    await fs.appendFile(ruta, contenido, 'utf8');
    console.log('Archivo actualizado');
  } catch (error) {
    console.error('Error al actualizar el archivo:', error);
  }
}

actualizarArchivo('archivo.txt', '\nEste es el contenido agregado');
```

#### Delete files:
- Para *eliminar* un archivo se utiliza el siguiente método:
	- `fs.unlink()`: nos permite eliminar el archivo especificado.
``` js
const fs = require('fs').promises;

async function eliminarArchivo(ruta) {
  try {
    await fs.unlink(ruta);
    console.log('Archivo eliminado');
  } catch (error) {
    console.error('Error al eliminar el archivo:', error);
  }
}

eliminarArchivo('archivo.txt');
```

#### Rename files:
- Para *renombrar* un archivo se utiliza el siguiente método:
	- `fs.rename()`: método para renombrar el archivo especificado.
``` js
const fs = require('fs').promises;

async function renombrarArchivo(rutaAntigua, rutaNueva) {
  try {
    await fs.rename(rutaAntigua, rutaNueva);
    console.log('Archivo renombrado');
  } catch (error) {
    console.error('Error al renombrar el archivo:', error);
  }
}

renombrarArchivo('archivo.txt', 'archivoRenombrado.txt');
```

### *File System con Directorios*
#modulo #file_system #carpetas #directorios

Con el módulo de File System también podemos trabajar con carpetas o directorios de nuestro sistema:

Los usos más comunes para leer y modificar directorios con el módulo File System:
- Read files
- Create files
- Update files
- Delete files
- Rename files

#### Read folder:
- Para *leer* directorios utilizamos el siguiente método:
	- `fs.readdir()`: lee el contenido del directorio especificado.
``` js
const fs = require('fs').promises;

async function leerCarpeta(ruta) {
  try {
    const archivos = await fs.readdir(ruta);
    console.log('Contenido de la carpeta:', archivos);
  } catch (error) {
    console.error('Error al leer la carpeta:', error);
  }
}

leerCarpeta('nuevaCarpeta');
```

#### Create folder:
- Para *crear* directorios utilizamos el siguiente método:
	- `fs.mkdir()`: crea un directorio en la ruta especificada.
``` js
const fs = require('fs').promises;

async function crearCarpeta(ruta) {
  try {
    await fs.mkdir(ruta);
    console.log('Carpeta creada');
  } catch (error) {
    console.error('Error al crear la carpeta:', error);
  }
}

crearCarpeta('nuevaCarpeta');
```

#### Delete folder:
- - Para *eliminar* directorios utilizamos el siguiente método:
	- `fs.rmdir()`: elimina el directorio de la ruta especificado.
``` js
const fs = require('fs').promises;

async function eliminarCarpeta(ruta) {
  try {
    await fs.rmdir(ruta);
    console.log('Carpeta eliminada');
  } catch (error) {
    console.error('Error al eliminar la carpeta:', error);
  }
}

eliminarCarpeta('carpetaRenombrada');

```

#### Rename folder:
- Para *renombrar* un directorio se utiliza el siguiente método:
	- `fs.rename()`: método para renombrar un directorio en la ruta especificado.
``` js
const fs = require('fs').promises;

async function renombrarCarpeta(rutaAntigua, rutaNueva) {
  try {
    await fs.rename(rutaAntigua, rutaNueva);
    console.log('Carpeta renombrada');
  } catch (error) {
    console.error('Error al renombrar la carpeta:', error);
  }
}

renombrarCarpeta('nuevaCarpeta', 'carpetaRenombrada');
```