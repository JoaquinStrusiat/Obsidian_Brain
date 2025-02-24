### Instalar Node Version Manager (nvm)
**Node Version Manager (nvm)** es una herramienta que permite instalar y gestionar múltiples versiones de Node.js en tu máquina. Esto es especialmente útil si trabajas en varios proyectos que requieren diferentes versiones de Node.js. Aquí tienes un resumen y los pasos para instalarlo:

#### Resumen de nvm:
- **Propósito:** Administrar múltiples versiones de Node.js.
- **Beneficios:**
    - Cambiar entre versiones de Node.js fácilmente.
    - Mantener diferentes versiones para diferentes proyectos.
    - Probar tu código en varias versiones de Node.js.

#### Pasos para instalar nvm en Windows:

**1) Descargar e instalar nvm-windows:**
- Ve al [repositorio de nvm-windows](https://github.com/coreybutler/nvm-windows) y descarga el archivo `nvm-setup.zip`.
- Ejecuta el instalador y sigue las instrucciones para completar la instalación.

**2) Instalar una versión específica de Node.js:**
- Tenemos varias formas de instalar versiones de node:
	- Abre una ventana de comandos (CMD) y ejecuta `nvm install <version>`.
		- Podemos directamente especificar la `versión` exacta que deseamos instalar como en el ejemplo de abajo, o podemos utilizar el comando `latest` para instalar la versión más reciente de node o `lts` para instalar la ultima versión estable de node.
``` sh
nvm install 22.0.0
```

**3) Usar una versión específica de Node.js:**
- Para cambiar a una versión específica de Node.js ejecutamos `nvm use <version | latest | lts>`.
	- Nuevamente podemos especificar la versión exacta o utilizar los comandos específicos de `latest` o `lts`.
``` sh
nvm use 22.0.0
```

**4) Listar versiones instaladas:**
- Para ver las versiones de Node.js que tienes instaladas ejecutamos:
``` sh
nvm ls
```