---
title: 'ACSD-66093: los campos de nombre de cliente invitado permiten la entrada de correo electrónico, lo que provoca correos electrónicos de pedido no válidos'
description: Aplique el parche ACSD-66093 para corregir el problema de Adobe Commerce donde es posible introducir direcciones de correo electrónico en los campos Cliente invitado **[!UICONTROL First Name]** y **[!UICONTROL Last Name]** y enviar correos electrónicos de confirmación de pedido no válidos.
feature: Checkout
role: Admin, Developer
source-git-commit: 6ee2f99b53424071fda4cba9396aa039621135fc
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---


# ACSD-66093: los campos de nombre de cliente invitado permiten la entrada de correo electrónico, lo que provoca correos electrónicos de pedido no válidos

El parche ACSD-66093 corrige el problema en el que se podían introducir direcciones de correo electrónico en los campos **[!UICONTROL First Name]** y **[!UICONTROL Last Name]** del cliente invitado, lo que daba como resultado correos electrónicos de confirmación de pedido no válidos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. El ID del parche es ACSD-66093. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p11

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se pudieron introducir direcciones de correo electrónico en los campos **[!UICONTROL First Name]** y **[!UICONTROL Last Name]** del cliente invitado, lo que resultó en correos electrónicos de confirmación de pedido no válidos.

<u>Pasos a seguir</u>:

1. Agregue productos al carro de compras como cliente invitado.
2. Vaya a Pago y envío.
3. Rellene la dirección de correo electrónico con &quot;test1@gmail.co&quot;.
4. Rellene **[!UICONTROL First Name]** con &quot;<test2@gmail.co>&quot;.
5. Rellene **[!UICONTROL Last Name]** con &quot;<test3@gmail.co>&quot;.
6. Rellene otros campos obligatorios.
7. Realice el pedido.

<u>Resultados esperados</u>:

Los mensajes de validación deberían aparecer para indicar que los campos **[!UICONTROL First Name]** y **[!UICONTROL Last Name]** no son válidos, como *El nombre no es válido. y el apellido no son válidos.* y no se debe realizar el pedido.

<u>Resultados reales</u>:

Se realiza el pedido.
Los campos **[!UICONTROL First Name]** y **[!UICONTROL Last Name]** se guardan como se ingresaron.
El correo electrónico de confirmación de pedido se envía a los tres correos electrónicos: test1@gmail.co, test2@gmail.co y test3@gmail.co.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
