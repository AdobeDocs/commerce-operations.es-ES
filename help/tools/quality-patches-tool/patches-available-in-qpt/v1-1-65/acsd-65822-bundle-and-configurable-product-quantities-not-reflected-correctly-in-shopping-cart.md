---
title: 'ACSD-65822: las cantidades de productos agrupados y configurables no se reflejan correctamente en el carro de compras'
description: Aplique el parche ACSD-65822 para solucionar el problema de Adobe Commerce, donde la cantidad aparecía como 0 en la sección del carro de compras del cliente en el panel de administración al añadir productos agrupados.
feature: Admin Workspace, Checkout, Orders
role: Admin, Developer
source-git-commit: d8421ba07a5d2fa3a3174541ed8cd6a2bc76f157
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# ACSD-65822: las cantidades de producto configurables y del paquete no se reflejan correctamente en [!UICONTROL Shopping Cart]

La revisión ACSD-65822 corrige el problema en el que las cantidades de paquetes y productos configurables no se muestran correctamente en la sección **[!UICONTROL Shopping Cart]** en *[!UICONTROL Customer's Activities]*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. El ID del parche es ACSD-65822. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las cantidades de paquetes y productos configurables no se muestran correctamente en la sección **[!UICONTROL Shopping Cart]** en *[!UICONTROL Customer's Activities]*.

<u>Pasos a seguir</u>:

1. Cree un usuario en la tienda.
2. Crear un(a) **[!UICONTROL Bundle product]** en el panel de administración.
3. En la tienda, como usuario que ha iniciado sesión, añada el producto del paquete al carro de compras con una cantidad especificada.
4. En el panel *Administrador*, vaya a **[!UICONTROL Customers]** y haga clic en **[!UICONTROL Edit]** para el cliente creado en el paso 1.
5. Haga clic en **[!UICONTROL Create Order]**.
6. En el lado izquierdo, debajo de *[!UICONTROL Customer's Activities]*, marque la sección **[!UICONTROL Shopping Cart]**. Debería ver el producto agrupado junto con la cantidad seleccionada.

<u>Resultados esperados</u>:

La cantidad del artículo del paquete debe coincidir con la cantidad mostrada en la tienda.

<u>Resultados reales</u>:

La cantidad de artículos agrupados se muestra como 0.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
