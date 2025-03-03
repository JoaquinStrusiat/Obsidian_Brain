## ¿Qué es REST?
REST (**Representational State Transfer**) es un estilo de arquitectura para diseñar APIs que interactúan con recursos en la web.

### **Principios de REST**
1. **Stateless (Sin estado)**: Cada solicitud es independiente; el servidor no almacena información de sesiones.
2. **Recursos**: Todo se trata como un recurso identificado por una URL (Ejemplo: `/productos`, `/usuarios`).
3. **Representaciones**: Los datos se pueden representar en diferentes formatos (JSON, XML, etc.).
4. **Operaciones HTTP estándar**: Se usan métodos HTTP (`GET`, `POST`, etc.) para realizar acciones en los recursos.

Ejemplo de un **endpoint REST**:
``` sh
GET https://api.ejemplo.com/productos
```

### **Diferencias entre REST, SOAP y GraphQL**

|Característica|REST|SOAP|GraphQL|
|---|---|---|---|
|**Formato de datos**|JSON, XML|XML|JSON|
|**Complejidad**|Simple|Complejo|Medio|
|**Flexibilidad**|Alta|Baja|Muy Alta|
|**Estado**|Stateless|Stateful|Stateless|
|**Eficiencia**|Alta|Baja|Alta|

- **SOAP** (Simple Object Access Protocol): Protocolo más rígido, usado en servicios empresariales.
- **GraphQL**: Alternativa moderna que permite consultas más flexibles.
