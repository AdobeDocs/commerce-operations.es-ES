---
title: Pasos posteriores a la migración de datos
description: Descubra los pasos que debe seguir después de usar la variable [!DNL Data Migration Tool] para migrar datos del Magento 1 al Magento 2.
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# Pasos posteriores a la migración de datos

Una vez completada la migración y probada exhaustivamente el nuevo sitio de Magento 2, realice las siguientes tareas:

* Coloque el Magento 1 en modo de mantenimiento y detenga permanentemente todo [Administrador](https://glossary.magento.com/admin) actividades

* Iniciar trabajos cron de Magento 2

* [Vaciar todos los tipos de caché de Magento 2](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-cache.html#clean-and-flush-cache-types)

* [Reindexar todos los indexadores del Magento 2](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#reindex)

* Cambie los equilibradores de carga y DNS para que apunten al hardware de producción de Magento 2
