---
title: 'ACP2E-4050: [!UICONTROL Free Shipping] no se aplica con el cierre de compra de envío múltiple'
description: Aplique el parche ACP2E-4050 para corregir el problema de Adobe Commerce en el que [!UICONTROL Free Shipping] no se aplica durante la desprotección de varias direcciones cuando [!UICONTROL Cart Price Rules] incluye condiciones de subselección y productos con precios específicos.
feature: Shopping Cart, Shipping/Delivery
role: Admin, Developer
type: Troubleshooting
source-git-commit: d36ce39fcd897261b784d57f8806b3eceb66fc01
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# ACP2E-4050: **[!UICONTROL Free Shipping]** no se aplica con el cierre de compra de envío múltiple

El parche ACP2E-4050 corrige el problema en el que **[!UICONTROL Free Shipping]** no se aplica durante el cierre de compra de envío múltiple cuando **[!UICONTROL Cart Price Rules]** incluye condiciones de subselección y productos con precios específicos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACP2E-4050. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p10

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

**[!UICONTROL Free Shipping]** no se aplica durante el cierre de compra de envío múltiple cuando **[!UICONTROL Cart Price Rules]** incluye condiciones de subselección y productos con precios específicos.

<u>Pasos a seguir</u>:

1. Cree una cuenta de cliente con dos direcciones.
1. Habilite **[!UICONTROL Free Shipping]** y establezca **[!UICONTROL Minimum Order Amount]** en *999999*.
1. Vaya a [!UICONTROL Admin] > [!UICONTROL Marketing] > [!UICONTROL Cart Price Rules] y cree una regla de precio del carro de compras con las siguientes condiciones:

```
If ALL of these conditions are TRUE:
 * Subtotal is at least 50
 * The subtotal is at most 500
 * Apply this condition if the total amount is 50 or more for a subset of cart items that meet all specified criteria:
 * Category is 23
```

1. Instalar datos de ejemplo.
1. Agregue los siguientes productos al carro de compras en el orden especificado:
   * Wayfarer Messenger Bag
   * Olivia 1/4 Zip Light Jacket
   * Kit de acompañamiento de yoga Sprite.
1. Abra el carro de compras y verifique que la opción **[!UICONTROL Free Shipping]** esté disponible.
1. Haga clic en **[!UICONTROL Check Out with Multiple Addresses]**.
1. Seleccione una dirección de envío diferente para el producto simple.
1. Haga clic en **[!UICONTROL Go to Shipping Information]**.

<u>Resultados esperados</u>:

**[!UICONTROL Free Shipping]** se aplica a los envíos de productos configurables y agrupados.

<u>Resultados reales</u>:

**[!UICONTROL Free Shipping]** no está disponible.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
