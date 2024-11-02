---
title: Prácticas recomendadas de configuración para indexadores
description: Mantenga y optimice el rendimiento del sitio siguiendo las prácticas recomendadas para la configuración del indexador.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Prácticas recomendadas para la configuración del indexador

Para optimizar y mantener el rendimiento del sitio, revise y actualice la configuración del indizador siguiendo las prácticas recomendadas de rendimiento descritas en este artículo.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Configurar indizadores para que se actualicen según una programación

Adobe Commerce tiene dos tipos de modos de indizador: [!UICONTROL Update on Save] y [!DNL Update on Schedule].

- El modo **[!UICONTROL Update on Save]** actualiza los índices inmediatamente cada vez que cambia el catálogo u otros datos. Por ejemplo, si un usuario administrador agrega nuevos productos a una categoría, el índice de productos de la categoría se reindexa inmediatamente cuando se guarda la actualización.

- El modo **[!UICONTROL Update on Schedule]** almacena información sobre actualizaciones de datos, y las operaciones de reindexación y las actualizaciones de índice son administradas por un trabajo cron que se ejecuta en segundo plano a intervalos programados. El trabajo cron no siempre realiza una reindexación cada vez que se ejecuta. Solo vuelve a indexar cuando hay nuevas entradas en los registros de cambios del indexador (por ejemplo, hay un registro de pendientes en los indexadores).

Tener un almacén grande con varios administradores trabajando en el backend o tener muchos déclencheur de importación y exportación con actualizaciones frecuentes de índice. Si la configuración del índice del sitio se establece en modo [!UICONTROL Update on Save], la reindexación frecuente degrada el rendimiento de la base de datos, lo que ralentiza el rendimiento del sitio y provoca largos retrasos en el proceso de reindexación, especialmente en tiendas grandes.

Para maximizar el rendimiento del sitio, siga estas prácticas recomendadas para la indexación:

- Revise la configuración del índice.
- Establezca los indexadores en _[!UICONTROL Update on Schedule]_para sitios grandes y sitios con actualizaciones frecuentes y tráfico intenso. Consulte [Administración de índices](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management#change-the-index-mode).
- Siga [prácticas recomendadas de rendimiento](../../../performance/configuration.md) para administrar índices.

>[!IMPORTANT]
>
>[!DNL Customer Grid] solo se puede reindexar usando la opción [!UICONTROL Update on Save]. Este índice no admite la opción `Update by Schedule`.

## Más información

- [Administración de índices para usuarios administradores](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Administración de índices mediante la CLI de Magento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Información general de indización para desarrolladores](https://developer.adobe.com/commerce/php/development/components/indexing/)
