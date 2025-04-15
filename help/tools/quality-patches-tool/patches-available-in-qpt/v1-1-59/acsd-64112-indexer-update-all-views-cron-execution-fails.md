---
title: 'ACSD-64112: `indexer_update_all_views` la ejecución de cron falla cuando se establece "MAGE_INDEXER_THREADS_COUNT"'
description: Aplique el parche ACSD-64112 para corregir el problema de Adobe Commerce donde la ejecución de cron "indexer_update_all_views" falla cuando se establece "MAGE_INDEXER_THREADS_COUNT".
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: c95f179d-5291-481f-b655-08a9db608513
source-git-commit: 0078cf5fb6d6c3a8650762d7cdf5556de642e201
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-64112: `indexer_update_all_views` la ejecución de cron falla cuando se establece `MAGE_INDEXER_THREADS_COUNT`

>[!NOTE]
>
>Este parche fue reemplazado por [ACP2E-3705](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3705-fixes-an-issue-where-the-indexer.md) para las versiones de Adobe Systems Commerce anteriores a 2.4.7.

La parche ACSD-64112 corrige el problema en el que la ejecución cron `indexer_update_all_views` falla cuando `MAGE_INDEXER_THREADS_COUNT` está configurada. Este parche está disponible cuando está instalado 1.1.59 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) . El ID de parche es ACSD-64112. Tenga en cuenta que el problema está programado para solucionarse en Adobe Systems Commerce 2.4.8.

## Productos y versiones afectados

**El parche se crea para Adobe Systems versión de Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p10

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p10

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Emitir

La `indexer_update_all_views` ejecución de cron falla cuando `MAGE_INDEXER_THREADS_COUNT` se establece en un valor mayor que 2, afectando específicamente al indexador con B2B [!UICONTROL Customer Segments] habilitado.

<u>Procedimiento</u>:

1. Instale un instancia limpio con B2B.
1. Habilitar **[!UICONTROL B2B Company]** y **[!UICONTROL Shared Catalog]**.
1. Crear un categoría.
1. Cree algunos productos y asígnelos a la categoría.
1. Ejecute una reindexación completa.
1. Establezca los siguientes indizadores en **[!UICONTROL Update on Schedule]**:

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Vaya al servidor y cargue la categoría recién creada.
1. Haga clic en **[!UICONTROL Category Permissions]** y cree un **[!UICONTROL New Permission]** para un grupo de clientes existente.
1. Asegúrese de que el `catalogpermissions_category` indexador tenga un trabajo pendiente. Ejecute el siguiente comando para verificarlo:

   ```
   bin/magento indexer:status
   ```

1. Establezca el siguiente número de subprocesos del indexador en `env.php`:

   ```php
   'MAGE_INDEXER_THREADS_COUNT' => 8
   ```

1. Ejecute el trabajo cron:

   ```
   bin/magento cron:run
   ```

<u>Resultados esperados</u>:

El trabajo cron debería ejecutarse sin problemas.

<u>Resultados reales</u>:

El trabajo cron `indexer_update_all_views` encuentra el siguiente error:

```
report.CRITICAL: PDOException: There is no active transaction in /home/vendor/magento/zend-db/library/Zend/Db/Adapter/Pdo/Abstract.php:326
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Pasos adicionales necesarios después de la instalación del parche

(Esta sección es opcional; es posible que se requieran algunos pasos después de aplicar el parche para solucionar el problema). 

## Lecturas relacionadas

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: Un herramienta de autoservicio para parches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) de calidad en el Herramientas guía.
