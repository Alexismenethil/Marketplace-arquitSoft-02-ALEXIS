# Marketplace · Clean Architecture con Angular

Demostración académica: catálogo, carrito y compra con datos en memoria y pago simulado. Los adaptadores externos son ejemplos; no implementa la API propuesta en los diagramas.

```bash
npm ci
npm start
npm run pruebas
npm run build
```

| Capa (`src/app/`) | Responsabilidad |
|---|---|
| `dominio/` | Productos, carrito, pedidos y contratos; sin Angular. |
| `aplicacion/` | Consultar catálogo, agregar al carrito y registrar compra. |
| `infraestructura/` | Repositorios, pagos, notificaciones y tokens de inyección. |
| `presentacion/` | Componentes Angular y estado del carrito. |

Las dependencias apuntan hacia el dominio. `app.config.ts` conecta las implementaciones de los contratos.

Flujo: Carrito → RegistrarCompraCasoUso → contratos de pagos, pedidos y notificaciones.
