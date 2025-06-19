---
title: Invisible [!DNL reCAPTCHA] falla durante el cierre de compra, lo que impide que se realice el pedido
description: Aplique el parche ACSD-54656 para solucionar el problema de Adobe Commerce donde invisible [!DNL reCAPTCHA] no funciona correctamente durante el cierre de compra, lo que impide realizar un pedido.
feature: Checkout, Gift
role: Admin, Developer
exl-id: 08850189-2e1b-4132-8d63-ce447b1f1211
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-54656: Invisible [!DNL reCAPTCHA] no funciona correctamente durante la desprotección, lo que impide realizar un pedido.

El parche ACSD-54656 corrige el problema en el que el elemento invisible [!DNL reCAPTCHA] no funciona correctamente durante la desprotección, lo que impide realizar un pedido. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.46. El ID del parche es ACSD-54656. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Invisible [!DNL reCAPTCHA] no funciona correctamente durante el cierre de compra, lo que impide que se realice un pedido.

<u>Pasos a seguir</u>:

1. Habilite cualquier tipo de [!DNL reCAPTCHA] para la tarjeta regalo en la página [!UICONTROL Checkout].
1. Agregue el producto al carro de compras y vaya a la página **[!UICONTROL Checkout]**.
1. Expanda el formulario de tarjeta de regalo y rellene un cupón de tarjeta de regalo válido.
1. Haga clic en el botón **[!UICONTROL See balance and apply]**.

<u>Resultados esperados</u>:

La tarjeta regalo se ha aplicado correctamente.

<u>Resultados reales</u>:

Aparece el mensaje de error: Error de validación de *[!DNL reCAPTCHA]. Inténtelo de nuevo*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
