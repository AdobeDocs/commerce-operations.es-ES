---
title: 'ACSD-53118: Las reglas del carro de compras con cupón no funcionan correctamente'
description: Aplique el parche ACSD-53118 para corregir el problema de Adobe Commerce en el que la regla de precio del carro de compras se aplica mediante un código de cupón, mientras que el producto del carro de compras tiene un atributo de coincidencia vacío.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 8957790e-c22b-4a25-939b-94d7a9fb1cc7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-53118: Las reglas del carro de compras con cupón no funcionan correctamente

El parche ACSD-53118 corrige el problema en el que la regla de precio del carro de compras se aplica usando un código de cupón mientras que el producto en el carro de compras tiene un atributo de coincidencia vacío. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41. El ID del parche es ACSD-53118. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La regla de precio del carro de compras se aplica mediante un código de cupón mientras que el producto del carro de compras tiene un atributo de coincidencia vacío.

<u>Pasos a seguir</u>:

1. Cree un atributo de precio y añádalo al juego de atributos. Hacer que el atributo se pueda utilizar en condiciones de regla de promoción.
1. Cree un producto y deje vacío el nuevo atributo.
1. Cree una regla de precio de carro de compras con un cupón específico y la siguiente condición:

   * Si se ENCUENTRA un elemento en el carro de compras con TODAS estas condiciones en true: Atributo1 es 0.

1. Añada el producto creado en el paso 2 al carro de compras.
1. Utilice el código de cupón para la regla de carro de compras creada en el paso 3.

<u>Resultados esperados</u>:

El descuento no se aplica al carro de compras.

<u>Resultados reales</u>:

El descuento se aplica al carro de compras.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
