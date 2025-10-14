---
title: 'ACSD-66179: si se cancela una factura con el tipo de pago [!UICONTROL Not Capture], se generará una página de error 404'
description: Aplique el parche ACSD-66179 para corregir el problema de Adobe Commerce en el que la cancelación de una factura con el tipo de pago [!UICONTROL Not Capture] provocó una página de error 404.
feature: Orders, Payments
role: Admin, Developer
type: Troubleshooting
exl-id: a7c1827d-fe28-40e2-9ec6-a04b4a5d33ee
source-git-commit: a35beeb278ac3b72701c54ac7727fd5423e687e7
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-66179: si se cancela una factura con el tipo de pago [!UICONTROL Not Capture], se generará una página de error 404

La revisión ACSD-66179 corrige el problema en el cual la cancelación de una factura creada con el tipo de pago *[!UICONTROL Not Capture]* resultaba en una página de error 404. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. El ID del parche es ACSD-66179. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p11 - 2.4.4-p14, 2.4.5-p10 - 2.4.5-p13, 2.4.6-p8 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Si se cancela una factura creada con el tipo de pago *[!UICONTROL Not Capture]*, aparecerá una página de error 404.

<u>Pasos a seguir</u>:

1. Crea un pedido con una forma de pago como Pago y envío por PayPal Express.
1. Crear una factura. Establezca **[!UICONTROL Amount]** en *[!UICONTROL Not Capture]* y envíe la factura.
1. Abra la factura creada y seleccione **[!UICONTROL Cancel]**.

<u>Resultados esperados</u>:

1. La factura se ha cancelado correctamente.
1. Se muestra un mensaje de éxito: *Ha cancelado la factura.*

<u>Resultados reales</u>:

Se muestra una página de error 404: *Página no encontrada.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
