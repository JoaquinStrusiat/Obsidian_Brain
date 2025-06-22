# Unidad 3: Datos Semiestructurados

### 1. Datos Semiestructurados: Conceptos Clave
- 1.1 **Definición y Características  **
	- Qué son: Datos que no siguen un esquema rígido (como las tablas SQL) pero usan etiquetas/marcas para organizar la información. 
	- Ventajas: 
		- Flexibilidad para representar jerarquías complejas. 
		- Independencia de plataformas (legibilidad humana/máquina). 
	- Casos de uso: •
		- Intercambio de datos entre sistemas heterogéneos (APIs, feeds).
		- Archivos de configuración (AndroidManifest.xml, package.json).

- 1.2 **Comparación con Otros Formatos**

|       Tipo       |   Ejemplo   | Rigidez |         Uso típico         |
| :--------------: | :---------: | :-----: | :------------------------: |
|   Estructurado   |  Tabla SQL  |  Alta   | Base de Datos relacionales |
| Semiestructurado |  XML, JSON  |  Media  |     Web services, Apis     |
| No estructurado  | Texto plano |  Nula   |    Documentos digitales    |

### 2. SGML: El Lenguaje Padre
- 2.1 **Historia y Evolución **
	- *Origen*: Estándar ISO (1986) para documentos electrónicos. 
	- *Derivados*: HTML (para web) y XML (para datos).
- 2.2 **DTD (Document Type Definition)**
	- *Definición:* significa Document Type Definition (Definición de Tipo de Documento). Es un archivo o sección que define la estructura de un documento SGML (o XML). Es decir, qué etiquetas se pueden usar, en qué orden y con qué contenido.
	- *Función:* Para validar que un documento está bien estructurado.
	- *Tipos de declaraciones:*
```
<!ELEMENT>: Define elementos y su contenido.
<!ATTLIST>: Define atributos de elementos.
```
- **Ejemplo:**
``` xml
<!ELEMENT articulo (titulo, autor, fecha, contenido)>
<!ELEMENT titulo (#PCDATA)>
<!ELEMENT autor (#PCDATA)>
<!ELEMENT fecha (#PCDATA)>
<!ELEMENT contenido (#PCDATA)>
```

- 2.3 **SGML**
	- **SGML (Standard Generalized Markup Language)** es un **lenguaje estándar para definir lenguajes de marcado**. Es un metalinguaje, es decir, un lenguaje que sirve para crear otros lenguajes de marcado, como **HTML** y **XML**.
	- Fue creado en los años 80 y es muy flexible, pero también complejo.
	- Se usa para describir la estructura y contenido de documentos.
	- XML es una simplificación de SGML.
``` sgml
<!DOCTYPE articulo SYSTEM "articulo.dtd">
<articulo>
   <titulo>El futuro de los lenguajes de marcado</titulo>
   <autor>Federico Aranda</autor>
   <fecha>2025-06-22</fecha>
   <contenido>
      SGML es el estándar base para lenguajes como HTML y XML. Aunque ya no es comúnmente usado,
      su influencia sigue vigente en la forma en que estructuramos la información.
   </contenido>
</articulo>

```

- 2.4 **Diferencia clave**
	- **SGML** es el lenguaje de meta-marcado.
	- **DTD** es una forma de definir la **estructura** de un documento (ya sea XML o SGML).


### 3. XML: El Estándar Moderno

- 3.1 Diferencias Clave con SGML
	- XML es una **versión simplificada y más estricta de SGML**.
	- Más fácil de aprender y usar.
	- Fue diseñado para la **web y aplicaciones modernas**.
	- No permite tantas personalizaciones como SGML, lo que lo hace más predecible y compatible.

- 3.2 Sintaxis XML
	- Los documentos XML deben estar **bien formados** (bien cerrados, anidados correctamente).
	- Es sensible a mayúsculas y minúsculas.
	- Ejemplo:
  ```xml
  <persona>
    <nombre>Ana</nombre>
    <edad>28</edad>
  </persona>
```

- 3.3 Validación de XML
	- Un XML puede validarse contra una estructura predefinida:
	    - **DTD** (Document Type Definition)
	    - **XSD** (XML Schema Definition)
	- La validación asegura que el contenido y estructura del XML cumplen ciertas reglas.

### Comparación Detallada SGML vs. XML  
- ¿Por qué XML reemplazó a SGML?  
- Ejemplo de Validación con DTD  
- Conclusión

### Características Clave de JSON en MySQL
- 1. Tipo de dato JSON  
- 2. Validación Automática  
- 3. Funciones para Manipular JSON  

### Ventajas vs. XML en MySQL  
- Ejemplo Completo: Tabla con JSON  
- ¿Cuándo usar JSON en MySQL?  
- Limitaciones  
- Conclusión

### Comparativa: XML vs JSON
- Tabla Comparativa Ampliada  
- Casos de Uso Específicos  
- Flujo de Trabajo Híbrido (XML + JSON)

### Parsing: Concepto y Aplicación en JSON y SGML
- ¿Qué es Parsing?

#### Parsing en JSON
- 1. Librerías Comunes  
- 2. Ejemplo en Python  
- 3. Proceso Interno

#### Parsing en SGML
- 1. Herramientas  
- 2. Ejemplo con BeautifulSoup (Python)  
- 3. Proceso Interno

- Diferencias Clave  
- Ejercicio Práctico  

### Ejemplo de Parsing, Lectura y Escritura de Archivos JSON en PHP

#### Estructura de archivos
- 1. Archivo JSON de ejemplo (usuarios.json)  
- 2. Código PHP completo (procesar_json.php)  
- Explicación paso a paso  
  - Parsing (`json_decode`)  
  - Escritura (`json_encode`)  
  - Lectura/Escritura de archivos  
  - Posibles mejoras  
  - Salida esperada  

### Trabajando con JSON en MySQL y PHP
- Configuración inicial  
  - 1. Crear tabla con campo JSON  
  - 2. Insertar datos JSON  
- Conexión PHP con MySQL para trabajar con JSON  
  - 1. Establecer conexión  
  - 2. Insertar datos JSON en MySQL desde PHP  
  - 3. Consultar y extraer datos JSON  
  - 4. Consultas avanzadas con funciones JSON de MySQL  
- Funciones útiles de MySQL para JSON  
- Buenas prácticas  
- Ejemplo completo: API REST con PHP y MySQL JSON

