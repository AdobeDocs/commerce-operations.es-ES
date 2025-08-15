---
title: Prácticas recomendadas de configuración para el procesamiento de pedidos
description: Conozca las prácticas recomendadas de configuración para mejorar el rendimiento de cierre de compra y procesamiento de pedidos.
role: Admin, User
feature: Best Practices
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Prácticas recomendadas de configuración para el procesamiento de pedidos

A medida que aumenta el volumen de pedidos en los sitios de Commerce, puede optimizar el rendimiento de cierre de compra y el procesamiento de pedidos si habilita las siguientes opciones de configuración de tienda:

- **[!UICONTROL Asynchronous indexing]**: habilite esta opción para evitar bloqueos de base de datos y procesos lentos que pueden producirse cuando se realizan simultáneamente grandes cantidades de pedidos.
- **[!UICONTROL Asynchronous email notifications]**: habilite esta opción para acelerar el rendimiento del cierre de compra enviando notificaciones de cierre de compra y procesamiento de pedidos por correo electrónico a intervalos designados en lugar de enviarlas inmediatamente.
- **[!UICONTROL Enable Archiving]**: habilita esta opción para mejorar el rendimiento de pedidos, facturas, envíos y notas de crédito, y para mantener el espacio de trabajo libre de información innecesaria, de modo que pueda centrarse en el negocio actual. Consulte [Habilitar archivado](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Habilitar procesamiento asincrónico de pedidos

Los pasos para habilitar el procesamiento asincrónico de pedidos dependen del modo de implementación:

- Para Adobe Commerce en infraestructura en la nube y sitios locales en modo de producción, utilice el siguiente comando CLI de Magento para habilitar la indexación asíncrona:

  ```php
  php bin/magento config:set dev/grid/async_indexing 1
  ```

- Para los sitios locales de Adobe Commerce en modo predeterminado o de producción, habilite la indexación asíncrona actualizando la configuración de la cuadrícula en el Administrador.

  Ver [Habilitar las actualizaciones programadas de la cuadrícula y la reindexación](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

  >[!WARNING]
  >
  >Pruebe siempre los cambios de configuración en el entorno de ensayo antes de actualizar el entorno de producción.

## Más información

- [Prácticas recomendadas de configuración](../../../performance/configuration.md)
- [Referencia de rutas de configuración generales y avanzadas](../../../configuration/reference/config-reference-general.md)
- [Procesamiento de pedidos de alto rendimiento](../../../performance/high-throughput-order-processing.md)
