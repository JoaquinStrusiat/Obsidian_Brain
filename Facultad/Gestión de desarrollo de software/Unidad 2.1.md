## Ingeniería de requerimientos y propuestas de proyectos

#### Ingeniería de requerimientos
Permite comprender y documentar con lo que los usuarios necesitan del sistema. Siendo la base para todo proyecto, evitando malentendidos, errores costosos y desviaciones durante el desarrollo.
#### Requerimientos funcionales y no funcionales
**Funcionales**: 
- Son aquellos que **describen lo que el sistema debe hacer**, es decir, las funciones, servicios y procesos que debe soportar.  
- Se enfocan en el **comportamiento observable** del sistema.

- *Ejemplos:
	- El sistema debe permitir el registro de usuarios.
	- El usuario podrá autenticarse con email y contraseña.
	- El sistema debe enviar un correo de confirmación al crear una cuenta.
	- El sistema debe permitir generar un informe en PDF de las ventas diarias.
En resumen: **acciones, operaciones, casos de uso**.

**No funcionales:**
- Son las **condiciones o restricciones** sobre cómo deben implementarse los requerimientos funcionales.  
- Se relacionan con **atributos de calidad**, como rendimiento, seguridad, usabilidad, escalabilidad, etc.

- *Ejemplos:*
	- - El sistema debe poder atender al menos 1.000 usuarios concurrentes. (**rendimiento/escalabilidad**)
	- El tiempo de respuesta no debe superar los 2 segundos en el 95% de las consultas. (**eficiencia**)
	- La interfaz debe ser intuitiva y accesible para usuarios con discapacidad visual. (**usabilidad/accesibilidad**)
	- Toda comunicación debe estar cifrada mediante HTTPS. (**seguridad**)
En resumen: **restricciones de calidad, estándares o limitaciones**.

###### **Analogía simple:**
- **Funcional:** El auto debe arrancar al girar la llave.
- **No funcional:** El auto debe arrancar en menos de 2 segundos, incluso con temperaturas bajo cero.

#### Técnicas de Recolección de Requerimientos:
La **recolección de requerimientos** es una etapa clave en el desarrollo de software o sistemas: se trata de obtener la información necesaria para comprender qué necesita realmente el usuario/cliente.  
Existen diversas técnicas, que se pueden combinar según el contexto del proyecto.

- **Entrevistas:**
	- Consisten en **reunirse directamente con los interesados (stakeholders)** para hacer preguntas y recopilar información sobre sus necesidades, expectativas y problemas.
		- **Ventajas:** permiten profundizar, aclarar dudas y obtener información detallada.
		- **Desventajas:** pueden consumir mucho tiempo y depender de la disponibilidad del entrevistado.
		- **Ejemplo:** entrevistar al gerente de ventas para entender cómo genera reportes actualmente y qué espera del nuevo sistema.
- **Encuestas:**
	- Se elaboran **preguntas estructuradas** (cerradas o abiertas) y se distribuyen a un grupo amplio de usuarios o clientes.
		- **Ventajas:** recopilan información de muchas personas en poco tiempo.
	    - **Desventajas:** limitan la posibilidad de aclarar respuestas y dependen de la disposición de los encuestados.
		- **Ejemplo:** enviar un formulario online a todos los empleados para conocer los problemas más comunes con el sistema actual.
- **Prototipos:**
	- Se crean **versiones preliminares** del sistema (bocetos, wireframes, maquetas o prototipos funcionales) para que los usuarios interactúen y den retroalimentación.
		- **Ventajas:** ayudan a los usuarios a visualizar el producto, reducen malentendidos.
		- **Desventajas:** pueden generar expectativas de que el prototipo ya es el producto final.
		- **Ejemplo:** diseñar un prototipo de la interfaz de usuario en Figma para que los usuarios validen el flujo de navegación.
- **Otras técnicas incluyen: **
	- Taller de grupo focal (focus group).
	- Observación del trabajo actual
	- Análisis de documentos. 

#### Validación y Verificación de Requerimientos:
Una vez recolectados y documentados, los requerimientos deben validarse y verificarse para asegurar que sean correctos, completos y realizables.

#### Propuesta de Proyecto:
Es un documento inicial que presenta una visión general del proyecto, explica su propósito, objetivos, alcance e identifica a los involucrados
- **Descripción del Proyecto:**
	- Que problema resuelve este proyecto?
	- Como contribuye al objetivo del negocio?
-  **Objetivos del Proyecto (SMART)**: La técnica **SMART** se usa para definir objetivos claros, alcanzables y medibles en un proyecto.
	- **(S) Specific – Específico**: 
		- El objetivo debe ser **concreto y detallado**, sin ambigüedades.  
		- Responde: **¿Qué se quiere lograr?**
		- **Ejemplo:** “Desarrollar un sistema web para gestionar turnos médicos en clínicas privadas.”
	- **(M) Measurable – Medible:**
		- El objetivo debe poder **cuantificarse o verificarse**, de manera que se pueda evaluar el progreso.  
		- Responde: **¿Cómo sé que se cumplió?**
		- **Ejemplo:** “El sistema debe permitir registrar al menos 500 turnos diarios y generar reportes mensuales automáticamente.”
	- **(A) Achievable – Alcanzable:**
		- El objetivo debe ser **realista**, considerando recursos, tiempo y capacidades del equipo.  
		- Responde: **¿Es posible lograrlo con lo que tenemos?**
		- **Ejemplo:** “Implementar la primera versión del sistema en un plazo de 4 meses utilizando el equipo actual de 5 desarrolladores.”
	- **(R) Relevant – Relevante:**
		- El objetivo debe estar **alineado con la estrategia y necesidades reales** del proyecto o negocio.  
		- Responde: **¿Por qué es importante?**
		- **Ejemplo:** “El sistema debe mejorar la eficiencia en la atención al cliente, reduciendo un 30% las demoras en la asignación de turnos.”
	- **(T) Time-bound – Temporal:**
		- El objetivo debe tener un **plazo definido** para cumplirse, evitando que quede abierto indefinidamente.  
		 - Responde: **¿Cuándo se debe lograr?**
		- **Ejemplo:** “El sistema debe estar en funcionamiento para diciembre de 2025.”

#### Inclusiones y Exclusiones:
Se detalla en forma explícita lo que estará incluidas e la entrega y lo que no.
- Se cubre (inclusiones).
- No se cubrirán (exclusiones).

#### Registro de Interesados (Stakeholders)
Identificar a todas las partes interesadas en el proyecto.


