---
title: Pasos de la migración posterior a los datos
description: Descubra los pasos que debe seguir después de usar [!DNL Data Migration Tool] para migrar datos de Magento 1 a Magento 2.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 0%
---
# Pasos de la migración posterior a los datos

Después de completar la migración y probar a fondo el nuevo sitio de Magento 2, realice las siguientes tareas:

* Ponga Magento 1 en modo de mantenimiento y detenga permanentemente todas las actividades de administración

* Iniciar trabajos de Magento 2 cron

* [Vaciar todos los tipos de caché de Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Reindexar todos los indexadores de Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Cambiar DNS y equilibradores de carga para que apunten al hardware de producción de Magento 2
