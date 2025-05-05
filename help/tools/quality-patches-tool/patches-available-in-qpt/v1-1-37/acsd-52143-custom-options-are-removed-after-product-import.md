---
title: "ACSD-52143: las opciones personalizadas se eliminan después de importar el producto"
description: Aplique el parche ACSD-52143 para corregir el problema de Adobe Commerce en el que las opciones de personalización se eliminan después de importar el producto.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-52143: las opciones personalizadas se eliminan después de importar el producto

El parche ACSD-52143 corrige el problema en el que las opciones personalizadas se eliminan después de la importación del producto. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.37. El ID del parche es ACSD-52143. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las opciones personalizadas se eliminan después de la importación del producto.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Store]** > **[!UICONTROL All Stores]** y configure una instancia de varias tiendas (un sitio web con dos vistas de tiendas).
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y cree dos productos con [!UICONTROL Customizable Options].
1. En cada producto, agregue [!UICONTROL Customizable Option].
1. Cambie a la vista de la segunda tienda y modifique el nombre del producto en cada producto.
1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** y exporte los dos productos que creó.
1. Descargue el archivo CSV.
1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** y vuelva a importar el archivo.
1. Compruebe ambos productos.

<u>Resultados esperados</u>:

Las opciones personalizadas no se eliminan después de la importación del producto.

<u>Resultados reales</u>:

Las opciones de aduana se eliminan después de la importación del producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
