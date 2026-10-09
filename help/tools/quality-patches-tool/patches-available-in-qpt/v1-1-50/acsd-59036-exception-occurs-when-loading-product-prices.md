---
title: 'ACSD-59036: Se produce una excepción al cargar precios de productos con límites inferior y superior establecidos en 0 $'
description: Aplique el parche ACSD-59036 para solucionar el problema de Adobe Commerce donde se produce una excepción al cargar precios de productos con límites inferior y superior establecidos en *$0*.
feature: Categories, Products, Storefront, Search
role: Admin, Developer
exl-id: a7d05108-0b03-4eb4-84ab-0dc5601530cb
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
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
source-wordcount: '465'
ht-degree: 0%
---
# ACSD-59036: Se produce una excepción al cargar precios de productos con límites inferior y superior establecidos en *$0*

El parche ACSD-59036 corrige el problema en el que se produce una excepción al cargar precios de productos con límites inferior y superior establecidos en *$0*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50. El ID del parche es ACSD-59036. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce una excepción al cargar precios de productos con los límites inferior y superior establecidos en *$0*.

El problema se produce porque el algoritmo no tiene en cuenta los valores NULL al cargar la consulta con intervalos de precios. Para solucionarlo, podemos comprobar si los intervalos inferior y superior son NULL y, si lo son, asignar un valor de *0* para ambos límites. Esto debería evitar que se generen errores.

<u>Pasos a seguir</u>:

1. Crear *13* productos simples.
1. Asignar todos los productos de *13* a una categoría.
1. Establezca el precio de un producto en *$1322.94*.
1. Establezca el precio de todos los demás productos en *$0*.
1. Configure [!DNL OpenSearch] como motor de búsqueda.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** y establezca el recuento de **[!UICONTROL PLP]** en *16*.
1. Establezca **[!UICONTROL Price Navigation Step Calculation]** en *Automático (igualar recuentos de productos)*.
1. Ejecutar reindexación completa.
1. Abra la página *[!UICONTROL Category]*.

<u>Resultados esperados</u>:

La página *[!UICONTROL Category]* muestra todos los productos.

<u>Resultados reales</u>:

Se produce un error:

```JSON
report.CRITICAL: OpenSearch\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]"}],"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [filter]","caused_by":{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]","caused_by":{"type":"illegal_argument_exception","reason":"field name is null or empty"}}},"status":400} in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Connections/Connection.php:664
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
