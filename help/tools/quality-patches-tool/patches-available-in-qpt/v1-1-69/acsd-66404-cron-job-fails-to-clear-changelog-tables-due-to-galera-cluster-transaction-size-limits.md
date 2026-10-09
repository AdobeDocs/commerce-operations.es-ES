---
title: 'ACSD-66404: el trabajo de cron no puede borrar las tablas de registro de cambios debido a los límites de tamaño de transacción de [!DNL Galera Cluster]'
description: Aplique el parche ACSD-66404 para corregir el problema de Adobe Commerce con el trabajo cron sin borrar las tablas changelog y causando [!DNL Galera Cluster] problemas en caso de una gran cantidad de datos en estas tablas.
feature: System
role: Admin, Developer
type: Troubleshooting
exl-id: d7ad3b11-aee6-4a26-8892-369fbfe6932e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
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
source-wordcount: '382'
ht-degree: 0%
---
# ACSD-66404: el trabajo de cron no puede borrar las tablas de registro de cambios debido a los límites de tamaño de transacción de [!DNL Galera Cluster]

El parche ACSD-66404 corrige el problema en el que el trabajo cron no borra las tablas changelog, lo que provoca [!DNL Galera Cluster] problemas al gestionar grandes cantidades de datos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACSD-66404. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p6, 2.4.7-p6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El trabajo cron no borra las tablas changelog y causa [!DNL Galera Cluster] problemas en caso de una gran cantidad de datos en estas tablas.

<u>Pasos a seguir</u>:

1. Genere muchos productos utilizando perfiles de rendimiento.
1. Realice una actualización masiva de todos los productos del sistema, por lo que hay muchas entradas en la tabla de base de datos `inventory_cl`.
1. Ejecute el trabajo cron `indexer_clean_all_changelogs`.

<u>Resultados esperados</u>:

El trabajo cron de `indexer_clean_all_changelogs` puede realizar la limpieza del registro de cambios en registros de cambios grandes (10+ GB) en varias consultas de eliminación, sin causar [!DNL Galera Cluster] problemas.

<u>Resultados reales</u>:

El trabajo cron de `indexer_clean_all_changelogs` realiza la limpieza del registro de cambios en registros de cambios grandes (más de 10 GB) en una única consulta de eliminación, lo que provoca [!DNL Galera Cluster] problemas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas
