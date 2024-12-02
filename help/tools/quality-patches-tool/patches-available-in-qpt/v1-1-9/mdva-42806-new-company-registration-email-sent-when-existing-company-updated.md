---
title: 'MDVA-42806: Se envía un nuevo correo electrónico de registro de empresa cada vez que se actualiza la empresa existente'
description: El parche MDVA-42806 soluciona el problema de enviar un nuevo correo electrónico de registro de empresa cada vez que se actualiza una empresa existente mediante la API de REST. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9. El ID del parche es MDVA-42806. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: REST, B2B, Communications, Companies
role: Admin
exl-id: 4fc2ee54-d88b-4940-b6ac-e25ad61e5c66
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-42806: Se envía un nuevo correo electrónico de registro de empresa cada vez que se actualiza la empresa existente

El parche MDVA-42806 soluciona el problema de enviar un nuevo correo electrónico de registro de empresa cada vez que se actualiza una empresa existente mediante la API de REST. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9. El ID del parche es MDVA-42806. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se envía un nuevo correo electrónico de registro de empresa cada vez que se actualiza una empresa existente mediante la API de REST.

<u>Requisitos previos</u>:

Módulos B2B instalados.

<u>Pasos a seguir</u>:

1. Cree una cuenta de compañía.
1. Usar extremo `/V1&#x200B;/company&#x200B;/<company_id>`. Para actualizar la compañía creada, consulta [actualizar la compañía](https://developer.adobe.com/commerce/webapi/rest/b2b/company-object/#update-the-company) en nuestra documentación para desarrolladores. A continuación se muestra un ejemplo de carga útil:

```php
{
    "company": {
        "id": 2,
        "status": 1,
        "company_name": "Company",
        "company_email": "company@example.test",
        "street": [
            "Test"
        ],
        "city": "Test",
        "country_id": "US",
        "region_id": "1",
        "postcode": "12345",
        "telephone": "8009994301",
        "customer_group_id": 2,
        "sales_representative_id": 1,
        "super_user_id": 2
    }
}
```

<u>Resultados esperados</u>:

No se envía ningún correo electrónico que indique &quot;Nueva solicitud de registro de empresa&quot;, ya que la API está actualizando una empresa existente.

<u>Resultados reales</u>:

Cada vez que se envía la solicitud de API se envía un correo electrónico con el texto &quot;Nueva solicitud de registro de empresa&quot;.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
