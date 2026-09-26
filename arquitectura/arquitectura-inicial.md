# Arquitectura inicial del marketplace de productos para mascotas

> Propuesta de diseño en tres capas para el Laboratorio 02.

## Diagrama de arquitectura

```mermaid
flowchart TD

%% ---------------------
%% ACTORES
%% ---------------------
subgraph ACTORES["ACTORES"]
    Cliente["Cliente"]
    Seller["Seller"]
    Admin["Administrador"]
end

%% ---------------------
%% PRESENTACIÓN
%% ---------------------
subgraph PRESENTACION["PRESENTACIÓN"]
    Web["Aplicación Web + API REST"]
end

%% ---------------------
%% LÓGICA DE NEGOCIO
%% ---------------------
subgraph NEGOCIO["LÓGICA DE NEGOCIO"]
    Usuarios["Usuarios"]
    Sellers["Sellers"]
    Catalogo["Catálogo"]
    Carrito["Carrito"]
    Pedidos["Pedidos"]
end

%% ---------------------
%% DATOS
%% ---------------------
subgraph DATOS["DATOS"]
    BD["Base de datos"]
end

%% ---------------------
%% SISTEMAS EXTERNOS
%% ---------------------
subgraph EXTERNOS["SISTEMAS EXTERNOS"]
    Pago["Pasarela de pago"]
    ERP["ERP"]
    Envio["Servicio de envío"]
end

%% ---------------------
%% FLUJO PRINCIPAL
%% ---------------------
ACTORES --> PRESENTACION
PRESENTACION --> NEGOCIO
NEGOCIO --> DATOS

%% Integraciones
DATOS -->|"integraciones"| EXTERNOS

%% ---------------------
%% DISTRIBUCIÓN HORIZONTAL
%% ---------------------
Cliente ~~~ Seller
Seller ~~~ Admin

Usuarios ~~~ Sellers
Sellers ~~~ Catalogo
Catalogo ~~~ Carrito
Carrito ~~~ Pedidos

Pago ~~~ ERP
ERP ~~~ Envio

%% ---------------------
%% ESTILOS
%% ---------------------
style ACTORES fill:#222,stroke:#fff,stroke-width:2px,color:#fff
style PRESENTACION fill:#222,stroke:#fff,stroke-width:2px,color:#fff
style NEGOCIO fill:#222,stroke:#fff,stroke-width:2px,color:#fff
style DATOS fill:#222,stroke:#fff,stroke-width:2px,color:#fff
style EXTERNOS fill:#222,stroke:#fff,stroke-width:2px,color:#fff

style Cliente fill:#222,stroke:#fff,color:#fff
style Seller fill:#222,stroke:#fff,color:#fff
style Admin fill:#222,stroke:#fff,color:#fff

style Web fill:#222,stroke:#fff,color:#fff

style Usuarios fill:#222,stroke:#fff,color:#fff
style Sellers fill:#222,stroke:#fff,color:#fff
style Catalogo fill:#222,stroke:#fff,color:#fff
style Carrito fill:#222,stroke:#fff,color:#fff
style Pedidos fill:#222,stroke:#fff,color:#fff

style BD fill:#222,stroke:#fff,color:#fff
```

### Vista gráfica (Archify)

![Diagrama de arquitectura inicial generado con Archify](./diagrama-arquitectura.png)

[**Abrir el diagrama interactivo original de Archify**](./arquitectura-inicial.html)

## Descripción

- **Presentación:** la aplicación web permite interactuar a Cliente, Seller y Administrador; la API REST recibe las solicitudes.
- **Lógica de negocio:** Usuarios, Sellers, Catálogo, Carrito y Pedidos separan las funciones principales del marketplace.
- **Datos:** la base de datos almacena y permite consultar la información del sistema.
- **Sistemas externos:** Pedidos se integra con la pasarela de pago y el servicio de envío. El ERP puede aportar información de productos y stock al Catálogo.
