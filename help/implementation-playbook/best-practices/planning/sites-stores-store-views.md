---
title: Prácticas recomendadas para configurar sitios, tiendas y vistas de tiendas
description: Conozca las prácticas recomendadas para configurar sitios, tiendas y vistas de tiendas para maximizar el rendimiento del sitio.
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%
---
# Práctica recomendada para configurar sitios, tiendas y vistas de tiendas

Para Adobe Commerce en infraestructuras en la nube, las prácticas recomendadas se aplican específicamente al entorno de producción (y posiblemente a la arquitectura de ensayo en Pro, sujeta a restricciones de recursos), que tendría más recursos que los entornos de integración y desarrollo.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Estrategias para mejorar el rendimiento

Si el proyecto requiere muchos sitios, tiendas o vistas de tiendas, puede utilizar las siguientes estrategias para mejorar el rendimiento:

- Reestructurar el catálogo cambiando la lógica a las categorías
- Separe las listas de precios de los datos del catálogo mediante un sistema de gestión de precios (PMS) y un precio externo.
- Uso de un almacenamiento de datos no SQL alternativo como Elasticsearch

## Impactos potenciales en el rendimiento

Los sitios web y las tiendas son multiplicadores de los datos del catálogo, por lo que tener muchos sitios web y tiendas puede afectar negativamente al rendimiento del sitio de las siguientes maneras:

- Las tablas de índice más grandes aumentan el tiempo necesario para completar las operaciones de indización [Índice de precios].
- El tiempo aumentado para recuperar la configuración de la aplicación degrada el tiempo de respuesta de la tienda para las páginas de catálogo no almacenadas en caché.
- Se han producido aumentos significativos en el tiempo necesario para completar las operaciones de guardado en Admin, ya que los datos se guardan por separado para cada sitio web.


## Más información

- [Explicación de sitios web, tiendas y vistas de tiendas](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure-store/best-practices)
- [Configurar varios sitios web o tiendas](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure-store/multiple-sites)
