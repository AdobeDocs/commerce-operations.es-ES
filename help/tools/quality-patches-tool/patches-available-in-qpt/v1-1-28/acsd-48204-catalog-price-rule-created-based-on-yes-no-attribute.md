---
title: 'ACSD-48204: La regla de precios de catálogo creada en función del atributo *Sí/No* no tiene en cuenta el ámbito seleccionado'
description: Aplique el parche ACSD-48204 para corregir el problema de Adobe Commerce en el que la regla de precios de catálogo creada en función del atributo *Sí/No* no tiene en cuenta el ámbito seleccionado.
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
exl-id: 69f2b35c-856e-4f96-ae2f-fb0c64d5eb94
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 2%
---
# ACSD-48204: La regla de precios de catálogo creada en función del atributo *Yes/No* no tiene en cuenta el ámbito seleccionado

El parche ACSD-48204 corrige el problema en el que la regla de precios de catálogo creada en función del atributo *Yes/No* no tiene en cuenta el ámbito seleccionado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28. El ID del parche es ACSD-48204. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La regla de precios de catálogo creada basada en el atributo *Yes/No* no tiene en cuenta el ámbito seleccionado.

<u>Pasos a seguir</u>:

1. Crear dos sitios web (Predeterminado y W2).
1. Crear un atributo de producto de tipo *Sí/No*.
   * Conjunto [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Cree un producto configurable basado en cualquier atributo con dos variaciones (V1 y V2).
   * Agregue el atributo *Yes/No* al conjunto de atributos de variaciones configurables
   * Para una de las variaciones (V1), establezca el valor en *[!UICONTROL Yes]* en el sitio web no predeterminado (W2)
1. Crear una regla de catálogo:
   * Se aplica a ambos sitios web
   * Condición: *Sí/No* valor de atributo es *[!UICONTROL Yes]*
   * Descuento = 50 %
1. Abra el producto configurable en el sitio web no predeterminado (W2).
1. Compruebe que la variación V1 tenga el descuento del 50 % aplicado.
1. Abra la variación V1 en el Administrador de Adobe Commerce.
   * Cambiar al sitio web predeterminado
   * No realice cambios y guarde el producto
1. Actualice la página de tienda de productos configurable.

<u>Resultados esperados</u>:

La variación V1 sigue teniendo el descuento del 50 % aplicado, ya que no se han realizado cambios.

<u>Resultados reales</u>:

El descuento desaparece.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
