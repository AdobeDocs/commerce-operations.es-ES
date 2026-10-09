---
title: 'ACP2E-3705: `indexer_update_all_views` La ejecución de cron falla cuando se establece "MAGE_INDEXER_THREADS_COUNT"'
description: Aplique el parche ACP2E-3705 para corregir el problema de Adobe Commerce donde la ejecución de cron "indexer_update_all_views" falla cuando se establece "MAGE_INDEXER_THREADS_COUNT".
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: 111325fa-8ed5-45f9-9e68-b52f4425d253
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '341'
ht-degree: 0%
---
# ACP2E-3705: `indexer_update_all_views` falla la ejecución de cron cuando se establece `MAGE_INDEXER_THREADS_COUNT`

>[!NOTE]
>
>Este parche reemplaza el [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md) para las versiones 2.4.7 y posteriores.

El parche ACP2E-3705 corrige el problema en el que la ejecución de `indexer_update_all_views` cron falla cuando se establece `MAGE_INDEXER_THREADS_COUNT`. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. El ID del parche es ACP2E-3705. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La ejecución de cron `indexer_update_all_views` falla cuando `MAGE_INDEXER_THREADS_COUNT` se establece en un valor mayor que *2*, lo que afecta específicamente al indizador [!UICONTROL Customer Segments] con B2B habilitado.

<u>Pasos a seguir</u>:

1. Aplique el parche QPT [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md).
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Category permissions]**.
1. Habilitar **[!UICONTROL Category Permissions]**.
1. Establezca los siguientes indizadores en el modo **[!UICONTROL Update on Schedule]**:

   ```shell
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Cree algunos productos y asígnelos a una categoría.
1. Ejecute una reindexación completa.
1. Vaya a una categoría y establezca **[!UICONTROL Category Permissions]**.
1. Ejecutar trabajo cron `indexer_update_all_views` con `MAGE_INDEXER_THREADS_COUNT` establecido en *8*.

<u>Resultados esperados</u>:

La reindexación se completa sin errores.

<u>Resultados reales</u>:

El trabajo cron `indexer_update_all_views` encuentra el siguiente error:

```text
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura en la nube: Actualizaciones y parches > Aplicar parches en la guía de Commerce en la infraestructura en la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
* [Reindexación en modo paralelo](/help/configuration/cli/manage-indexers.md#reindexing-in-parallel-mode) en la Guía de configuración de Commerce.
