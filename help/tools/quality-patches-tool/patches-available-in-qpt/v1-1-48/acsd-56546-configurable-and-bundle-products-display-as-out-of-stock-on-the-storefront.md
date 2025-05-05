---
title: 'ACSD-56546: los productos configurables y agrupados se muestran como agotados en la tienda'
description: Aplique el parche ACSD-56546 para corregir el problema de Adobe Commerce en el que los productos configurables y del paquete se muestran como agotados en la tienda cuando la opción de configuración *[!UICONTROL Display Out of Stock Products]* está deshabilitada.
feature: Storefront, Products
role: Admin, Developer
exl-id: d9bb05ca-a84e-48bb-957e-55b28631b3cb
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-56546: los productos configurables y agrupados se muestran como agotados en la tienda

El parche ACSD-56546 corrige el problema en el que los productos configurables y del paquete se muestran como agotados en la tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48. El ID del parche es ACSD-56546. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos configurables y agrupados se muestran como agotados en la tienda cuando la opción *[!UICONTROL Display Out of Stock Products]* está deshabilitada.

<u>Pasos a seguir</u>:

1. Establezca la opción **[!UICONTROL Display Out of Stock Products]** en *No*.
1. Cree un sitio web, una tienda y una vista de tienda.
1. Cree un origen y un inventario y, a continuación, asígnelo al segundo sitio web.
1. Crear un *producto configurable* con dos productos secundarios. Asigne los productos secundarios a ambos orígenes y a ambos sitios web.
1. Actualice el primer producto secundario para que tenga *qty=0* en ambos orígenes.
1. Actualice el segundo producto secundario y desactívelo en el segundo sitio web.
1. Realice una reindexación completa.
1. Compruebe la categoría que contiene el producto configurable en el segundo sitio web.

<u>Resultados esperados</u>:

Los productos configurables que no tienen existencias no son visibles en la tienda.

<u>Resultados reales</u>:

Los productos configurables que no tienen existencias están visibles en la tienda incluso cuando la opción *[!UICONTROL Display Out of Stock Products]* está deshabilitada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
