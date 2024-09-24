---
title: "ACSD-52398: la cantidad solicitada no está disponible al intentar actualizar la cantidad del producto agrupado"
description: Aplique el parche ACSD-52398 para solucionar el problema de Adobe Commerce en el que la cantidad solicitada no está disponible al intentar actualizar la cantidad de un producto agrupado en el carro de compras de la tienda.
feature: Shopping Cart, Quotes, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-52398: la cantidad solicitada no está disponible al intentar actualizar la cantidad del producto agrupado

El parche ACSD-52398 corrige el problema en el que la cantidad solicitada no está disponible al intentar actualizar la cantidad de un producto agrupado en el carro de compras de la tienda. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.35. El ID del parche es ACSD-52398. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cantidad solicitada no está disponible al intentar actualizar la cantidad de un producto agrupado en el carro de compras en la tienda.

<u>Pasos a seguir</u>:

1. Cree dos productos simples con las cantidades *1* y *10*.
1. Cree un producto agrupado con los productos simples.
1. Añadir el producto agrupado al carro de compras.
1. Edite el producto e intente actualizar la cantidad a *3* para la opción donde hay disponibles *10* elementos.

<u>Resultados esperados</u>:

No hay ningún error. La cantidad se ha actualizado correctamente debido a que hay *10* elementos en stock para esta opción.

<u>Resultados reales</u>:

Se genera el siguiente error: *La cantidad solicitada no está disponible*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
