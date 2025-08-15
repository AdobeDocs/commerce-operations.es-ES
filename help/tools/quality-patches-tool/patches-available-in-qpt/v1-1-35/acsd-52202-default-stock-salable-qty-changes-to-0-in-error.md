---
title: 'ACSD-52202: La cantidad vendible de stock predeterminada cambia a 0 por error cuando las existencias no predeterminadas se establecen en 0 cant en orden'
description: Aplique el parche ACSD-52202 para corregir el problema de Adobe Commerce en el que una cantidad vendible de stock predeterminada cambia a 0 por error cuando el stock no predeterminado se establece en 0 en un pedido.
feature: Inventory, Products
role: Admin
exl-id: 2ba5cc3b-9774-49f6-948f-371ab3c0c9df
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-52202: La cantidad vendible de stock predeterminada cambia a 0 por error cuando el stock no predeterminado se establece en 0 cantidad en un pedido

El parche ACSD-52202 corrige el problema en el que una cantidad vendible de stock (cantidad) predeterminada cambia a 0 por error cuando el stock no predeterminado se establece en 0 cantidad en un pedido. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.35. El ID del parche es ACSD-52202. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cantidad vendible de stock predeterminada cambia a 0 por error cuando el stock no predeterminado se establece en 0 cantidad en un pedido.

<u>Pasos a seguir</u>:

1. Inicie sesión en [!DNL Admin].
1. Crear **sitio web2**.
1. Crear **origen2** personalizado.
1. Crear **stock2** personalizado.
1. Asigne **source2** y **stock2** al **sitio web1**, y el origen y las existencias predeterminados al sitio web predeterminado.
1. Cree un producto simple y asigne **qty** = *10* para el origen predeterminado y **qty** = *1* para el origen **source2**.
1. Realiza un pedido con **qty** = *1* para **sitio web2**.
1. Cree una factura y un envío.
1. Compruebe el producto simple **cantidad vendible**.

<u>Resultados esperados</u>:

La **cantidad comercializable** = *10* para **origen2**.

<u>Resultados reales</u>:

La **cantidad vendible** = *0* para ambos orígenes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
