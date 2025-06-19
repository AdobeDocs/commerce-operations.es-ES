---
title: 'ACSD-61348: elementos de la lista de deseos visibles a través de GraphQL pero no en la tienda'
description: Aplique el parche ACSD-61348 para corregir el problema de Adobe Commerce en el que los elementos de la lista de deseos son visibles a través de GraphQL, pero no en la tienda en un entorno de varios sitios web.
feature: Customers
role: Admin, Developer
exl-id: fcba2c28-077d-4663-b129-7da436e2791d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-61348: elementos de la lista de deseos visibles a través de GraphQL pero no en la tienda

El parche ACSD-61348 soluciona el problema de que los elementos de la lista de deseos son visibles a través de GraphQL, pero no en la tienda en un entorno de varios sitios web. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. El ID del parche es ACSD-61348. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6-p5

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los elementos de la lista de deseos son visibles a través de GraphQL, pero no en la tienda en un entorno de varios sitios web.

<u>Pasos a seguir</u>:

1. Configure dos sitios web.
1. Vaya a **[!UICONTROL Config Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** y establezca **[!UICONTROL Share Customer Accounts]** en *[!UICONTROL Global]*.
1. Vaya a **[!UICONTROL Config Customers]** > **[!UICONTROL Wishlist]** > **[!UICONTROL General Options]** y establezca **[!UICONTROL Enable Multiple Wish Lists]** en *Sí*.
1. Vaya a **[!UICONTROL Config General]** > **[!UICONTROL Web]** y establezca **[!UICONTROL Add Store Code to URLs]** en *Sí*.
1. Cree un producto simple y asígnelo al segundo sitio web.
1. Cree un cliente e inicie sesión.
1. Añadir un producto a la lista de deseos.
1. Asigne el producto al sitio web predeterminado.
1. Ir a la página *[!UICONTROL Wishlist]* en el sitio web predeterminado.

<u>Resultados esperados</u>:

El producto está en la lista de deseos.

<u>Resultados reales</u>:

No hay productos en la lista de deseos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
