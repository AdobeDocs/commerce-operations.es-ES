---
title: "ACSD-54887: el carro de compras del cliente se borra después de que la sesión del cliente haya caducado"
description: Aplique el parche ACSD-54887 para corregir el problema de Adobe Commerce en el que se borra el carro de compras del cliente después de que la sesión del cliente haya caducado con [!UICONTROL Persistent Shopping Cart] habilitado.
feature: Shopping Cart
role: Admin, Developer
source-git-commit: 52742cbc2098958f8e4cddf8534e0c2bf79d5c3e
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---


# ACSD-54887: el carro de compras del cliente se borra después de que la sesión del cliente haya caducado

El parche ACSD-54887 corrige el problema por el que el carro de compras del cliente se borra después de que la sesión del cliente haya caducado con [!UICONTROL Persistent Shopping Cart] habilitado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50. El ID del parche es ACSD-54887. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p8, 2.4.5-p3 - 2.4.5-p7 y 2.4.6-p1 - 2.4.6-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El carro de compras del cliente se borra después de que la sesión del cliente caduque con [!UICONTROL Persistent Shopping Cart] habilitado.

<u>Pasos a seguir</u>:

1. Habilitar [!UICONTROL Persistent Shopping Cart]. Ir a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** = *Sí*.

   Iniciar sesión con Persistencia habilitada (Nota: No está disponible en la autorización emergente, pero solo en la página de [!UICONTROL Sign in] directa).

1. Añadir un producto al carro de compras.
1. Continúa con el proceso de pago y selecciona una forma de pago.
1. Caduca la sesión (elimina `PHPSESSID`).
1. Actualice la página. Observe que la cotización se convierte inmediatamente en una cotización de invitado porque ya se ha seleccionado un método de pago y se ha eliminado la cookie [!UICONTROL Persistent Cart].
1. Caduca la sesión (elimina `PHPSESSID`).
1. Actualice la página. Compruebe que el carro de compras esté vacío.
1. Inicie sesión de nuevo.

<u>Resultados esperados</u>:

El carrito tiene el producto cuando vuelves a iniciar sesión.

<u>Resultados reales</u>:

El carrito está vacío cuando se vuelve a iniciar sesión.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].

