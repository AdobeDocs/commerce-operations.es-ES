---
title: 'ACSD-63574: agregar el listado [!UICONTROL Bundle Product] al bloque mediante  [!DNL Page Builder] genera un error'
description: Aplique el parche ACSD-63574 para solucionar el problema de Adobe Commerce donde al agregar **[!UICONTROL Bundle Product]** con las opciones "Checkbox" o "Multi Select" a un bloque a través de  [!DNL Page Builder] se genera un error.
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: bb56c0c2-e094-4173-8260-da154df79748
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-63574: agregar el listado [!UICONTROL Bundle Product] al bloque a través de [!DNL Page Builder] genera un error

La revisión ACSD-63574 corrige el problema en el cual agregar **[!UICONTROL Bundle Product]** con las opciones `Checkbox` o `Multi Select` a un bloque a través de [!DNL Page Builder] genera un error. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. El ID del parche es ACSD-63574. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4-p10

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al agregar **[!UICONTROL Bundle Product]** a un bloque mediante [!DNL Page Builder], la vista previa del widget de productos se interrumpe y muestra el mensaje de error *Lo sentimos, se produjo un error al generar este contenido*. Este problema ocurre específicamente cuando el paquete de productos incluye `Checkbox` o `Multi Select` tipos de opciones y `indexer dimension mode` está establecido en `website_and_customer_group`. El registro de excepciones muestra el siguiente error:

    &quot;
    report.CRITICAL: PDOException: SQLSTATE[42S02]: No se encontró la tabla o vista base: 1146 La tabla &#39;db_name.catalog_product_index_price_cg0_ws0&#39; no existe en /home/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
    &quot;

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. En el panel izquierdo, expanda **[!UICONTROL Catalog]** y seleccione **[!UICONTROL Catalog]** de las siguientes opciones.
1. Desplácese hacia abajo hasta la sección **[!UICONTROL Price]** y establezca **[!UICONTROL Catalog Price Scope]** en **[!UICONTROL Global]**.
1. Establezca `Indexer dimension mode` en `website_and_customer_group` mediante el siguiente comando:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website_and_customer_group`

1. Cree un(a) **[!UICONTROL Bundle Product]** con un tipo de opción de paquete `Checkbox` o `Multi Select` y asigne el producto a una categoría.
1. Vaya a **[!UICONTROL Content]** > **[!UICONTROL Blocks]** > **[!UICONTROL Edit Content with Page Builder]**.
1. Seleccione la categoría a la que se asigna el producto creado e intente **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

Producto añadido sin errores.

<u>Resultados reales</u>:

No se puede agregar un producto a través de [!DNL Page Builder] cuando el tipo de opción **[!UICONTROL Bundle Product]** es `Checkbox` o `Multi Select` y `indexer dimension mode` está establecido en `website_and_customer_group`. Genera el error: *Se produjo un error al generar este contenido*.


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
