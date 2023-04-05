---
title: Pasos posteriores a la migración de datos
description: Descubra los pasos que debe seguir después de usar la variable [!DNL Data Migration Tool] para migrar datos del Magento 1 al Magento 2.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# Pasos posteriores a la migración de datos

Una vez completada la migración y probada exhaustivamente el nuevo sitio de Magento 2, realice las siguientes tareas:

* Ponga el Magento 1 en modo de mantenimiento y detenga permanentemente todas las actividades de administración

* Iniciar trabajos cron de Magento 2

* [Vaciar todos los tipos de caché de Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Reindexar todos los indexadores del Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Cambie los equilibradores de carga y DNS para que apunten al hardware de producción de Magento 2
