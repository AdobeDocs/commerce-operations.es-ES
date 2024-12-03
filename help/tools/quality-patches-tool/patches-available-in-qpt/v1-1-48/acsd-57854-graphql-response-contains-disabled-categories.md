---
title: 'ACSD-57854: la respuesta *GraphQL* contiene categorías desactivadas que no deberían aparecer en las agregaciones de categorías'
description: Aplique el parche ACSD-57854 para solucionar el problema de Adobe Commerce donde la respuesta *GraphQL* contiene categorías desactivadas que no deberían aparecer en las agregaciones de categorías.
feature: GraphQL
role: Admin, Developer
exl-id: 216aad2a-f470-49f9-b8ca-79107ca07891
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-57854: la respuesta *GraphQL* contiene categorías deshabilitadas que no deberían enumerarse en las agregaciones de categorías

El parche ACSD-57854 corrige el problema en el que la respuesta *GraphQL* contiene categorías deshabilitadas que no deberían aparecer en las agregaciones de categorías. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.48. El ID del parche es ACSD-57854. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La respuesta *GraphQL* contiene categorías deshabilitadas que no deberían aparecer en las agregaciones de categorías.

<u>Pasos a seguir</u>:

1. Cree dos categorías.
1. Cree un producto (Producto de Adobe de prueba) y asígnelo a ambas categorías.
1. Deshabilite una de las categorías que se han creado.
1. Use productos *GraphQL* para buscar el producto.
1. Compruebe la lista de categorías de productos en la respuesta *GraphQL*.

<u>Resultados esperados</u>:

Las categorías deshabilitadas no se enumeran en la respuesta *GraphQL*.

<u>Resultados reales</u>:

Las categorías deshabilitadas se enumeran en la respuesta de agregación de categorías *GraphQL*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
