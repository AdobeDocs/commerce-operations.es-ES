---
title: '"ACSD-56415: el rendimiento de [!UICONTROL Partial Price Indexing] se ralentizó debido a la consulta "DELETE"'
description: Aplique el parche ACSD-56415 para corregir el problema de Adobe Commerce en el que el rendimiento de [!UICONTROL Partial Price Indexing] se ve ralentizado debido a una consulta "DELETE" cuando la base de datos tiene muchos datos de precios parciales para indexar.
feature: Catalog Service
role: Admin, Developer
source-git-commit: 809defe75d7b218d8085f85ff815472a531040cf
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-56415: el rendimiento de [!UICONTROL Partial Price Indexing] se ha ralentizado debido a la consulta `DELETE`

El parche ACSD-56415 corrige el problema en el que el rendimiento de [!UICONTROL Partial Price Indexing] se ralentiza debido a una consulta `DELETE` cuando la base de datos tiene un montón de índice de datos de precios parciales. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45. El ID del parche es ACSD-56023. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El rendimiento de [!UICONTROL Partial Price Indexing] se ve ralentizado debido a una consulta `DELETE` cuando la base de datos tiene un montón de índice de datos de precios parciales.

<u>Pasos a seguir</u>:

1. Cree *300000 productos* y *10 sitios web* con el perfil de rendimiento grande.
1. Inicie sesión en el panel de administración.
1. Crear *10 grupos de clientes*.
1. Ejecute la siguiente consulta para agregar productos a la tabla `_cl`:

   &grave;&grave;
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 &grave;&grave;

1. Ejecute el siguiente comando para almacenar en déclencheur el proceso de indexación de precios parcial:

   &grave;&grave;
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 &grave;&grave;

<u>Resultados esperados</u>:

El DELETE de consultas SQL `main_table` DE `catalog_product_index_price` se ejecuta rápidamente.

<u>Resultados reales</u>:

El DELETE de consultas SQL `main_table` DE `catalog_product_index_price` se ejecuta muy lentamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool]
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
