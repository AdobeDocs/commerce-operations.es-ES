---
title: '"ACSD-57074: *Sí/No* el atributo personalizado con el prefijo "price_*" en el atributo "attribute_code" no funciona con la indexación"'
description: Aplique el parche ACSD-57074 para solucionar el problema de Adobe Commerce donde el atributo personalizado *Yes/No* con el prefijo "price_* en el atributo "attribute_code" no funciona con la indexación.
feature: Products, Categories, Catalog Management
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-57074: *Sí/No* el atributo personalizado con prefijo `price_*` en el atributo `attribute_code` no funciona con la indexación

El parche ACSD-57074 corrige el problema en el que el atributo personalizado *Yes/No* con el prefijo `price_*` en el atributo `attribute_code` no funciona con la indexación. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.47. El ID del parche es ACSD-57074. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El atributo personalizado *Yes/No* con el prefijo `price_*` en el atributo `attribute_code` no funciona con la indización.

<u>Pasos a seguir</u>:

1. Cree un atributo de producto personalizado con las siguientes opciones:
   * *[!UICONTROL Catalog Input Type]*: *Sí/No*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *Sí*
1. Asigne el atributo al conjunto de atributos predeterminado.
1. Cree un producto con el atributo que hemos creado.
1. Asigne el producto que hemos creado a una categoría.
1. Ejecutar reindexación completa.

<u>Resultados esperados</u>:

El producto se muestra en la categoría asignada.

<u>Resultados reales</u>:

El producto no aparece en la página de categoría principal.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
