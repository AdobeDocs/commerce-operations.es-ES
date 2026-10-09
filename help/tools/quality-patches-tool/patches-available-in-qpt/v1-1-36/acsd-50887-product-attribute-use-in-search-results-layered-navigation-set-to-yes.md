---
title: 'ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* establecido en Sí sin la opción *[!UICONTROL Use in Search]*'
description: Aplique el parche ACSD-50887 para corregir el problema de Adobe Commerce en el que la propiedad de atributo de producto *[!UICONTROL Use in Search Results Layered Navigation]* se puede establecer en *Sí* sin que la opción *[!UICONTROL Use in Search]* también se establezca en *Sí*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: 5e797121-c386-4aca-9139-0a02a60be38a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
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
source-wordcount: '461'
ht-degree: 0%
---
# ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* se estableció en *Yes* sin la opción *[!UICONTROL Use in Search]*

La revisión ACSD-50887 corrige el problema en el que la propiedad de atributo de producto *[!UICONTROL Use in Search Results Layered Navigation]* se puede establecer en *Sí* sin que la opción *[!UICONTROL Use in Search]* también se establezca en *Sí*. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.36. El ID del parche es ACSD-50887. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La propiedad de atributo de producto *[!UICONTROL Use in Search Results Layered Navigation]* se puede establecer en *Sí* sin que la opción *[!UICONTROL Use in Search]* también se establezca en *Sí*.

Estos ajustes se diseñaron para utilizarse juntos. Con el parche aplicado, cuando la opción *[!UICONTROL Use in Search]* está establecida en *No*, la opción *[!UICONTROL Use in Search Results Layered Navigation]* está oculta para funcionar como si también estuviera establecida en *No*.

<u>Pasos a seguir</u>:

1. En el Administrador, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** y cree un atributo con el tipo multiselect y establezca lo siguiente:

   * *[!UICONTROL Use in Search]= No*
   * *[!UICONTROL Use in Layered Navigation]= (Cualquier opción)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Sí*
   * *Nombre = Atributo_de_prueba*
   * *Opciones*:
     * *Etiqueta*
     * *Selector*

1. Agregue el nuevo atributo al conjunto de atributos predeterminado.
1. Cree dos productos:

   1. Primer producto:
      * Nombre = Etiqueta
      * Establecer precio, cantidad, peso en 1
      * Atributo de prueba = seleccionar opción *Etiqueta*

   1. Segundo producto:
      * Nombre = Selector
      * Establecer precio, cantidad, peso en 1
      * Atributo_prueba = seleccionar ambas opciones

1. Ejecutar reindexación `catalogsearch_fulltext`:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Busca por la palabra *sticker* en la tienda.

<u>Resultados esperados</u>:

Solo se devuelve el producto *Sticker*, porque [!DNL Elasticsearch] no indexará Test_attribute cuando *[!UICONTROL Use in Search]* se haya establecido en *No*.

<u>Resultados reales</u>:

Se devuelven ambos productos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
