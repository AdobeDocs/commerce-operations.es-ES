---
title: 'ACSD-56546: los productos configurables y agrupados se muestran como agotados en la tienda'
description: Aplique el parche ACSD-56546 para corregir el problema de Adobe Commerce en el que los productos configurables y del paquete se muestran como agotados en la tienda cuando la opción de configuración *[!UICONTROL Display Out of Stock Products]* está deshabilitada.
feature: Storefront, Products
role: Admin, Developer
exl-id: d9bb05ca-a84e-48bb-957e-55b28631b3cb
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%
---
# ACSD-56546: los productos configurables y agrupados se muestran como agotados en la tienda

El parche ACSD-56546 corrige el problema en el que los productos configurables y del paquete se muestran como agotados en la tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.48. El ID del parche es ACSD-56546. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
