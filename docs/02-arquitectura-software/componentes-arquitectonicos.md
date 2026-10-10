# Componentes arquitectónicos

![Componentes del Marketplace](../../img/componentes.png)

| Componente | Responsabilidad | Origen |
|---|---|---|
| Usuarios | Identidad, sesión y permisos. | AC04, DA03. |
| Sellers | Alta, actualización y desactivación de vendedores. | RF07, HU05. |
| Catálogo | Búsqueda, detalle, disponibilidad y gestión de productos y stock. | RF01–RF03, HU01–HU02. |
| Carrito | Agregar, modificar y quitar productos; calcular totales. | RF04, HU03. |
| Pedidos | Registrar, consultar y coordinar la compra; sincronizar pedidos con el ERP. | RF05–RF06, RF08, HU04/HU06; ERP. |
| Pagos | Procesar el pago mediante contrato y adaptador de pasarela. | RC04, DA04, HU04. |
| Envíos | Coordinar información de entrega con el proveedor externo. | RC05. |
| Notificaciones | Comunicar confirmación y cambios del pedido. | HU06; mecanismo propuesto. |

Los componentes pertenecen al mismo backend; Pagos, Envíos y Notificaciones colaboran con Pedidos mediante contratos. PostgreSQL conserva la información autoritativa y Redis solo consultas cacheadas.
