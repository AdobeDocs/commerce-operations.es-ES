---
title: 'ACSD-61756: degradación de rendimiento de los filtros AdvancedSalesRule debido a la falta de índices de base de datos'
description: Aplique el parche ACSD-61756 para solucionar el problema de Adobe Commerce, donde la consulta magento_salesrule_filter realiza un análisis de tabla completo sin utilizar índices, lo que provoca una degradación del rendimiento al gestionar grandes volúmenes de registros. Este parche mejora el rendimiento añadiendo los índices de base de datos que faltan para los filtros AdvancedSalesRule.
feature: Price Rules, Price Indexer
role: Admin, Developer
exl-id: 418c7c40-83ee-4cd9-8ebb-b356886ffb58
source-git-commit: 23e92bb9032001134d2696be498a4c384f323c36
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-61756: degradación de rendimiento de `AdvancedSalesRule` filtros debido a la falta de índices de base de datos

Aplique el parche ACSD-61756 para mejorar el rendimiento de los filtros `AdvancedSalesRule` agregando los índices de base de datos que faltan. Esto corrige el problema en el cual la consulta `magento_salesrule_filter` realiza un análisis de tabla completo sin utilizar los índices, lo que provoca una degradación del rendimiento cuando hay muchos registros en la tabla. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.54. El ID del parche es ACSD-61756. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p9

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La consulta `magento_salesrule_filter` realiza un análisis de tabla completo sin utilizar índices, lo que provoca una degradación del rendimiento de los filtros `AdvancedSalesRule` cuando hay muchos registros en la tabla.

<u>Pasos a seguir</u>:

1. Cierre la compra con varias reglas de ventas activas.

<u>Resultados esperados</u>:

Rendimiento mejorado de las reglas de ventas.

<u>Resultados reales</u>:

La consulta realiza un análisis de tabla completo y no utiliza índices, lo que provoca una degradación del rendimiento cuando hay muchos registros en la tabla.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
