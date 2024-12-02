---
title: 'MDVA-40175: Los botones de opción no se muestran al reordenar'
description: El parche MDVA-40175 soluciona el problema de que los botones de opción no se muestran cuando los usuarios intentan reordenar. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10. El ID del parche es MDVA-40175. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
feature: Admin Workspace, Orders
role: Admin
exl-id: e84ff581-13ba-4f9f-9247-519b0b54807a
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-40175: Los botones de opción no se muestran al reordenar

El parche MDVA-40175 soluciona el problema de que los botones de opción no se muestran cuando los usuarios intentan reordenar. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10. El ID del parche es MDVA-40175. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los botones de opción no se muestran en la sección Información de pago y envío cuando los usuarios intentan realizar un nuevo pedido.

<u>Requisitos previos</u>:

1. Se crea una cuenta de cliente con una dirección de envío y una dirección de facturación.
1. Se crea un producto simple.
1. Se configuran varios métodos de entrega.
1. Se crea al menos un pedido.

<u>Pasos a seguir</u>:

1. Vaya al Panel de administración > **Ventas** > **Pedidos**.
1. Seleccione el pedido creado.
1. Haga clic en el vínculo **Ver**.
1. Haga clic en el botón **Reordenar**.
1. Desplácese hacia abajo en la página hasta la sección **Información de pago y envío**.
1. Haz clic en **Haz clic para cambiar el método de envío**.

<u>Resultados esperados</u>:

Aparece la lista de métodos de envío con botones de opción.

<u>Resultados reales</u>:

Aparece la lista de métodos de envío sin botones de opción.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
