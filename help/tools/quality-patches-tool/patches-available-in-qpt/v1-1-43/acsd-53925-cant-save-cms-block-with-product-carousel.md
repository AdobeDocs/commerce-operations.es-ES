---
title: 'ACSD-53925: no se puede guardar el bloque de CMS con [!UICONTROL Product Carousel]'
description: Aplique el parche ACSD-53925 para solucionar el problema de Adobe Commerce en el que el administrador no puede guardar un bloque de CMS con Carrusel de productos cuando el modo de dimensiones para catalog_product_price está configurado en el sitio web.
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: f6d286ab-d904-4f08-8265-99632f74b88a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: ed510963-0b8c-4764-86f6-f3c7735bc334
    internal-label: Page Builder
  - id: b0d35b91-b9b0-5983-b37c-f35bd2650b53
    internal-label: Price Indexer
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
source-wordcount: '424'
ht-degree: 0%
---
# ACSD-53925: no se puede guardar el bloque de CMS con *[!UICONTROL Product Carousel]*

La revisión ACSD-53925 corrige el problema en el cual el administrador no puede guardar un bloque de CMS con *[!UICONTROL Product Carousel]* cuando el modo de dimensiones para `catalog_product_price` está establecido en el sitio web. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.43. El ID del parche es ACSD-53925. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El administrador no puede guardar un bloque de CMS con *[!UICONTROL Product Carousel]* cuando el modo de dimensiones de `catalog_product_price` está establecido en el sitio web.

<u>Pasos a seguir</u>:

1. Cree dos productos simples:
   * simple1 - $10
   * simple2 - $20
1. Cree un producto agrupado &#39;*bundle1-dyn*&#39; con dos opciones basadas en SKU de producto simples.
1. Establezca el modo de dimensiones para el indexador de precios del producto:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. Vaya a **[!UICONTROL Content]** > **[!UICONTROL Blocks]** y cree un nuevo bloque de CMS.
1. Editar el contenido mediante [!DNL Page Builder]:
   * Agregar un elemento *[!UICONTROL Row]*
   * Agregar un elemento *[!UICONTROL Products]*
   * Seleccionar *[!UICONTROL Product Carousel]*
   * Introducir SKU del producto: *paquete1-dinar*
1. Guarde el bloque de CMS.

<u>Resultados esperados</u>:

El usuario puede añadir un carrusel de productos sin errores.

<u>Resultados reales</u>:

* Se ha lanzado un mensaje en la interfaz de usuario: *Lo sentimos, se produjo un error al generar este contenido*
* `var/log/exception.log` contiene el siguiente error:

  ```text
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
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
