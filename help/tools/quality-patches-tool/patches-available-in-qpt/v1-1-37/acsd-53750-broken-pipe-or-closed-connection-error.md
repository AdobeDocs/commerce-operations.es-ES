---
title: '"ACSD-53750: Error de "Tubería rota o conexión cerrada" durante el reíndice catalog_product_price multiproceso"'
description: Aplique el parche ACSD-53750 para corregir el problema de Adobe Commerce en el que se produce un error de *Conexión rota o Conexión cerrada* durante el reíndice catalog_product_price multiproceso.
feature: Products
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-53750: *Error de canalización rota o conexión cerrada* durante el reíndice de `catalog_product_price` de subprocesos múltiples

La revisión ACSD-53750 corrige el problema en el que se produce un error de *interrupción de la canalización o conexión cerrada* durante el reíndice de `catalog_product_price` de subprocesos múltiples. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.37. El ID del parche es ACSD-53750. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

*Se ha roto la canalización o se ha cerrado la conexión* durante el reindexado de `catalog_product_price` de subprocesos múltiples.

<u>Pasos a seguir</u>:

1. Configure RabbitMq.
1. Generar datos de ejemplo utilizando el archivo `small.xml` adjunto.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** y establezca **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**.
1. Establezca el modo de dimensión para los índices que admitan esto. Por ejemplo: `catalog_product_price_website_and_customer_group` o `customer_group`.

   ```
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. Ejecutar el restablecimiento de indizadores para `catalog_product_price`.

   ```
   bin/magento indexer:reset catalog_product_price
   ```

1. Ejecute el indexador para el indexador de restablecimiento utilizando varios subprocesos.

   ```
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>Resultados esperados</u>:

No se producen errores.

<u>Resultados reales</u>:

El siguiente error se debe a una conexión AMQP: *Conexión rota o cerrada*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
