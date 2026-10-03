# Decisiones Arquitectónicas

> Guía 03, paso 3. Propuesta de diseño del marketplace; estas decisiones no significan que el backend esté implementado.

| ID | Decisión arquitectónica | Driver relacionado | Justificación | Resultado |
| :--- | :--- | :--- | :--- | :--- |
| ADR-001 | Monolito modular con posibilidad de escalamiento horizontal | DA01 – Escalabilidad; DA06 – Mantenibilidad | Organizar el negocio en módulos con límites definidos y mantener una sola unidad de despliegue del backend. Ante mayor demanda, replicar el backend completo. | Módulos de Usuarios, Sellers, Catálogo, Carrito y Pedidos dentro de una aplicación. |
| ADR-002 | Clean Architecture | DA06 – Mantenibilidad | Separar las reglas del negocio de la interfaz, la persistencia y los servicios externos, con dependencias de código hacia el núcleo. | Dominio, Aplicación, Presentación e Infraestructura; detalle en el paso 5. |
| ADR-003 | Caché para consultas frecuentes | DA02 – Rendimiento | Reducir lecturas repetitivas del catálogo, definiendo caducidad e invalidación. La disponibilidad y el stock deben validarse nuevamente al comprar. | Caché de consulta y validación de stock contra la fuente de verdad durante la compra. |
| ADR-004 | Integración de pagos mediante contratos y adaptadores | DA04 – Pago externo | Aislar al proveedor de pagos de las reglas del negocio y permitir sustituir su implementación. | Pedidos coordina el pago mediante un contrato y un adaptador de la pasarela externa. |
| ADR-005 | Autenticación y autorización por roles | DA03 – Seguridad | Verificar la identidad y los permisos en el backend antes de ejecutar operaciones protegidas. | Acceso diferenciado para Cliente, Seller y Administrador, con comunicación HTTPS. |
| ADR-006 | Separación de cliente web y backend mediante API REST | DA05 – API REST | Ofrecer un contrato de comunicación definido entre la interfaz y el backend, sin acceso directo del navegador a la base de datos. | Solicitudes HTTPS y respuestas JSON; rutas y controladores como entrada al backend. |

## ADR-001: selección del estilo global

**Estado:** seleccionado para la propuesta académica.

**Contexto:** el marketplace necesita buscar productos, gestionar vendedores, preparar carritos y registrar pedidos. DA06 exige aislar cambios; DA01 exige contemplar incrementos de demanda durante campañas.

**Alternativas consideradas:**

- **Monolito sin límites modulares:** despliegue sencillo, pero facilita el acoplamiento entre responsabilidades.
- **Monolito modular:** despliegue único y responsabilidades separadas mediante contratos entre módulos.
- **Microservicios:** permiten despliegue y escalamiento por servicio, pero añaden comunicación distribuida, coordinación de datos y operación de múltiples servicios. El análisis actual no demuestra esa necesidad.

**Decisión:** seleccionar el monolito modular. Las capas describen la organización de responsabilidades; el monolito describe la unidad de despliegue. Ambas decisiones son compatibles.

**Consecuencias:**

- Las llamadas internas se realizan dentro de la misma aplicación mediante servicios o interfaces; cada módulo protege sus detalles de implementación.
- Todos los módulos se despliegan juntos. El escalamiento horizontal replica la aplicación completa, no cada módulo de forma independiente.
- Para varias instancias se requiere balanceo de carga y evitar estado de sesión exclusivo de una instancia. También se debe revisar la capacidad de PostgreSQL y sus conexiones.
- La modularidad facilita cambios, pero no garantiza por sí sola rendimiento, disponibilidad ni escalabilidad. Estas cualidades necesitan tácticas y validación posterior.

## Coherencia con el gráfico de la guía

Se conservan las cinco columnas del ejemplo de la página 8: **Usuarios, Sellers, Catálogo, Carrito y Pedidos**. En esta vista, pagos y envíos son responsabilidades coordinadas por Pedidos mediante adaptadores; no se dibuja un módulo de Pagos separado. Esto precisa la lista inicial de ADR-001 y conserva el objetivo de ADR-004.

El gráfico del paso 4 representa llamadas en una organización de tres capas. No representa las dependencias de código de Clean Architecture: en el paso 5, el dominio y los casos de uso no deben depender de implementaciones de base de datos ni de proveedores externos.

## Referencias

- Guía 03 de Arquitectura de Software, Ing. Lizbeth Jaico Quispe, semestre 2026-II, páginas 6 a 8.
- [Microsoft: arquitecturas comunes de aplicaciones web](https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/common-web-application-architectures).
- [Robert C. Martin: The Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html).
