# Enfoque arquitectónico

| Elemento | Aplicación al Marketplace |
|---|---|
| Enfoque | **Clean Architecture** — ADR-002, DA06. |
| Objetivo | Separar responsabilidades y dirigir dependencias hacia el núcleo. |
| Problema | Evitar reglas de compra acopladas a interfaz, base de datos o pasarela. |
| Capas | Dominio, Aplicación, Presentación e Infraestructura. |
| Beneficios | Pruebas del núcleo y sustitución de adaptadores que cumplen el mismo contrato. |

![Clean Architecture del Marketplace](../../img/ArquitecturalimpiadelMarketplaceWeb.png)

| Capa | Responsabilidad |
|---|---|
| Dominio | Producto, Carrito, Pedido y reglas de precios y stock. |
| Aplicación | Consultar catálogo, agregar productos y registrar compras mediante contratos. |
| Presentación | Pantallas y controladores que invocan casos de uso. |
| Infraestructura | Repositorios y adaptadores de persistencia, pagos y notificaciones. |

**Regla:** Dominio y Aplicación no importan frameworks ni implementaciones externas; la composición conecta contratos y adaptadores.

La API Node.js/Express, PostgreSQL y Redis representan la propuesta del sistema; `tecnologia/boilerplate-clean-arquitecture/` es una demostración Angular con adaptadores en memoria.
