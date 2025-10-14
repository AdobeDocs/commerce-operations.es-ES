---
title: 'ACSD-63067: resolución de problemas de validación de cantidades en productos agrupados en tienda'
description: Aplique el parche ACSD-63067 para solucionar el problema de Adobe Commerce, en el que todas las cantidades de productos de los productos agrupados se resaltan incorrectamente como no válidas cuando solo un producto tiene una cantidad incorrecta.
feature: Storefront
role: Admin, Developer
exl-id: a497f2c4-8bf0-41da-955a-a58e79f09c08
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-63067: resolución de problemas de validación de cantidades en productos agrupados en tienda

El parche ACSD-63067 corrige el problema en el que todas las cantidades de productos en productos agrupados se resaltan incorrectamente como no válidas cuando solo un producto tiene una cantidad incorrecta. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. El ID del parche es ACSD-63067. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

En los productos agrupados, una cantidad no válida en uno de los subproductos hace que todas las cantidades se resalten incorrectamente como no válidas. Además, aparece un mensaje de validación para todos los productos en lugar de solo para el que tiene la cantidad no válida.

<u>Pasos a seguir</u>:

1. Cree un nuevo producto agrupado con al menos dos productos simples como opciones.
1. Abra el producto en la tienda.
1. Introduzca una cantidad no válida (por ejemplo: -1) para una de las opciones y una cantidad válida (por ejemplo: 1) para las demás opciones.
1. Haga clic en **[!UICONTROL Add to Cart]**.

<u>Resultados esperados</u>:

Solo el producto con la cantidad no válida se resalta como no válido.

<u>Resultados reales</u>:

Todas las cantidades de productos se resaltan como no válidas y aparece el mensaje *Especifique la cantidad de productos. se muestra para todos los productos*.


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
