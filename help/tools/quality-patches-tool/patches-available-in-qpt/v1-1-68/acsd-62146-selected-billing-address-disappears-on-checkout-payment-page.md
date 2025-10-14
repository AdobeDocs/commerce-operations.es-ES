---
title: 'ACSD-62146: la dirección de facturación seleccionada desaparece en la página de pago de pago'
description: Aplique el parche ACSD-62146 para corregir el problema de Adobe Commerce en el que la dirección de facturación seleccionada desaparece en la página de pago de cierre de compra cuando la búsqueda de direcciones está habilitada y el límite de número de direcciones de cliente está establecido en 1.
feature: Customers, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: 3de3de80383372d0e3bec5485fd65b9d70fe8860
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# ACSD-62146: la dirección de facturación seleccionada desaparece en la página de pago de pago

El parche ACSD-62146 corrige el problema en el que la dirección de facturación seleccionada desaparece en la página de pago de cierre de compra cuando la búsqueda de direcciones está habilitada y [!UICONTROL Number of Customer Addresses Limit] está establecido en 1. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. El ID del parche es ACSD-62146. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La dirección de facturación seleccionada desaparece en la página de pago de cierre de compra cuando la búsqueda de direcciones está habilitada y **[!UICONTROL Number of Customer Addresses Limit]** está establecido en 1.

<u>Pasos a seguir</u>:

1. Para habilitar la búsqueda de direcciones, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.
1. Establezca **[!UICONTROL Number of Customer Addresses Limit]** en 1.
1. Cree un cliente de y añada dos direcciones diferentes.
1. Añada un producto al carro de compras y continúe con el cierre de compra.
1. Haga clic en **[!UICONTROL Change Address]** y utilice la ventana emergente para cambiar la dirección.
1. Seleccione Dirección 2 como dirección de envío.
1. Haga clic en **[!UICONTROL Next]** para continuar con el paso de pago.
1. Verifique que la dirección de facturación y envío sea la misma.
1. Actualiza la página sin realizar el pago.

<u>Resultados esperados</u>:

La dirección de envío es visible cuando las direcciones de facturación y envío son iguales.

<u>Resultados reales</u>:

La dirección de facturación predeterminada y la dirección de envío seleccionada no están visibles.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
