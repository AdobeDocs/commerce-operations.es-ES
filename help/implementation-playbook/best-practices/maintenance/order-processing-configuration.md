---
title: Prácticas recomendadas de configuración para el procesamiento de pedidos
description: Conozca las prácticas recomendadas de configuración para mejorar el rendimiento del cierre de compra y del procesamiento de pedidos.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: fb30b18c9b9f6a9f538189eeafda9ee7a29d436c
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Prácticas recomendadas de configuración para el procesamiento de pedidos

A medida que aumenta el volumen de pedidos en sus sitios de comercio, puede optimizar el rendimiento de cierre de compra y el procesamiento de pedidos habilitando las siguientes opciones de configuración de almacén:

- **[!UICONTROL Asynchronous indexing]**: habilite esta opción para evitar bloqueos de base de datos y un procesamiento lento que se pueden producir cuando se realizan grandes cantidades de pedidos simultáneamente.
- **[!UICONTROL Asynchronous email notifications]**: habilite esta opción para acelerar el rendimiento del cierre de compra enviando notificaciones de cierre de compra y procesamiento de solicitudes por correo electrónico a intervalos designados en lugar de enviarlas inmediatamente.
- **[!UICONTROL Enable Archiving]**: habilite esta opción para mejorar el rendimiento de pedidos, facturas, envíos y notas de crédito, y mantenga su espacio de trabajo libre de información innecesaria para que pueda centrarse en el negocio actual. Consulte [Habilitar archivado](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving).

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Habilitar el procesamiento asincrónico de pedidos

Los pasos para habilitar el procesamiento asincrónico de solicitudes dependen del modo de implementación:

- Para Adobe Commerce en infraestructura en la nube y sitios locales en modo Producción, utilice el siguiente comando CLI del Magento para habilitar la indexación asíncrona:

   ```php
   php bin/magento config:set dev/grid/async_indexing 1
   ```

- Para los sitios locales de Adobe Commerce en modo Predeterminado o Producción, habilite la indexación asincrónica actualizando la configuración de Configuración de cuadrícula en el Administrador.

   Consulte [Habilitar actualizaciones de cuadrícula programadas y reindexación](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

   >[!WARNING]
   >
   >Antes de actualizar el entorno de producción, pruebe siempre los cambios de configuración en el entorno de ensayo.

## Información adicional

- [Prácticas recomendadas de configuración](../../../performance/configuration.md)
- [Referencia de rutas de configuración generales y avanzadas](../../../configuration/reference/config-reference-general.md)
- [Procesamiento de pedidos de alto rendimiento](../../../performance/high-throughput-order-processing.md)
