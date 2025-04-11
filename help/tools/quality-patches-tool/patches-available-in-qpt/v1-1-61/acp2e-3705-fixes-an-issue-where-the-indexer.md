---
title: 'ACP2E-3705: Se produce un error en la ejecución cron de "indexer_update_all_views" cuando se establece "MAGE_INDEXER_THREADS_COUNT".'
description: Aplicar el parche ACP2E-3705 para solucionar el problema de Adobe Systems Commerce, donde la ejecución cron de "indexer_update_all_views" falla cuando se establece "MAGE_INDEXER_THREADS_COUNT".
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: 111325fa-8ed5-45f9-9e68-b52f4425d253
source-git-commit: 7ef772510274bc8681c395656437d64f8b40e70a
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACP2E-3705: `indexer_update_all_views` error en la ejecución de cron cuando `MAGE_INDEXER_THREADS_COUNT` se configura

>[!NOTE]
>
>Este parche reemplaza al [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md) para las versiones 2.4.7 y superiores.

El parche ACP2E-3705 corrige el problema donde la ejecución cron `indexer_update_all_views` falla cuando `MAGE_INDEXER_THREADS_COUNT` está configurada. Este parche está disponible cuando está instalado 1.1.61 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) . El ID de parche es ACP2E-3705. Tenga en cuenta que este problema está programado para solucionarse en Adobe Systems Commerce 2.4.9.

## Productos y versiones afectados

**El parche se crea para Adobe Systems versión de Commerce:**

* Adobe Systems Commerce (todos los métodos implementación) 2.4.7-p4

**Compatible con las versiones de Adobe Systems Commerce:**

* Adobe Systems Commerce (todos los métodos implementación) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con nuevas [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Systems Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]Search para parches Página](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Emitir

La `indexer_update_all_views` ejecución de cron falla cuando `MAGE_INDEXER_THREADS_COUNT` se establece en un valor mayor que *2*, afectando específicamente al indexador con B2B [!UICONTROL Customer Segments] habilitado.

<u>Procedimiento</u>:

1. Aplicar el QPT parche [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md).
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Category permissions]**.
1. Habilite **[!UICONTROL Category Permissions]**.
1. Ponga en **[!UICONTROL Update on Schedule]** modo los siguientes indexadores:

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Crear algunos productos y asígnelos a una categoría.
1. Ejecute un reindexado completo.
1. Vaya a un categoría y establezca **[!UICONTROL Category Permissions]**.
1. Ejecutar `indexer_update_all_views` trabajo cron con `MAGE_INDEXER_THREADS_COUNT` establecido en *8*.

<u>Resultados esperados</u>:

La reindexación se ha completado sin errores.

<u>Resultados reales</u>:

El `indexer_update_all_views` trabajo cron encuentra el siguiente error:

```
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función de su método implementación:

* Adobe Systems de comercio o Magento Open Source local: [[!DNL Quality Patches Tool] uso >](/help/tools/quality-patches-tool/usage.md) en el [!DNL Quality Patches Tool] guía.
* Adobe Systems Commerce on infraestructura en la nube: Upgrades and Patches > Aplicar Patches in the Commerce on Cloud Infrastructure guía.

## Lecturas relacionadas

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: Un herramienta de autoservicio para parches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) de calidad en el Herramientas guía.
