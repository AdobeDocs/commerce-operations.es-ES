---
title: 'ACSD-64112: `indexer_update_all_views` la ejecución de cron falla cuando se establece "MAGE_INDEXER_THREADS_COUNT"'
description: Aplique el parche ACSD-64112 para corregir el problema de Adobe Commerce donde la ejecución de cron "indexer_update_all_views" falla cuando se establece "MAGE_INDEXER_THREADS_COUNT".
feature: Catalog Management, B2B
role: Admin, Developer
source-git-commit: 544c7b9664ccc9204c2c0c78b103ad823e18ef7d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---


# ACSD-64112: `indexer_update_all_views` la ejecución de cron falla cuando se establece `MAGE_INDEXER_THREADS_COUNT`

El parche ACSD-64112 corrige el problema en el que la ejecución de `indexer_update_all_views` cron falla cuando se establece `MAGE_INDEXER_THREADS_COUNT`. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. El ID del parche es ACSD-64112. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p10

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La ejecución de cron de `indexer_update_all_views` falla cuando `MAGE_INDEXER_THREADS_COUNT` se establece en un valor mayor que 2, lo que afecta específicamente al indizador [!UICONTROL Customer Segments] con B2B habilitado.

<u>Pasos a seguir</u>:

1. Instale una instancia limpia con B2B.
1. Habilitar **[!UICONTROL B2B Company]** y **[!UICONTROL Shared Catalog]**.
1. Cree una categoría.
1. Cree algunos productos y asígnelos a la categoría.
1. Ejecute una reindexación completa.
1. Establezca los siguientes indizadores en **[!UICONTROL Update on Schedule]**:

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Vaya al servidor y cargue la categoría recién creada.
1. Haga clic en **[!UICONTROL Category Permissions]** y cree un **[!UICONTROL New Permission]** para un grupo de clientes existente.
1. Asegúrese de que el indizador `catalogpermissions_category` tenga un registro de pendientes. Ejecute el siguiente comando para verificarlo:

   ```
   bin/magento indexer:status
   ```

1. Establezca el siguiente recuento de subprocesos del indizador en `env.php`:

   ```php
   'MAGE_INDEXER_THREADS_COUNT' => 8
   ```

1. Ejecute el trabajo cron:

   ```
   bin/magento cron:run
   ```

<u>Resultados esperados</u>:

El trabajo cron debe ejecutarse sin ningún problema.

<u>Resultados reales</u>:

El trabajo cron `indexer_update_all_views` encuentra el siguiente error:

```
report.CRITICAL: PDOException: There is no active transaction in /home/vendor/magento/zend-db/library/Zend/Db/Adapter/Pdo/Abstract.php:326
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Pasos adicionales necesarios tras la instalación del parche

(Esta sección es opcional; es posible que se requieran algunos pasos después de aplicar el parche para solucionar el problema). 

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
