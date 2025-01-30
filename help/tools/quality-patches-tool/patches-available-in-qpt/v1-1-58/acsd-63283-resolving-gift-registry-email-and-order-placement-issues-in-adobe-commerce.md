---
title: 'ACSD-63283: resolución de [!UICONTROL Gift Registry] problemas de correo electrónico y ubicación de pedidos en Adobe Commerce'
description: Aplique el parche ACSD-63283 para corregir el problema de Adobe Commerce en el que al ordenar elementos de [!UICONTROL Gift Registry] se produce una excepción y se garantiza que [!UICONTROL Gift Registry Updates] incluya solo los elementos correctos.
feature: Gift, Shopping Cart
role: Admin, Developer
source-git-commit: a9dd031ba004954074a0551315e80a2bd733f690
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-63283: resolución de [!UICONTROL Gift Registry] problemas de correo electrónico y ubicación de pedidos en Adobe Commerce

La revisión ACSD-63283 corrige el problema en el que al ordenar elementos de [!UICONTROL Gift Registry] se produce una excepción y se garantiza que [!UICONTROL Gift Registry Updates] incluya únicamente los elementos correctos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. El ID del parche es ACSD-63283. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

>[!NOTE]
>Este parche reemplaza y amplía el parche QPT [ACSD-56280](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-44/acsd-56280-gift-registry-purchases-are-not-completed).

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La funcionalidad [!UICONTROL Gift Registry] de Adobe Commerce se ve afectada por dos problemas importantes:

* Cuando un cliente realiza un pedido de elementos de su [!UICONTROL Gift Registry], el proceso falla debido a que se activa una excepción.
* Además, el correo electrónico de [!UICONTROL Gift Registry Updates] enviado al propietario del Registro incluye incorrectamente elementos de todos los registros de regalos, en lugar de restringir las actualizaciones a los elementos del Registro específico que se está actualizando.

<u>Pasos a seguir</u>:

1. Cree dos productos: producto A y producto B.
1. Cree dos clientes: cliente A y cliente B.
1. Inicie sesión como cliente A y cree un nuevo [!UICONTROL Gift Registry].
1. Vaya a la página de producto A y agréguela a [!UICONTROL Wishlist]. Abra [!UICONTROL Wishlist Page] y mueva el producto A a [!UICONTROL Gift Registry] mediante [!UICONTROL Add to Gift Registry].
1. Inicie sesión como cliente B, cree un nuevo(a) [!UICONTROL Gift Registry] y agréguele el producto B.
1. Como cliente B, comparta [!UICONTROL Gift Registry] por correo electrónico: **[!UICONTROL My Account]> [!UICONTROL Gift Registry] >[!UICONTROL Share]**.
1. Cierre la sesión del cliente B.
1. Haga clic en el vínculo recibido en el correo electrónico. Agregue el producto B a [!UICONTROL Cart] y haga un pedido.

<u>Resultados esperados</u>:

El cliente B recibe el correo electrónico con artículos actualizados solo desde su registro de regalos.

<u>Resultados reales</u>:

El cliente B recibe el correo electrónico con artículos de todos los registros de regalos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
