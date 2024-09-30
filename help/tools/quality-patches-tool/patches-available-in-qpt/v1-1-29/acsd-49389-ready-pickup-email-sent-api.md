---
title: "ACSD-49389: listo para recibir correo electrónico enviado por API cuando no está listo para recibir"
description: Aplique el parche ACSD-49389 para solucionar el problema de Adobe Commerce donde la API envía un correo electrónico listo para recibir cuando el pedido no está listo para recibir.
feature: REST, Communications
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49389: listo para recibir correo electrónico enviado por API cuando no está listo para recibir

El parche ACSD-49389 corrige el problema en el que la API envía un correo electrónico listo para recibir cuando el pedido no está listo para recibir. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-49389. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la [página de aterrizaje de QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La API envía un correo electrónico listo para la recogida cuando el pedido no está listo para la recogida.

<u>Pasos a seguir</u>:

1. Habilite el método *[!UICONTROL In-Store Delivery]*.
1. Cree un origen de stock con la ubicación de recogida habilitada.
1. Cree nuevas existencias utilizando el sitio web principal con la fuente creada anteriormente.
1. Cree un producto que asigne el mismo origen.
1. Establecer cantidad de stock = 1.
1. Consulte el producto creado en el paso 4 mediante el método *[!UICONTROL In-Store Delivery]* de la tienda.
1. Cree una factura para el pedido.
1. Establezca la cantidad del producto en *0* y sírvase de existencias.
1. Publique la siguiente solicitud de API:

```
{
    "orderIds": [
        1
    ]
}
```

<u>Resultados esperados</u>:

El correo electrónico listo para la recogida no se envía.

<u>Resultados reales</u>:

La API devuelve *El pedido no está listo para la recogida*, pero se envía un mensaje de correo electrónico listo para la recogida.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
