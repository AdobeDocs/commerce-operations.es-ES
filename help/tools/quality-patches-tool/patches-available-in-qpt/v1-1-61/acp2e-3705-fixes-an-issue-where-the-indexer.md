---
title: 'ACP2E-3705: &grave;indexer_update_all_views&grave; La ejecución de cron falla cuando se establece "MAGE_INDEXER_THREADS_COUNT"'
description: Aplique el parche ACP2E-3705 para corregir el problema de Adobe Commerce donde la ejecución de cron "indexer_update_all_views" falla cuando se establece "MAGE_INDEXER_THREADS_COUNT".
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: 111325fa-8ed5-45f9-9e68-b52f4425d253
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '326'
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
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La ejecución de cron `indexer_update_all_views` falla cuando `MAGE_INDEXER_THREADS_COUNT` se establece en un valor mayor que *2*, lo que afecta específicamente al indizador [!UICONTROL Customer Segments] con B2B habilitado.

<u>Pasos a seguir</u>:

1. Aplique el parche QPT [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md).
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Category permissions]**.
1. Habilitar **[!UICONTROL Category Permissions]**.
1. Establezca los siguientes indizadores en el modo **[!UICONTROL Update on Schedule]**:

   ```
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

```
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura en la nube: Actualizaciones y parches > Aplicar parches en la guía de Commerce en la infraestructura en la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
