---
title: 'ACSD-46618: el widget de lista de productos muestra precios en caché incorrectos para clientes que iniciaron sesión'
description: Aplique un parche para corregir el problema de Adobe Commerce en el que el widget de lista de productos muestra precios en caché incorrectos para un cliente que ha iniciado sesión.
feature: Cache, Orders, Products
role: Admin
exl-id: fa350f84-2fe5-474b-b4fd-d6c1e8bb0f95
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%
---
# ACSD-46618: el widget de lista de productos muestra precios en caché incorrectos para un cliente que ha iniciado sesión

El parche ACSD-46618 soluciona el problema de que el widget de lista de productos muestra precios en caché incorrectos para un cliente que ha iniciado sesión. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 1.1.21. El ID del parche es ACSD-46618. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El parche ACSD-46618 soluciona el problema de que el widget de lista de productos muestra precios en caché incorrectos para un cliente que ha iniciado sesión.

<u>Pasos a seguir</u>:

1. En el Administrador de Adobe Commerce, seleccione **[!UICONTROL Stores]**, luego **[!UICONTROL Configuration]**, expanda **[!UICONTROL Sales]** y seleccione **[!UICONTROL Tax]**. Actualice la configuración de impuestos para mostrar los precios, incluidos y excluidos los impuestos.
1. Conjunto **[!UICONTROL Enable Cross Border Trade]** = _Sí_.
1. Cree una regla fiscal que solo se aplique a EE. UU.
1. Agregue un widget a la página de inicio que incluya más de un producto.
1. Cree dos clientes con una dirección de EE. UU. y otra que no sea de EE. UU.
1. Inicie sesión con el cliente de EE. UU. desde la tienda. Asegúrese de que la página se almacena en caché.
1. Observe el precio mostrado en el widget de página de inicio.
1. Cierre la sesión e inicie sesión con un cliente que no sea de EE. UU.

<u>Resultados esperados</u>:

El precio mostrado en el widget de página de inicio corresponde a la dirección del cliente.

<u>Resultados reales</u>:

El widget de página de inicio muestra los precios usando el impuesto para clientes que no son estadounidenses.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
