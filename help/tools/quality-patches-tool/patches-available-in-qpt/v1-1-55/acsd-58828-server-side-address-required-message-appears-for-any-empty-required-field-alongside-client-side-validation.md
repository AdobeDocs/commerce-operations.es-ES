---
title: 'ACSD-58828: aparece un mensaje del lado del servidor *la dirección es obligatoria* para cualquier campo obligatorio vacío, junto con la validación del lado del cliente'
description: Aplique el parche ACSD-58828 para corregir el problema de Adobe Commerce donde el mensaje de validación del lado del servidor *address is required* aparece si se deja vacío cualquier campo requerido, junto con el mensaje de validación del lado del cliente.
feature: Shipping/Delivery, Checkout
role: Admin, Developer
exl-id: 6c19773d-cb75-409f-bbd7-78d285a0252a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-58828: la dirección *del lado del servidor es necesaria* el mensaje aparece para cualquier campo obligatorio vacío, junto con la validación del lado del cliente

La revisión ACSD-58828 corrige el problema en el que el mensaje de validación del lado del servidor *dirección es necesaria* aparece si se deja vacío cualquier campo requerido, junto con el mensaje de validación del lado del cliente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. El ID del parche es ACSD-58828. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La dirección del mensaje de validación del lado del servidor *es necesaria* aparece si algún campo obligatorio queda vacío, junto con el mensaje de validación del lado del cliente.

Pasos a seguir:

1. Inicie sesión como cliente.
1. Añadir un producto al carro de compras.
1. Continúe con el cierre de compra.
1. Deje la dirección de envío tal cual.
1. Seleccione **[!UICONTROL Flat rate]** y seleccione **[!UICONTROL Next]**.
1. Anule la selección de **[!UICONTROL My billing and shipping address are the same]**.
1. Añada una nueva dirección desde la lista desplegable.
1. Deje cualquier campo requerido vacío y seleccione **[!UICONTROL Update]**.

Resultados esperados:

El mensaje de error describe la información que falta o es incorrecta y que es necesaria para realizar la compra.

Resultados reales:

Se requiere la dirección de error *. Introduzca e inténtelo de nuevo.* se muestra.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
