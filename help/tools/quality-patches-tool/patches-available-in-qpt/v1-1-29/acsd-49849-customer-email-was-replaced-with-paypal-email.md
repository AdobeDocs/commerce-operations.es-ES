---
title: 'ACSD-49849: el correo electrónico del cliente se ha sustituido por el de PayPal'
description: Aplique el parche ACSD-49849 para solucionar el problema de Adobe Commerce en el que el correo electrónico del cliente se ha sustituido por correo electrónico de PayPal al realizar un pedido con PayPal Express a través de GraphQL.
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 1d7a2bde-892a-4ded-a4b4-9450989c8aee
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-49849: el correo electrónico del cliente se ha reemplazado por [!DNL PayPal] correo electrónico

El parche ACSD-49849 corrige el problema en el cual el correo electrónico de un cliente se reemplaza con un correo electrónico de [!DNL PayPal's] al realizar un pedido con [!DNL PayPal Express] a través de GraphQL. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-49849. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El correo electrónico de un cliente se reemplaza con un correo electrónico [!DNL PayPal's] al realizar un pedido con [!DNL PayPal Express] a través de GraphQL.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Habilite y configure [!DNL PayPal Express] y establezca **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y cree un producto simple.
1. Complete el cierre de compra de invitados con GraphQL. Para obtener más información, consulte el [tutorial de cierre de compra de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) en la documentación para desarrolladores de Adobe Commerce.
1. Usar [!DNL PayPal Express] como método de pago.
1. Tenga en cuenta el correo electrónico que utilizó en el paso en el que [configuró su correo electrónico para el carro de compras](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) en la documentación para desarrolladores de Adobe Commerce.
1. Una vez realizado el pedido, vaya al administrador de Adobe Commerce y compruebe el correo electrónico en el pedido creado.

<u>Resultados esperados</u>:

El correo electrónico es el mismo que se establece durante el cierre de compra.

<u>Resultados reales</u>:

El correo electrónico establecido durante la desprotección se anula con el correo electrónico establecido en la cuenta de [!DNL PayPal].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
