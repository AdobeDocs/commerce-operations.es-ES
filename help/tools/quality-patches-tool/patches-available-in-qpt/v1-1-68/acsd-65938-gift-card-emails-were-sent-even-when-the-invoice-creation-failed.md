---
title: 'ACSD-65938: correos electrónicos de tarjeta de regalo enviados incluso cuando falló la creación de la factura'
description: Aplique el parche ACSD-65938 para solucionar el problema de Adobe Commerce donde los correos electrónicos con tarjeta regalo se enviaron antes de que la factura se guardara y confirmara correctamente, lo que garantiza que los correos electrónicos se activen después de guardar correctamente la factura.
feature: Orders, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: b688875cd0a7bfc07dba77254605e7055ae7cca4
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# ACSD-65938: correos electrónicos de tarjeta de regalo enviados incluso cuando falló la creación de la factura

El parche ACSD-65938 resuelve un problema por el que los correos electrónicos de tarjetas de regalo se enviaban antes de que la factura se guardara y confirmara correctamente. Con esta corrección, los correos electrónicos ahora solo se activan después de que la factura se haya guardado correctamente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. El ID del parche es ACSD-65938. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se han enviado correos electrónicos con tarjeta de regalo antes de confirmar que la factura se ha creado y guardado correctamente, lo que da como resultado que se envíen correos electrónicos incluso cuando falla la creación de la factura.

<u>Pasos a seguir</u>:

1. Inicie sesión en el panel **[!UICONTROL Admin]**.
2. Vaya a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Cards]** > **[!UICONTROL Gift Card General Settings]** y establezca **[!UICONTROL Generate Gift Card Account when Order Item is]** en *Facturado*.
3. Cree un nuevo producto de tarjeta regalo.
4. Agregar producto del carro de regalos al carro de compras y continuar con **[!UICONTROL checkout]**. Puedes usar **[!UICONTROL Check/Money Order]** como método de pago.
5. Realice el pedido.
6. Modifique `OrderRepository` para simular una excepción durante la colocación del pedido.
7. Envíe una solicitud POST a `rest/default/V1/order/<ORDER_ID>/invoice` con la siguiente carga útil:

   ```
   {
     "capture": true,
     "notify": true
   }
   ```


<u>Resultados esperados</u>:

No se debe enviar ningún correo electrónico de tarjeta regalo si falla la creación de la factura.

<u>Resultados reales</u>:

El correo electrónico de la tarjeta regalo se envía aunque se haya producido un error en la creación de la factura.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
