---
title: 'ACSD-46767: [!UICONTROL Category] caché de página invalida cuando cambia la cantidad de existencias'
description: Aplique el parche ACSD-46767 para corregir el problema de Adobe Commerce en el que la caché de la página [!UICONTROL Category] se invalida cuando cambia la cantidad de existencias, incluso si el producto aún está en existencias.
feature: Cache, Products, Inventory
role: Admin, Developer
exl-id: 5872dca7-fdef-47ad-8718-bf343cd3a42a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '394'
ht-degree: 0%
---
# ACSD-46767: [!UICONTROL Category] caché de página invalida cuando cambia la cantidad de existencias

El parche ACSD-46767 corrige el problema en el que las cachés de la página [!UICONTROL Category] se invalidan cuando cambia la cantidad de existencias, incluso si el producto aún está en existencias. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.46. El ID del parche es ACSD-46767. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!UICONTROL Category] cachés de página invalidan cuando cambia la cantidad de stock.

<u>Pasos a seguir</u>:

1. Cree algunos productos y agréguelos a la misma categoría.
1. Abra la página *[!UICONTROL Category]* en la tienda para asegurarse de que la página se almacena en caché.
1. Coloque el pedido con uno de los productos de la categoría *(la cantidad del producto ha cambiado, pero el producto sigue en existencias)*.
1. Vuelva a abrir la página [!UICONTROL Category] en la tienda.

<u>Resultados reales</u>:

La página no se carga desde la caché. Se vuelve a generar.

<u>Resultados esperados</u>:

La página se carga desde la caché.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
