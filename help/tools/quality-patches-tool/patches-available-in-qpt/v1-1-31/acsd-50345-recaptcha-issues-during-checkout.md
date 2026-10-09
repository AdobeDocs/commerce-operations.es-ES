---
title: 'ACSD-50345: problemas de reCAPTCHA durante el cierre de compra'
description: Aplique el parche ACSD-50345 para corregir el problema de Adobe Commerce en el que las validaciones reCAPTCHA v2 y v3 fallan al realizar pedidos y durante el cierre de compra.
feature: Checkout, Orders
role: Admin
exl-id: eae9a6ad-0999-4581-b3c0-7667ee7beb54
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%
---
# ACSD-50345: problemas de reCAPTCHA durante el cierre de compra

El parche ACSD-50345 corrige el problema en el que las validaciones de reCAPTCHA v2 y v3 fallan al realizar pedidos y durante el cierre de compra. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.31. El ID del parche es ACSD-50345. Tenga en cuenta que el problema se solucionó parcialmente en Adobe Commerce 2.4.6 y se ha programado que se corrija completamente en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

**Caso #1**

Google reCAPTCHA v2 no se vuelve a cargar después de enviar un pago fallido.

<u>Pasos a seguir</u>

1. Configurar **[!UICONTROL Google reCAPTCHA v2]** (*No soy un robot*).
1. Habilitar **[!UICONTROL reCAPTCHA]** para el cierre de compra.
1. Intente realizar un pedido sin hacer clic en **[!UICONTROL reCAPTCHA]**.
1. Una vez que el usuario reciba el mensaje de error correspondiente al reCAPTCHA que falta (*error de validación de reCAPTCHA, inténtelo de nuevo*), haga clic en **[!UICONTROL reCAPTCHA]** e intente realizar un pedido.

<u>Resultados esperados</u>

El pedido no se realizará con un reCAPTCHA incorrecto.

<u>Resultados reales</u>

Se produjo un error - Error de validación de *reCAPTCHA, vuelva a intentarlo* y *No existe ese carro con id = 4*

**Caso #2**

Google reCAPTCHA v3 Invisible no funciona en el cierre de compra y no se puede realizar el pedido. El evento `PlaceOrder` no se ha activado.

<u>Pasos a seguir</u>

1. Configure **[!UICONTROL reCAPTCHA v3 Invisible]** desde **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**.
1. Habilite **[!UICONTROL reCAPTCHA v3 Invisible]** para el cierre de compra o la colocación de un pedido en la ficha **[!UICONTROL Storefront]**.
1. Intente realizar un pedido con el método de pago [!UICONTROL Check/Money order].

<u>Resultados esperados</u>

El pedido se debe realizar con **[!UICONTROL reCAPTCHA]** activado.

<u>Resultados reales</u>

Después de hacer clic en el botón **[!UICONTROL Place Order]**, se deshabilita y no ocurre nada más.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
