---
title: "ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* establecido en Sí sin la opción *[!UICONTROL Use in Search]*"
description: Aplique el parche ACSD-50887 para corregir el problema de Adobe Commerce en el que la propiedad de atributo de producto *[!UICONTROL Use in Search Results Layered Navigation]* se puede establecer en *Sí* sin que la opción *[!UICONTROL Use in Search]* también se establezca en *Sí*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '437'
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
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
