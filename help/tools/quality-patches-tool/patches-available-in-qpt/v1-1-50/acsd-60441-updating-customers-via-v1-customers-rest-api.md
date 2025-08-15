---
title: 'ACSD-60441: La actualización de clientes a través de V1/customers [!DNL REST] extremo de API genera un error'
description: Aplique el parche ACSD-60441 para solucionar el problema de Adobe Commerce donde la actualización de clientes a través de la API V1/customers [!DNL REST] al utilizar el token de acceso de integración generado desde el back-end genera un error.
feature: REST, Customers
role: Admin, Developer
exl-id: 3936c065-41a6-4860-8313-e054f9b23ac7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-60441: La actualización de clientes a través del extremo de API `V1/customers` [!DNL REST] genera un error

El parche ACSD-60441 corrige el problema en el que la actualización de clientes a través de la API `V1/customers` [!DNL REST] al utilizar el token de acceso de integración generado desde el servidor provoca un error. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50. El ID del parche es ACSD-60441. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p8

**Compatible con versiones de Adobe Commerce**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p9, 2.4.5-p8, 2.4.6-p6, 2.4.7-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La actualización de clientes a través del extremo de API `V1/customers` [!DNL REST] al utilizar el token de acceso de integración generado desde el backend genera un error.

<u>Pasos a seguir</u>:

1. Cree una integración desde el administrador.
1. Enviar una solicitud [!DNL POST] a `rest/default/V1/customers/<customer_id>` mediante el token de integración.

   ```json
   {
     "customer": {
       "email": "roni_cost@example.com",
       "firstname": "Veronica",
       "lastname": "Costello"
     }
   }
   ```

<u>Resultados esperados</u>:

Se actualizan los datos del cliente.

<u>Resultados reales</u>:

Se obtiene el siguiente error:

    &quot;json
    &lbrace;
    &quot;message&quot;: &quot;Ya existe un cliente con la misma dirección de correo electrónico en un sitio web asociado.&quot;,
    &quot;trace&quot;: ...
    &rbrace;
    &quot;

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
