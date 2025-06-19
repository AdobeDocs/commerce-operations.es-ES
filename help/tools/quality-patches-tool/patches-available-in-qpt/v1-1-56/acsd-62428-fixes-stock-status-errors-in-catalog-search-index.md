---
title: 'ACSD-62428: Errores de estado de stock en el índice de búsqueda del catálogo'
description: Aplique el parche ACSD-62428 para solucionar el problema en el que el valor is_out_of_stock en el índice de búsqueda en el catálogo se establece incorrectamente cuando el SKU no se encuentra como atributo en el que se puede buscar.
feature: Inventory, Catalog Management
role: Admin, Developer
exl-id: 4b9d7e4c-f522-4d75-8fc9-dcf14287d02a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62428: Errores de estado de stock en el índice de búsqueda del catálogo

El parche ACSD-62428 corrige el problema en el que los valores de `is_out_of_stock` del índice de búsqueda en el catálogo se establecen en un valor incorrecto cuando el atributo SKU no se establece como en el que se puede buscar. Este parche está disponible con [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. El ID del parche es ACSD-62428. Tenga en cuenta que el problema estaba programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6-p5

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El valor `is_out_of_stock` del índice de búsqueda en el catálogo está establecido en un valor incorrecto cuando el SKU no está configurado como atributo en el que se puede buscar, lo que provoca una representación de existencias inexacta.

<u>Pasos a seguir</u>:

1. Crear un(a) [!UICONTROL Source] personalizado(a) y un(a) [!UICONTROL Stock] personalizado.
1. Cree tres productos simples y asigne su inventario a [!UICONTROL Source] personalizados. Asigne estos productos a una categoría.
1. Establezca *[!UICONTROL Inventory (MSI) Indexer]* en *[!UICONTROL Update on Save]* para facilitar la replicación.
1. Establezca *[!UICONTROL Source Item Status]* en *[!UICONTROL In Stock]* y asigne a *[!UICONTROL Quantity]*.
1. Guarde el producto.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** y abra el atributo **[!UICONTROL SKU]**.
1. Establezca *[!UICONTROL Use In]* en *[!UICONTROL No]*.
1. Cambie la cantidad del producto (asegúrese de que no esté configurada en 0).
1. Guarde el producto.

<u>Resultados esperados</u>:

El valor `is_out_of_stock` refleja con precisión el estado de existencias del producto, incluso cuando el SKU no es un atributo en el que se pueda buscar.

<u>Resultados reales</u>:

El valor `is_out_of_stock` se ha establecido incorrectamente en 1 y el atributo SKU está ausente en los datos indizados.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
