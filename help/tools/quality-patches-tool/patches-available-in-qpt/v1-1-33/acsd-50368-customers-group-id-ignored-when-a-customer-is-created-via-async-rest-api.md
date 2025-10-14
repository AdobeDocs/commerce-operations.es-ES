---
title: 'ACSD-50368: se ignora el group_id de los clientes cuando se crea un cliente mediante la API de REST asincrónica o la API de REST asincrónica masiva'
description: Aplique el parche ACSD-50368 para corregir el problema de Adobe Commerce en el que el group_id de los clientes se ignora cuando se crea un cliente mediante la API de REST asíncrona o la API de REST asíncrona masiva.
feature: REST
role: Admin
exl-id: 1ca78717-2144-4410-a398-764864ee182f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-50368: se ignora el group_id de los clientes cuando se crea un cliente mediante la API de REST asincrónica o la API de REST asincrónica masiva

>[!NOTE]
>
>El parche ACSD-50368 está parcialmente obsoleto, ya que este problema se soluciona con el parche de seguridad obligatorio [APSB25-08](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08) para las versiones superiores a 2.4.4.

El parche ACSD-50368 corrige el problema en el que los clientes de group_id se ignoran cuando se crea un cliente mediante la API de REST asíncrona o la API de REST asíncrona masiva. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33. El ID del parche es ACSD-50368. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es>). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Customers group_id se ignora cuando se crea un cliente mediante la API de REST asincrónica o la API de REST asíncrona masiva.

<u>Requisitos previos</u>:

Configure RabbitMQ para procesar colas:

```
bin/magento setup:config:set --amqp-host=services --amqp-port=5672 --amqp-user=guest --amqp-password=guest 
bin/magento setup:upgrade --keep-generated
```

<u>Pasos a seguir</u>

1. Utilice una solicitud de API de REST asíncrona para crear un cliente:

   ```
   curl --location 'https://site.test/rest/default/async/V1/customers' \
   --header 'Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MiwiaWF0IjoxNjc5NDMzNzcxLCJleHAiOjE2Nzk0MzczNzF9.xau6KyILrkdCY_8K8aMlH4TmqcCXdH4Zcst_CLhdxYY' \
   --header 'Content-Type: application/json' \
   --header 'Cookie: PHPSESSID=844fltmqq1g15qe4ju3l00tiai' \
   --data-raw '{
       "customer": {
           "email": "foo@bar.test",
           "firstname": "Test",
           "lastname": "User",
           "group_id": 2
       }
   }
   ```

1. Se devuelve una respuesta similar:

   ```
   {
       "bulk_uuid": "b101ddcb-b7fd-4208-a2a6-2e84c9e61bcd",
       "request_items": [
           {
               "id": 0,
               "data_hash":   "6e718a93b02a30a98cb994d1c4e8cf1eeedcb962f384e4a463c"   ,
               "status": "accepted"
           }
       ],
       "errors": false
   }
   ```

1. Compruebe el estado de esta solicitud asincrónica:

   ```
   curl --location 'https://site.test/rest/default/V1/bulk/b101ddcb-b7fd-4208-a2a6-2e84c9e61bcd/detailed-status' \
   --header 'Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MiwiaWF0IjoxNjc5NDMzNzcxLCJleHAiOjE2Nzk0MzczNzF9.xau6KyILrkdCY_8K8aMlH4TmqcCXdH4Zcst_CLhdxYY' \
   --header 'Cookie: PHPSESSID=844fltmqq1g15qe4ju3l00tiai
   ```

<u>Resultados esperados</u>:

El group_id se establece correctamente en 2 para el nuevo cliente.

<u>Resultados reales</u>:

El group_id se establece en el valor predeterminado 1 para el nuevo cliente.

```
{
    "operations_list": [
        {
            "id": 0,
            "bulk_uuid": "b101ddcb-b7fd-4208-a2a6-2e84c9e61bcd",
            "topic_name": "async.magento.customer.api.accountmanagementinterface.createaccount.post",
            "serialized_data": null,
            "result_serialized_data": "{\"id\":4,\"group_id\":1,\"created_at\":\"2023-03-21 22:01:09\",\"updated_at\":\"2023-03-21 22:01:09\",\"created_in\":\"Default Store View\",\"email\":\"foo@bar.test\",\"firstname\":\"Test\",\"lastname\":\"User\",\"store_id\":1,\"website_id\":1,\"addresses\":[],\"disable_auto_group_change\":0,\"extension_attributes\":{\"is_subscribed\":false}}",
            "status": 1,
            "result_message": "Service execution success Magento\\Customer\\Model\\AccountManagement\\Interceptor::createAccount",
            "error_code": null
        }
    ],
        "user_type": 2,
        "bulk_id": "b101ddcb-b7fd-4208-a2a6-2e84c9e61bcd",
        "description": "Topic async.magento.customer.api.accountmanagementinterface.createaccount.post",
        "start_time": "2023-03-21 22:01:09",
        "user_id": 1,
        "operation_count": 1
}
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
