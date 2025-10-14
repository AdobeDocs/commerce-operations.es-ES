---
title: 'ACSD-51819: realización de varios pedidos con un solo ID de oferta'
description: Aplique el parche ACSD-51819 para solucionar el problema de Adobe Commerce, en el que se pueden realizar varios pedidos a través del mismo ID de oferta.
feature: Orders, Checkout
role: Admin, Developer
exl-id: dbca8790-d947-4104-bba9-b29abcfc0344
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-51819: realización de varios pedidos con un solo ID de oferta

El parche ACSD-51819 corrige el problema en el que se pueden realizar varios pedidos a través del mismo ID de presupuesto. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41. El ID del parche es ACSD-51819. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2, 2.4.5-p5, 2.4.6, 2.4.6-p4, 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p11, 2.4.5-p3 - 2.4.5-p10, 2.4.6 - 2.4.6-p8, 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se pueden realizar varios pedidos con el mismo ID de oferta.

<u>Pasos a seguir</u>:

1. Inicie sesión como usuario.
1. Agregue elementos al carro de compras y continúe con el cierre de compra.
1. Elija cualquier forma de pago, pero no haga clic en el botón **[!UICONTROL Place Order]**.
1. Inicie sesión en la misma cuenta en otro explorador.
1. Realice el cierre de compra con los mismos elementos sin hacer clic en el botón **[!UICONTROL Place Order]**.
1. Haga clic en el botón **[!UICONTROL Place Order]** en ambos sistemas al mismo tiempo.
1. Valide los pedidos realizados en ambos exploradores.

<u>Resultados esperados</u>:

Solo se procesa correctamente el primer pedido realizado desde un explorador.

<u>Resultados reales</u>:

Los pedidos se han realizado en ambos navegadores.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
