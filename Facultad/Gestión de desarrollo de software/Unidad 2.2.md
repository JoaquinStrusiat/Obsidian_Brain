## MANTENIMIENTO Y EVOLUCIÓN DEL SOFTWARE

En los estándares de ciclo de vida, el Mantenimiento es un proceso formal con actividades específicas (análisis de cambios, implementación, revisión/aceptación, migración y retiro). No es “lo que ocurre después” sino una fase planificada y con predelivery activities (plan de mantenimiento, requisitos de mantenibilidad) que se diseñan antes de liberar.

### DEFINICIONES NORMATIVAS Y CATEGORÍAS
**Definición (normativa)**: mantenimiento = modificación de un producto existente preservando su integridad, con actividades y productos definidos por el estándar ISO/IEC/IEEE 14764 (última edición 2022) y alineado con 12207. 

**Categorías clásicas (organizan el backlog y los reportes): **
1. *Correctivo* (errores),
2. *Perfectivo* (mejoras)
3. *Adaptativo* (cambios del entorno)
4. *Preventivo* (evitar degradación, por ejemplo: mejoramiento de seguridad, refactorizaciones).

### TÉCNICAS CLAVE PARA LA EVOLUCIÓN DEL SOFTWARE
Cuando hablamos de evolución del software, hay algunas técnicas que ayudan a mantener vivo y saludable el sistema: 
- *Refactorización*: limpiar y reorganizar el código sin cambiar lo que hace. Ejemplo: eliminar duplicaciones o mejorar nombres de variables. Esto hace que el sistema sea más fácil de mantener y extender. • 
- *Reingeniería / Ingeniería inversa*: cuando el código es tan complejo o antiguo que nadie entiende cómo funciona, se hace un trabajo de “descubrir” su estructura, documentarlo y rearmarlo con un diseño más claro. 
- *Migración o retiro de componentes*: a veces, la mejor evolución es mudar el software a una nueva tecnología (ej.: pasar de servidores físicos a la nube) o directamente retirar un módulo que ya no aporta valor.


### MÉTRICAS E INDICADORES
Para saber si un equipo mantiene y evoluciona bien un software, necesitamos medir. Algunas métricas importantes:
- **DORA Metrics (muy usadas en la industria):**
	- Tiempo de entrega de un cambio (Lead Time). 
	-  Frecuencia de despliegues (qué tan seguido liberamos nuevas versiones). 
	-  Tasa de fallas por cambio (cuántos despliegues rompen algo). 
	-  Tiempo de recuperación (qué tan rápido arreglamos un problema).
- **Métricas de mantenimiento (SWEBOK):**
	- Esfuerzo invertido por categoría (¿cuánto tiempo gastamos en correctivo, adaptativo, preventivo?). 
	-  Retrabajo (cuántas veces tenemos que arreglar lo mismo). 
	-  Facilidad de prueba y modificabilidad (qué tan fácil es hacer un cambio sin romper otra cosa).


## Tarea de Mapa de backlog por categorías


| **Ticket** | **Descripción**                                                | **Categoría**           | **Impacto** | **Urgente** | **Riesgo si no se atiende**                                     | **Origen del Tiket**    |
| ---------- | -------------------------------------------------------------- | ----------------------- | ----------- | ----------- | --------------------------------------------------------------- | ----------------------- |
| 5          | Refactorización del módulo de facturación con código duplicado | Perfectiva              | Medio       | Bajo        | Complejidad a la hora de escalar el proyecto                    | Equipo técnico          |
| 6          | Optimizar consultas SQL lentas                                 | Perfectivo -Correctivas | Medio       | Medio       | Puede volver el sistema cada vez más lento y volverlo poco útil | Equipo técnico -Usuario |
| 9          | Vulnerabilidad en librería de autenticación                    | Preventido              | Bajo        | Alta        | Acceso indebido a información de carácter privado               | Equipo técnico          |
