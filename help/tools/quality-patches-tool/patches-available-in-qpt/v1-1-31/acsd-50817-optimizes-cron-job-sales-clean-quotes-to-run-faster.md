---
title: "ACSD-50817: Optimiza el trabajo cron sales_clean_quote para que se ejecute más rápido"
description: Aplique el parche ACSD-50817 para optimizar el trabajo cron "sales_clean_quote" para que se ejecute más rápido añadiendo un índice compuesto en las columnas "store_id" y "updated_at" en la tabla de ofertas.
feature: Quotes
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-50817: optimiza el trabajo cron `sales_clean_quotes` para que se ejecute más rápido

El parche ACSD-50817 optimiza el trabajo cron `sales_clean_quotes` para que se ejecute más rápido al agregar un índice compuesto en las columnas `store_id` y `updated_at` de la tabla de comillas. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.31. El ID del parche es ACSD-50817.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El trabajo cron `sales_clean_quotes` es demasiado lento. Con este parche, se ha optimizado para que se ejecute más rápido agregando un índice compuesto en las columnas `store_id` y `updated_at` de la tabla de comillas.

<u>Pasos a seguir</u>:

1. Generar 50-80 millones de presupuestos con `updated_at` establecido como un período &lt; 30 días.
1. Ejecute el trabajo cron `sales_clean_quotes` o la siguiente consulta en la tabla de oferta:

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>Resultados esperados</u>

El trabajo cron `sales_clean_quotes` está optimizado para ejecutarse más rápido al agregar un índice compuesto en las columnas `store_id` y `updated_at` de la tabla de comillas.

<u>Resultados reales</u>

La consulta es demasiado lenta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
