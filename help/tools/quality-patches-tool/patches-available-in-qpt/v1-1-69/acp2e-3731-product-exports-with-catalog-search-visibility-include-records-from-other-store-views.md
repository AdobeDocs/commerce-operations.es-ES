---
title: 'ACP2E-3731: Las exportaciones de productos con visibilidad de [!UICONTROL Catalog, Search] incluyen registros de otras vistas de tiendas'
description: Aplique el parche ACP2E-3731 para corregir Adobe Commerce donde las exportaciones de productos con el filtro de visibilidad establecido en [!UICONTROL Catalog, Search] incluyen filas incorrectas en configuraciones de varias tiendas debido a variaciones de atributos con alcance de tienda.
feature: Data Import/Export
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7a2e98b836fcc1759910777d1e9fe50e03dabb07
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# ACP2E-3731: Las exportaciones de productos con visibilidad de [!UICONTROL Catalog, Search] incluyen registros de otras vistas de tiendas

El parche ACP2E-3731 corrige el problema en el que las exportaciones de productos con visibilidad *[!UICONTROL Catalog, Search]* incluyen incorrectamente registros de otras vistas de tiendas en entornos de varias tiendas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACP2E-3731. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p9

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las exportaciones de productos incluyen filas incorrectas cuando el filtro de visibilidad está establecido en *[!UICONTROL Catalog, Search]* en configuraciones de varias tiendas debido a variaciones de atributos con alcance de tienda.

<u>Pasos a seguir</u>:

1. En el panel de administración, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** para crear un sitio web, una tienda y una vista de tienda adicionales.
1. Ir a **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* **[!UICONTROL Attribute Set]**. Haga clic en **[!UICONTROL Add Attribute Set]** para crear un atributo. Establezca **[!UICONTROL Based On]** en *Predeterminado*.
1. Cree un producto y asígnelo al sitio web principal y al sitio web secundario.
1. Establezca un valor de texto para el atributo recién creado con **[!UICONTROL Scope]** establecido en *Todas las vistas de la tienda*.
1. Cambie el ámbito a la vista del almacén secundario y actualice el atributo con un valor diferente.
1. Cambie el ámbito a la vista de tienda predeterminada y a la vista de tienda secundaria y, a continuación, establezca la visibilidad del producto en *No visible de forma individual*.
1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Export]** y seleccione *Productos* en el menú desplegable.
1. Establezca un filtro donde **[!UICONTROL Visibility]** = *[!UICONTROL Catalog, Search]* y haga clic en **[!UICONTROL Continue]**.
1. Ejecute el siguiente comando para procesar la exportación:

   ```
   php bin/magento queue:consumers:start exportProcessor
   ```

1. Compruebe el archivo exportado.

<u>Resultados esperados</u>:

Solo se exportan los registros filtrados.

<u>Resultados reales</u>:

El archivo exportado incluye una fila para la vista de almacén secundario, que no coincide con los criterios de filtro establecidos durante la exportación.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
