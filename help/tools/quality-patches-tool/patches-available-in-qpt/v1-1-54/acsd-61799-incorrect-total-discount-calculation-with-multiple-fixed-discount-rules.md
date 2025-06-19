---
title: 'ACSD-61799: cálculo de descuento total incorrecto con varias reglas de carro de descuentos fijos aplicadas al presupuesto'
description: Aplique el parche ACSD-61799 para corregir el problema de Adobe Commerce en el que el descuento total se calcula incorrectamente cuando se aplican varias reglas del carro de compras con descuentos fijos a la oferta.
feature: Price Rules
role: Admin, Developer
exl-id: a87ec1cd-f141-43b9-bde1-eca354c12d4e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-61799: cálculo de descuento total incorrecto con varias reglas de carro de descuentos fijos aplicadas al presupuesto

El parche ACSD-61799 resuelve/corrige el problema en el que el descuento total se calcula incorrectamente cuando se aplican varias reglas del carro de compras con descuentos fijos a la oferta. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. El ID del parche es ACSD-61799. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El descuento total se calcula incorrectamente cuando se aplican varias reglas de carro de compras con *[!UICONTROL Fixed amount discount for the whole cart]* a un carro de compras.

<u>Pasos a seguir</u>:

1. Cree cuatro productos con un precio de 1000 $.
1. Cree tres reglas de precio de carro de compras sin ninguna condición que proporcione un descuento de 100 $ para todo el carro de compras.
1. Cree otra regla de precio de carro de compras que proporcione un descuento de 100 $ para todo el carro de compras, con una condición que impida que se aplique la regla.
1. Deshabilite la regla.
1. Agregue tres productos al carro de compras y observe el descuento en el carro de compras.
1. Añadir productos adicionales al carro de compras y observar el descuento en el carro de compras.
1. Activar la regla de precios del carro de compras desactivada.
1. Actualice la página del carro de compras y aplique el descuento.

<u>Resultados esperados</u>:

1. Añadir productos adicionales al carro de compras no cambia la cantidad de descuento.
1. Al habilitar la regla de precio del carro de compras con una condición que no se aplica, no se cambia la cantidad de descuento.

<u>Resultados reales</u>:

1. Si agrega productos adicionales al carro de compras, se cambia la cantidad de descuento.
1. Al habilitar la regla de precio del carro de compras con una condición que no se aplica, se cambia la cantidad de descuento.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
