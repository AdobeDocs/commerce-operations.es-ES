---
title: 'ACSD-63062: cálculos de descuento del carro de compras incorrectos con varias reglas superpuestas'
description: Aplique el parche ACSD-63062 para corregir el problema de Adobe Commerce donde se producen cálculos incorrectos de descuento en el carro de compras cuando se aplican varias reglas superpuestas.
feature: Price Rules
role: Admin, Developer
exl-id: c4a93063-b640-444e-ba0e-552dd8d1895b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63062: cálculos de descuento del carro de compras incorrectos con varias reglas superpuestas

El parche ACSD-63062 corrige el problema en el que se producen cálculos de descuento en el carro de compras incorrectos cuando se aplican varias reglas superpuestas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. El ID del parche es ACSD-63062. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se producen cálculos de descuento del carro de compras incorrectos cuando se aplican varias reglas superpuestas.

<u>Pasos a seguir</u>:

1. Instale una instancia nueva con datos de ejemplo.
1. Cree tres productos simples:

   * simple1: 1080 $
   * simple2: 260 $
   * simple3: 280 $

1. Cree cuatro *[!UICONTROL Cart Price Rules]* de la siguiente manera:

   * Regla 1:

      * *[!UICONTROL Priority]*: 100
      * Ficha *[!UICONTROL Conditions]*: utilice el producto simple2 ($280) si la cantidad total es igual o mayor que 3
      * Ficha *[!UICONTROL Actions]*: el SKU es simple2
      * *[!UICONTROL Fixed Amount Discount]*: 80 $

   * Regla 2:

      * *[!UICONTROL Priority]*: 200
      * Ficha *[!UICONTROL Actions]*: el SKU es simple2
      * *[!UICONTROL Percentage of Product Price Discount]*: 20 %

   * Regla 3:

      * *[!UICONTROL Priority]*: 300
      * *[!UICONTROL Conditions]* ficha: el subtotal es igual o mayor que 1000 $
      * *[!UICONTROL Fixed Amount Discount]* para todo el carro de compras: 100 $

   * Regla 4:

      * *[!UICONTROL Priority]*: 400
      * Pestaña *[!UICONTROL Conditions]*: utilice el producto simple1 ($1080) si la cantidad total es igual o mayor que 2
      * Ficha *[!UICONTROL Actions]*: el SKU es simple1
      * *[!UICONTROL Fixed Amount Discount]* para todo el carro de compras: $960

1. Vaya a la tienda y añada los siguientes productos con una cantidad determinada al carro de compras:

   * simple1 = 2
   * simple2 = 1
   * simple3 = 3

1. Compruebe el carro de compras.

<u>Resultados esperados</u>:

El descuento aplicado es de 1352 $.

<u>Resultados reales</u>:

El descuento aplicado es de 1525,33 $.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
