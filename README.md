# 🐾 Marketplace de Productos para Mascotas

> Proyecto académico de diseño y análisis de arquitectura de software para una plataforma de comercio electrónico de productos para mascotas, tomando como caso de estudio y referencia funcional a **GoPet**.

---

## 📌 Información del Proyecto

| Campo | Detalle |
| :--- | :--- |
| **Curso** | Arquitectura de Software |
| **Docente** | Ing. Lizbeth Jaico Quispe |
| **Estudiante** | Alexis Huamani Rivera |
| **Caso de Estudio** | GoPet (referencia funcional) |
| **Entregable** | Laboratorio 02 – Análisis del Sistema y Arquitectura Inicial |

---

## 📖 Descripción General

Este proyecto desarrolla la propuesta arquitectónica de un **Marketplace de Productos para Mascotas**, diseñado bajo un enfoque de **tres capas** e integración con servicios externos. La plataforma permite a los dueños de mascotas (clientes) explorar, comparar y comprar productos, a los vendedores (sellers) gestionar sus productos y ventas, y a los administradores gestionar integralmente la plataforma.

---

## 🏛️ Vista de la Arquitectura Inicial

La solución se estructura en tres capas principales complementadas con integraciones hacia servicios externos:

![Diagrama de Arquitectura](./arquitectura/diagrama-arquitectura.png)

* **Capa de Presentación:** Aplicación web para interacción de Cliente, Seller y Administrador, comunicándose mediante una API REST.
* **Capa de Lógica de Negocio:** Componentes modulares para Usuarios, Sellers, Catálogo, Carrito y Pedidos.
* **Capa de Datos:** Base de datos relacional para el almacenamiento persistente de transacciones, catálogo e inventario.
* **Sistemas e Integraciones Externas:** Pasarela de pago, Servicio de envío, Servicio de facturación y ERP para aprovisionamiento de productos y stock.

👉 [Ver detalle de arquitectura inicial y diagrama interactivo](./arquitectura/arquitectura-inicial.md)

---

## 📂 Estructura del Repositorio

```text
├── README.md
├── analisis-de-sistema/
│   ├── 01-actores.md
│   ├── 02-historias-del-usuario.md
│   ├── 03-requisitos-funcionales.md
│   ├── 04-atributos-de-calidad.md
│   ├── 05-restricciones.md
│   └── 06-driver-arquitectonicos.md
└── arquitectura/
    ├── arquitectura-inicial.md
    ├── arquitectura-inicial.html
    └── diagrama-arquitectura.png
```

### Detalle de Documentos

#### 1. Análisis del Sistema (`analisis-de-sistema/`)
- [**01. Actores:**](./analisis-de-sistema/01-actores.md) Identificación de actores directos (Cliente, Seller, Administrador) y sistemas externos (Pasarela de pago, Servicio de envío, Servicio de facturación, ERP).
- [**02. Historias de Usuario:**](./analisis-de-sistema/02-historias-del-usuario.md) Requerimientos expresados desde la perspectiva del usuario final.
- [**03. Requisitos Funcionales:**](./analisis-de-sistema/03-requisitos-funcionales.md) Catálogo de capacidades y reglas de negocio del marketplace.
- [**04. Atributos de Calidad:**](./analisis-de-sistema/04-atributos-de-calidad.md) Escenarios de rendimiento, disponibilidad, escalabilidad, seguridad y modificabilidad.
- [**05. Restricciones:**](./analisis-de-sistema/05-restricciones.md) Restricciones técnicas, de integración y de diseño del sistema.
- [**06. Drivers Arquitectónicos:**](./analisis-de-sistema/06-driver-arquitectonicos.md) Puntos de decisión clave que orientan la arquitectura.

#### 2. Diseño de Arquitectura (`arquitectura/`)
- [**Propuesta de Arquitectura Inicial:**](./arquitectura/arquitectura-inicial.md) Descripción de componentes y capas del sistema.
- [**Diagrama Interactivo (Archify):**](./arquitectura/arquitectura-inicial.html) Modelo interactivo de arquitectura.
- [**Diagrama de Arquitectura:**](./arquitectura/diagrama-arquitectura.png) Imagen representativa del diseño en capas.
