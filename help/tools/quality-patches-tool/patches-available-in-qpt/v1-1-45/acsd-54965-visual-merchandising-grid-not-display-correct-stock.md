---
title: 'ACSD-54965: la cuadrícula [!UICONTROL Visual Merchandising] no muestra las existencias correctas'
description: Aplique el parche ACSD-54965 para corregir el problema de Adobe Commerce en el que la cuadrícula [!UICONTROL Visual Merchandising] no muestra las existencias correctas cuando se asigna un producto a las existencias personalizadas.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: bd8a3547-1d84-4a17-b006-b35d92256211
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-54965: la cuadrícula [!UICONTROL Visual Merchandising] no muestra las existencias correctas

El parche ACSD-54965 corrige el problema en el que la cuadrícula [!UICONTROL Visual Merchandising] no muestra las existencias correctas cuando se asigna un producto a las existencias personalizadas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45. El ID del parche es ACSD-54965. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cuadrícula [!UICONTROL Visual Merchandising] no muestra las existencias correctas cuando se asigna un producto a las existencias personalizadas.

<u>Pasos a seguir</u>:

1. Cree una nueva fuente.
1. Cree un nuevo inventario de stock.
1. Cree dos productos:
   * Un producto solo con el stock personalizado.
   * Un producto solo con las existencias predeterminadas.
1. Añada estos productos a una categoría.
1. Ir a la cuadrícula [!UICONTROL visual Merchandising] (*[!UICONTROL Products in Category]*).

<u>Resultados reales</u>:

En los ámbitos *[!UICONTROL All Store Views]*, el producto con existencias personalizadas no muestra ninguna cantidad. Solo cuando se selecciona el ámbito *[!UICONTROL Default Store View]*, el inventario personalizado muestra la cantidad del producto.

<u>Resultados esperados</u>:

La cuadrícula muestra toda la información de existencias si el ámbito es *[!UICONTROL All Store Views]*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
