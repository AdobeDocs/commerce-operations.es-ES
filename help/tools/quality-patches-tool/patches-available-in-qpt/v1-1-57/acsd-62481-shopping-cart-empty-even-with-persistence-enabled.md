---
title: 'ACSD-62481: el carro de compras permanece vacío incluso con [!UICONTROL Persistence] habilitado'
description: Aplique el parche ACSD-62481 para corregir el problema de Adobe Commerce en el que la función de carro persistente falla al utilizar la ventana emergente de inicio de sesión durante el cierre de compra.
feature: Shopping Cart, Checkout
role: Admin, Developer
source-git-commit: 27a98c42f2c514b3dd1a2f59c140b60b7ac26592
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---


# ACSD-62481: el carro de compras permanece vacío incluso con *[!UICONTROL Persistence]* habilitado

El parche ACSD-62481 corrige el problema en el que la función de carro de compras persistente falla al utilizar la ventana emergente de inicio de sesión durante el cierre de compra porque carece de la casilla de verificación *[!UICONTROL Remember Me]*, lo que provoca que los productos desaparezcan del carro de compras después de cerrar sesión. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. El ID del parche es ACSD-62481. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La característica de carro persistente falla al usar la ventana emergente de inicio de sesión durante la desprotección porque carece de la casilla de verificación *[!UICONTROL Remember Me]*. Esto hace que los productos desaparezcan del carro de compras después de cerrar la sesión.

<u>Pasos a seguir</u>:

1. En el administrador, configure la cuenta de invitado y la configuración del carro de compras persistente de la siguiente manera:

   * Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** y establezca *[!UICONTROL Allow Guest Checkout]* en *No*.

      * Haga clic en **[!UICONTROL Save Config]**.

   * Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** > **[!UICONTROL General Options]** y establezca *[!UICONTROL Enable Persistence]* en *Sí*.
   * Deje el resto de la configuración como predeterminada, pero cambie *[!UICONTROL Clear Persistence on Sign Out]* a *No*.

      * Haga clic en **[!UICONTROL Save Config]**.

1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add product]** para agregar un producto simple al catálogo.

   * Rellene los detalles mínimos necesarios y asegúrese de que esté disponible.

1. En el front-end, cree una cuenta de cliente con el formulario principal `(../customer/account/create/)` y cierre la sesión.
1. Añadir el producto al carro de compras como invitado.
1. Abra el minicarrito con el icono en la parte superior derecha y luego haga clic en **[!UICONTROL View and Edit Cart]**.
1. Continúe con el cierre de compra.
1. Inicie sesión en la nueva cuenta de cliente mediante el cuadro de diálogo emergente que aparece y cierre la sesión.

<u>Resultados esperados</u>:

El carro de compras conserva los productos del usuario que ha iniciado sesión anteriormente.

<u>Resultados reales</u>:

* El carro está vacío.
* El cuadro de diálogo de inicio de sesión emergente no muestra la opción *[!UICONTROL Remember Me]*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura en la nube: Actualizaciones y parches > Aplicar parches en la guía de Commerce en la infraestructura en la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
