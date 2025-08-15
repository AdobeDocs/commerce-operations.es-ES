---
title: 'ACSD-52831: no se pueden realizar pedidos de presupuesto negociables cuando  [!DNL Google reCAPTCHA v3 Invisible] está habilitado'
description: Aplique el parche ACSD-52831 para corregir el problema de Adobe Commerce en el que no puede realizar pedidos de presupuesto negociables cuando  [!DNL Google reCAPTCHA v3 Invisible]  está habilitado.
feature: Quotes, B2B, Checkout
role: Admin
exl-id: fa09e41f-f6c3-4cc7-a814-0e1ac5e9ea2e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-52831: No se pueden realizar pedidos de presupuesto negociables cuando [!DNL Google reCAPTCHA v3 Invisible] está habilitado

El parche ACSD-52831 corrige el problema en el que no puede realizar pedidos de presupuesto negociables cuando [!DNL Google reCAPTCHA v3 Invisible] está habilitado. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.35. El ID del parche es ACSD-52831. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se pueden realizar pedidos de presupuesto negociables cuando [!DNL Google reCAPTCHA v3 Invisible] está habilitado.

<u>Pasos a seguir</u>:

1. Habilite la función de presupuesto B2B.
1. Habilite [!DNL Google reCAPTCHA v3 Invisible] en la tienda para habilitar el cierre de compra o la realización de pedidos.
1. Levante una cotización y proceda al cierre de compra con esa cotización.
1. No podrá realizar un pedido debido al error de CAPTCHA.

<u>Resultados esperados</u>:

La oferta continúa con el cierre de compra.

<u>Resultados reales</u>:

Recibió el error *Error de validación de reCAPTCHA, inténtelo de nuevo*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
