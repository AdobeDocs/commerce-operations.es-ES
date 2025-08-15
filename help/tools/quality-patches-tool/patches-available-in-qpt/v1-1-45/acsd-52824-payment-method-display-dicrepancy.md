---
title: 'ACSD-52824: métodos de pago desactivados mostrados para los clientes de la empresa'
description: Aplique el parche ACSD-52824 para solucionar el problema de Adobe Commerce donde aparecen  [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] métodos de pago para clientes de la empresa a pesar de estar deshabilitados en la configuración de la empresa.
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 39d67de6-1796-4067-ae7a-ef17fcf794e5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-52824: métodos de pago desactivados mostrados para los clientes de la empresa

El parche ACSD-52824 corrige el problema en el que aparecen los métodos de pago [!DNL PayPal Express], [!DNL Google Pay] y [!DNL Apple Pay] para los clientes de la empresa a pesar de estar deshabilitados en la configuración de la empresa. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45. El ID del parche es ACSD-52824. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se muestran los métodos de pago desactivados para los clientes de la empresa.

<u>Pasos a seguir</u>:

1. Configure y habilite [!DNL PayPal Express Checkout]. Vaya a **[!UICONTROL Basic Settings]** > seleccione **[!DNL PayPal Express Checkout]** y establezca la opción de **[!UICONTROL Display on Shopping Cart]** en *Sí*.
1. Configure [!DNL Braintree] y habilite [!DNL Apple Pay] y [!DNL Google Pay] mediante [!DNL Braintree].
1. Vaya a **[!UICONTROL Customers]** > **[!UICONTROL Companies]** y cree una nueva compañía.
1. Haga clic en **[!UICONTROL Advanced Settings]**, busque **[!UICONTROL Applicable Payment Methods]** y elija **[!UICONTROL Selected Payment Methods]**.
1. En **[!UICONTROL Selected Payment Methods]**, elija métodos de pago que estén habilitados y no estén asociados con *[!DNL PayPal Express Checkout]*, *[!DNL Apple Pay]* o *[!DNL Google Pay]*. Por ejemplo, seleccione **[!UICONTROL Check/Money Order]**.
1. Después de seleccionar los métodos de pago adecuados, cree un nuevo cliente y asócielo a la empresa creada anteriormente.
1. Inicie sesión con la cuenta de cliente asociada a la compañía y continúe para agregar artículos al carro de compras.
1. Preste atención al minicarrito, al carro de compras y al paso de pago durante el proceso de cierre de compra.

<u>Resultados esperados</u>:

Las opciones de pago de [!DNL PayPal] y [!DNL Braintree] no están visibles en el minicarrito ni en el carro de compras.

<u>Resultados reales</u>:

Las opciones de pago de [!DNL PayPal] y [!DNL Braintree] siguen visibles en el minicarrito y el carro de compras.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
