---
title: 'ACSD-63469: Los descuentos del carro de compras de cantidad fija no se aplican correctamente con varias reglas'
description: Aplique el parche ACSD-63469 para corregir el problema de Adobe Commerce en el que los descuentos de cantidad fija para todo el carro de compras no se aplican correctamente cuando se aplica más de una regla.
feature: Price Rules
role: Admin, Developer
source-git-commit: 3699a9f64198558fcf1ffe53753f035d22c2d301
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---


# ACSD-63469: Los descuentos del carro de compras de cantidad fija no se aplican correctamente con varias reglas

El parche ACSD-63469 corrige el problema de que los descuentos de cantidad fija para todo el carro de compras no se aplican correctamente cuando se aplica más de una regla. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. El ID del parche es ACSD-63469. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se aplican varias reglas de **[!UICONTROL Fixed amount discount for whole cart]** simultáneamente y los productos tienen precios especiales o con descuento, el valor de descuento se calcula incorrectamente.

<u>Pasos a seguir</u>:

1. Cree dos productos con un precio de 850 y 85 dólares y establezca sus precios especiales en 765 y 68 dólares, respectivamente.
1. Cree dos **[!UICONTROL Cart Price Rules]** de la siguiente manera:
   * Regla 1
      * **[!UICONTROL Conditions]**: para el producto de 850 $, establezca *Cantidad* en *igual o mayor que 2*
      * **[!UICONTROL Actions]**: aplicar **[!UICONTROL Fixed amount discount for whole cart]** de *$153*
   * Regla 2
      * **[!UICONTROL Conditions]**: para el producto de 85 $, establezca *Cantidad* en *igual o mayor que 2*
      * **[!UICONTROL Actions]**: aplicar **[!UICONTROL Fixed amount discount for whole cart]** de *$14*
1. Agregue ambos productos al carro de compras, cada uno con una cantidad de 2.

<u>Resultados esperados</u>:

El descuento aplicado en el carro es de 167 $.

<u>Resultados reales</u>:

El descuento aplicado en el carro de compras es de 41 $.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Pasos adicionales necesarios tras la instalación del parche

(Esta sección es opcional; es posible que se requieran algunos pasos después de aplicar el parche para solucionar el problema). 

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.

