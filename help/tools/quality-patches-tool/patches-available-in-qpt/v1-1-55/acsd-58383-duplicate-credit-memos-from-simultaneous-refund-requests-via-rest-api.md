---
title: 'ACSD-58383: duplicar notas de crédito de solicitudes de reembolso simultáneas a través de  [!DNL REST API]'
description: Aplique el parche ACSD-58383 para corregir el problema de Adobe Commerce donde al emitir un reembolso a través de  [!DNL REST API]  con dos solicitudes idénticas que se ejecutan simultáneamente, se crean notas de crédito duplicadas.
feature: REST, Payments, Returns
role: Admin, Developer
exl-id: 962970d5-22e7-4bdc-afa0-70e1fa21ecec
source-git-commit: 28390659fe180180c9b2c8d16239008a1f8a510b
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Parche de Adobe Commerce ACSD-58383: duplicar notas de abono de solicitudes de reembolso simultáneas a través de [!DNL REST API]

El parche ACSD-58383 corrige el problema en el que emitir un reembolso a través de [!DNL REST API] con dos solicitudes idénticas que se ejecutan simultáneamente, resulta en notas de crédito duplicadas.

Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. El ID del parche es ACSD-58383. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las notas de abono duplicadas son el resultado de dos reembolsos creados al mismo tiempo.

<u>Pasos a seguir</u>:

1. Configurar [!DNL Paypal Express] en Commerce [!UICONTROL Admin].
1. Establece la acción de pago en *Venta*.
1. Configure el IPN [!DNL PayPal] (notificación de pago instantáneo) en el sitio web de espacio aislado [!DNL PayPal].
1. Emitir reembolso en el sitio web de espacio aislado [!DNL PayPal].
1. Emular un mensaje IPN de [!DNL PayPal] con herramientas para desarrolladores. IPN debe crear un abono.
1. Crear un segundo abono usando una llamada de [!DNL API].

<u>Resultados esperados</u>:

Sólo se crea una nota de abono para el mismo artículo.


<u>Resultados reales</u>:

Se crean dos notas de abono para el mismo artículo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
