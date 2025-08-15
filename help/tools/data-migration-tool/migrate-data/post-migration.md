---
title: Pasos de la migración posterior a los datos
description: Descubra los pasos que debe seguir después de usar  [!DNL Data Migration Tool] para migrar datos de Magento 1 a Magento 2.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# Pasos de la migración posterior a los datos

Después de completar la migración y de probar a fondo el nuevo sitio de Magento 2, realice las siguientes tareas:

* Ponga Magento 1 en modo de mantenimiento y detenga permanentemente todas las actividades de administración

* Iniciar trabajos cron de Magento 2

* [Vaciar todos los tipos de caché de Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Reindexar todos los indexadores de Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Cambie el DNS y los equilibradores de carga para que apunten al hardware de producción de Magento 2
