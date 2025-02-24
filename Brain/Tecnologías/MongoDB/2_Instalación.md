En este caso solo voy a hacer un par de aclaraciones ya que la instalación del sistema gestor de la base de datos varía según el sistema operativo con el que trabajemos.
En el caso de utilizar *Windows* será necesario la utilización de tres componentes para trabajar con dicha base de datos:
1. Sistema gestor de Bases de datos (`MongoDB`): 
	- Es el encargado de administrar nuestras bases de datos, nuestras colecciones y documentos; administrar los métodos de autenticación y la concurrencia.
	
	- Para instalarla podemos ir a la página oficial de MongoDB o a este link: [Link MongoDB Community Edition](https://www.mongodb.com/products/self-managed/community-edition) . Al ejecutar el instalador por defecto y en automático nos da la opción de instalar el Cliente gráfico llamado MongoDB Compass.
	
	- Una vez que lo instalamos, debemos agregar al path de variables de entorno del sistema el archivo de ejecución llamado `mongod` que esta en la ruta: `C:\Program Files\MongoDB\Server\ {tu versión de mongo} \bin\mongod.cfg`
	
1. Un cliente para acceder a la base de datos:
	-  En estos casos tenemos dos alternativas, un cliente gráfico o simplemente uno que nos deje operar sobre la base de datos a través de una terminal de comandos. Por lo general recomiendo que instalen ambas, ya que primero es importante aprender a trabajar con la terminal y con los comandos básicos de la base de datos y luego para mayor comodidad implementar un cliente gráfico: 
		1. Cliente por consola (`MongoDB Shell`): [Shell para MongoDB](https://www.mongodb.com/docs/mongodb-shell/)
			1. Una vez descargado descompriman el archivo .zip, renombramos la carpeta como `mongoShell` y la movemos la carpeta dentro de la misma que se creo la base de datos a la altura de Server: `C:\Program Files\MongoDB\`
			2. Cuando finalizamos esto también debemos agregar el archivo de ejecución a las variables de entorno de la misma manera que lo hicimos en pasos anteriores, agregando el archivo `mongosh` al path del sistema que si siguieron los pasos anteriores de la forma correcta debería estar en la siguiente ruta:  `C:\Program Files\MongoDB\mongoShell\bin\mongosh.exe`
		2. Cliente Gráfico (`MongoDB Compass`): [ Compass, The GUI for MongoDB](https://www.mongodb.com/products/tools/compass)
			1. Lo pueden descargar con el mismo instalador que ofrece mongo en un principio o haciendo click en el link de arriba.

SI todo se instaló con éxito, tendríamos que poder ejecutar `mongosh` desde cualquier terminal y acceder a nuestra base de datos.