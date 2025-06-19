---
title: 'ACSD-45675: la exportación de productos utiliza nombres de categoría del ámbito de vista de tienda predeterminado'
description: El parche de ACSD-45675 corrige el problema en el que la exportación del producto utiliza nombres de categoría desde el ámbito de vista de tienda predeterminado. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20. El ID del parche es ACSD-45675. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: ebe72038-511d-43e1-bd65-e5b468342f05
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-45675: la exportación de productos utiliza nombres de categoría del ámbito de vista de tienda predeterminado

El parche de ACSD-45675 corrige el problema en el que la exportación del producto utiliza nombres de categoría desde el ámbito de vista de tienda predeterminado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20. El ID del parche es ACSD-45675. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La exportación de productos utiliza nombres de categoría del ámbito de vista de tienda predeterminado.

<u>Pasos a seguir</u>:

1. Crear una vista de tienda personalizada **[!UICONTROL Thai]** dentro del almacén principal.
1. Hacer que **[!UICONTROL Thai]** sea la vista de tienda predeterminada del sitio web principal.
1. Cree la siguiente estructura de categorías en **[!UICONTROL Default Category]**:

   *[!UICONTROL Default category/Tea/Black]*

1. Seleccione la categoría **[!UICONTROL Tea]** y cambie **[!UICONTROL Scope]** a **[!UICONTROL Thai]**.
1. Establezca **[!UICONTROL Category Name]** como **[!UICONTROL ชาดำ]**.
1. Cree un producto simple **[!UICONTROL SP001]** y asigne la categoría **[!UICONTROL Black]**.
1. Asegúrese de que el cron no funcione.
1. Realice una exportación de productos. Filtre por SKU y seleccione **[!UICONTROL SP001]**.
1. Compruebe la columna **[!UICONTROL categories]** en el CSV exportado.

<u>Resultados esperados</u>:

Como no se seleccionó ningún almacén durante la exportación, debe obtener una ruta de categoría como la siguiente: *[!UICONTROL Default Category/Tea/Black]*.

<u>Resultados reales</u>:

La ruta de la categoría tiene idiomas mixtos: *[!UICONTROL Default Category/ชาดำ/Black]*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tools] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía de la herramienta Parches de calidad.
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
