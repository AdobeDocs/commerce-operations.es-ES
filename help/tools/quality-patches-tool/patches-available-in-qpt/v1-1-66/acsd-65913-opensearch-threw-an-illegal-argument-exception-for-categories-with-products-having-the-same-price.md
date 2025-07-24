---
title: 'ACSD-65913: [!DNL OpenSearch] lanza una excepción de argumento_ilegal para categorías con productos que tienen el mismo precio'
description: Aplique el parche ACSD-65913 para corregir el problema de Adobe Commerce en el que  [!DNL Opensearch] está generando una excepción de argumento ilegal ("[from] parámetro no puede ser negativo") en las categorías que contienen todos los productos con el mismo precio.
feature: Search
role: Admin, Developer
type: Troubleshooting
source-git-commit: fa4c50fdf6b51c981e49369dc9f70600f46b5689
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---


# ACSD-65913: [!DNL OpenSearch] emite un `illegal_argument_exception` para categorías con productos que tienen el mismo precio

La revisión ACSD-65913 corrige el problema en el cual [!DNL OpenSearch] arrojó un `illegal_argument_exception` para categorías con productos que tenían el mismo precio. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. El ID del parche es ACSD-65913. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!DNL OpenSearch] emite un `illegal_argument_exception` (*[del parámetro ] no puede ser negativo*) al cargar categorías en las que todos los productos compartían el mismo precio.

<u>Pasos a seguir</u>:

1. Instale [!DNL OpenSearch] versión 2.19.1 y configúrelo como motor de búsqueda predeterminado.
1. Configure el atributo de producto **[!UICONTROL Price]** para que sea visible en la navegación por capas:
   1. **[!UICONTROL Visible in Advanced Search]**: *Sí*
   1. **[!UICONTROL Comparable on Storefront]**: *Sí*
   1. **[!UICONTROL Use in Layered Navigation]**: *Filtrable (con resultados)*
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Layered Navigation]**. Establezca **[!UICONTROL Price Navigation Step Calculation]** en *Automático (igualar recuentos de productos)*.
1. Cree una categoría con seis productos que tengan el mismo precio:
   1. SKU: product_super_0-1-1-1, precio: 150 $
   1. SKU: product_super_0-1-1, precio: 48 $
   1. SKU: product_super_0-1, precio: 48 $
   1. SKU: product_super_0, precio: 48 $
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1-1-1-1-1-1, precio: 48 $
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1-1, precio: 48 $
1. Ejecute el siguiente comando:
   `bin/magento indexer:reindex`
1. Abra la página de categoría. Verá un error:.
   El parámetro *[from] no puede ser negativo; se encontró [-1]*

<u>Resultados esperados</u>:

[!DNL OpenSearch] no debería arrojar un `illegal_argument_exception` cuando todos los productos de una categoría tengan el mismo precio.

<u>Resultados reales</u>:

* [!DNL OpenSearch] lanza un `illegal_argument_exception` con el mensaje:
  El parámetro *[from] no puede ser negativo; se encontró [-1]*

* El archivo `var/log/exception.log` contiene:

  ```
  [2025-05-14T22:39:33.595272+00:00] report.CRITICAL: [!DNL OpenSearch]\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"}],"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"},"status":400}
  ```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
