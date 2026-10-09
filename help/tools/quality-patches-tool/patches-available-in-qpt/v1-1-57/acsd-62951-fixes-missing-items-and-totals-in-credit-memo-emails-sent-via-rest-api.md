---
title: 'ACSD-62951: corrige los elementos y totales que faltan en [!UICONTROL Credit Memo] correos electrónicos enviados mediante la API de REST'
description: Aplique el parche ACSD-62951 para solucionar el problema de Adobe Commerce donde se envía el correo electrónico [!UICONTROL Credit Memo] sin incluir los elementos y totales del pedido.
feature: REST
role: Admin, Developer
exl-id: e0c6d4c1-ecaf-46e7-af2d-05a148970d71
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%
---
# ACSD-62951: corrige los elementos y totales que faltan en *[!UICONTROL Credit Memo]* correos electrónicos enviados mediante la API de REST

El parche ACSD-62951 corrige el problema por el que se envía el correo electrónico [!UICONTROL Credit Memo] sin incluir los elementos y totales del pedido. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. El ID del parche es ACSD-62951. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.5-p10

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El correo electrónico *[!UICONTROL Credit Memo]* enviado cuando se crea un abono a través de la API de REST `POST V1/order/:orderId/refund` no incluye los elementos y totales del pedido.

<u>Pasos a seguir</u>:

1. Cree un pedido con cualquier producto.
1. Enviar y facturar el pedido. Asegúrese de que se envía el correo electrónico de la factura e incluya los detalles del producto.
1. Genere un token de administrador mediante el cliente de API.
1. Utilice el token para crear un abono a través de la API de REST.
   1. Extremo: `POST V1/order/:orderId/refund`
   1. Solicitar carga útil:

      ```json
      {  
          "notify": true,  
          "items": [  
              {  
                  "order_item_id": 1,  
                  "qty": 1  
              }  
          ]  
      }  
      ```

<u>Resultados esperados</u>:

El correo electrónico *[!UICONTROL Credit Memo]* debe incluir los elementos y totales reembolsados

<u>Resultados reales</u>:

El correo electrónico *[!UICONTROL Credit Memo]* no contiene elementos ni totales, por lo que la información resultante es incompleta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
