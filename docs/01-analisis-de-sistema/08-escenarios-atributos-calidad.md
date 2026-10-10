# Escenarios de atributos de calidad del Marketplace

Los cinco escenarios desarrollan AC01–AC05. **Todas las medidas son propuestas por validar; no son resultados medidos.** Antes del ensayo se aprobarán entorno, datos, carga y pruebas.

## EQ-01 · Rendimiento — AC01

| Parte | Descripción |
|---|---|
| Fuente del estímulo | Cliente que consulta productos. |
| Estímulo | Búsqueda o consulta del detalle de un producto. |
| Artefacto | Catálogo, API, caché y acceso a PostgreSQL. |
| Entorno | Operación normal con datos representativos y 200 usuarios simultáneos. |
| Respuesta | Entregar resultados y detalles sin errores inesperados. |
| Medida de la respuesta | Propuesta: p95 ≤ 2 segundos y errores técnicos < 1 % de solicitudes durante el ensayo. |

## EQ-02 · Disponibilidad — AC02

| Parte | Descripción |
|---|---|
| Fuente del estímulo | Cliente que realiza una operación crítica. |
| Estímulo | Solicitud durante una campaña o una falla de un componente. |
| Artefacto | Web, API y dependencias de la operación. |
| Entorno | Sistema publicado y monitorizado; operaciones críticas y mantenimiento por acordar. |
| Respuesta | Atender las operaciones disponibles y comunicar de forma controlada las fallas. |
| Medida de la respuesta | Propuesta: disponibilidad mensual ≥ 99,5 % para las operaciones críticas, calculada con registros de monitoreo. |

## EQ-03 · Escalabilidad — AC03

| Parte | Descripción |
|---|---|
| Fuente del estímulo | Clientes concurrentes durante una campaña. |
| Estímulo | Incremento progresivo de solicitudes. |
| Artefacto | Backend modular, conexiones, caché y PostgreSQL. |
| Entorno | Ensayo con datos, mezcla de operaciones y configuración documentados. |
| Respuesta | Mantener tiempos y errores dentro de los límites acordados al aumentar la carga. |
| Medida de la respuesta | Propuesta: hasta 200 usuarios simultáneos, p95 ≤ 3 segundos y errores técnicos < 1 %; registrar CPU, memoria y conexiones. |

## EQ-04 · Seguridad — AC04

| Parte | Descripción |
|---|---|
| Fuente del estímulo | Usuario sin sesión o sin el permiso necesario. |
| Estímulo | Intento de consultar datos protegidos o ejecutar una operación no autorizada. |
| Artefacto | Autenticación, autorización y rutas protegidas de la API. |
| Entorno | Matriz de pruebas con cuentas Cliente, Seller y Administrador. |
| Respuesta | Rechazar la operación sin persistir cambios ni revelar información sensible. |
| Medida de la respuesta | Propuesta: rechazar el 100 % de intentos no autorizados incluidos en la matriz y comprobar ausencia de cambios o exposición de datos. |

## EQ-05 · Mantenibilidad — AC05

| Parte | Descripción |
|---|---|
| Fuente del estímulo | Equipo de desarrollo. |
| Estímulo | Cambio de una regla del pedido o del proveedor de pagos. |
| Artefacto | Dominio, casos de uso, contrato de pagos y adaptadores. |
| Entorno | Módulos y pruebas definidos, con reglas de Clean Architecture. |
| Respuesta | Concentrar el cambio en la responsabilidad afectada y conservar los contratos de funciones no relacionadas. |
| Medida de la respuesta | Propuesta: aprobar el 100 % de pruebas del módulo y regresión acordadas; ninguna dependencia de Dominio/Aplicación hacia frameworks o adaptadores concretos. |

**Verificación:** pruebas de carga para EQ-01/EQ-03; registros de monitoreo para EQ-02; matriz de accesos y revisión de datos para EQ-04; pruebas e inspección de imports para EQ-05.
