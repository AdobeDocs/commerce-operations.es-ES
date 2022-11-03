---
title: Prácticas recomendadas de configuración para indexadores
description: Mantener y optimizar el rendimiento del sitio siguiendo las prácticas recomendadas para la configuración del indexador.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# Prácticas recomendadas para la configuración del indexador

Para optimizar y mantener el rendimiento del sitio, revise y actualice la configuración del indexador utilizando las prácticas recomendadas de rendimiento descritas en este artículo.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Establecer indexadores para que se actualicen en una programación

Adobe Commerce tiene dos tipos de modos de indexador: [!UICONTROL Update on Save] (configuración predeterminada) y [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** el modo actualiza los índices inmediatamente cada vez que cambie el catálogo u otros datos. Por ejemplo, si un usuario administrador agrega nuevos productos a una categoría, el índice de productos de la categoría se reindexa inmediatamente cuando se guarda la actualización.

- **[!UICONTROL Update on Schedule]** mode almacena información sobre actualizaciones de datos, y las operaciones de reindexación y las actualizaciones de índice se administran mediante un trabajo cron que se ejecuta en segundo plano a intervalos programados.

Tener un almacén grande con varios administradores trabajando en el backend o tener muchos déclencheur de importación y exportación con actualizaciones de índice frecuentes. Si la configuración del índice del sitio está configurada en [!UICONTROL Update on Save] , la reindexación frecuente degrada el rendimiento de la base de datos, lo que ralentiza el rendimiento del sitio y provoca retrasos prolongados en el proceso de reindexación, especialmente en grandes almacenes.

Para maximizar el rendimiento del sitio, siga estas prácticas recomendadas para la indexación:

- Revise la configuración del índice.
- Configure los indexadores como _[!UICONTROL Update on Schedule]_para sitios grandes, y sitios con actualizaciones frecuentes y tráfico pesado. Consulte [Administración de índices](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- Seguir [prácticas recomendadas de rendimiento](../../../performance/configuration.md) para administrar índices.

## Información adicional

- [Administración de índices para usuarios administradores](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Administración de índices mediante la CLI del Magento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Información general sobre la indexación para desarrolladores](https://developer.adobe.com/commerce/php/development/components/indexing/)
