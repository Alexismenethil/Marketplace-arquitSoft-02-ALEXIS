# Decisiones arquitectónicas

Propuesta del marketplace; estas decisiones no acreditan un backend implementado.

| ID | Decisión arquitectónica | Driver relacionado | Justificación | Resultado |
|---|---|---|---|---|
| ADR-001 | Monolito modular | DA01 – Escalabilidad; DA06 – Mantenibilidad | Mantener un despliegue único con responsabilidades separadas; replicarlo cuando la carga medida lo justifique. | Usuarios, Sellers, Catálogo, Carrito, Pedidos, Pagos, Envíos y Notificaciones dentro de una API. |
| ADR-002 | Clean Architecture | DA06 – Mantenibilidad | Separar reglas y casos de uso de frameworks, persistencia y proveedores. | Dominio, Aplicación, Presentación e Infraestructura; dependencias hacia el núcleo. |
| ADR-003 | Caché de consultas frecuentes | DA02 – Rendimiento | Reducir lecturas repetidas del catálogo con caducidad e invalidación. | Redis como caché propuesta; precios y stock se validan contra PostgreSQL al comprar. |
| ADR-004 | Contratos y adaptadores para pagos | DA04 – Pago externo | Sustituir la pasarela sin modificar las reglas del pedido. | Contrato de pagos y adaptador del proveedor. |
| ADR-005 | Autenticación y autorización por roles | DA03 – Seguridad | Comprobar identidad y permisos antes de ejecutar operaciones protegidas. | Roles Cliente, Seller y Administrador; comunicación HTTPS. |
| ADR-006 | Separación web/API mediante REST | DA05 – API REST | Definir la comunicación sin acceso directo del navegador a la base de datos. | API Node.js/Express con solicitudes HTTPS y respuestas JSON. |

**Alternativa descartada:** microservicios, porque el alcance no demuestra una necesidad de despliegues independientes. El monolito escala como aplicación completa; la modularidad no garantiza por sí sola rendimiento o disponibilidad.

[Estilo arquitectónico](../02-arquitectura-software/estilo-arquitectonico.md) · [Enfoque Clean Architecture](../02-arquitectura-software/enfoque-aquitectonico.md).
