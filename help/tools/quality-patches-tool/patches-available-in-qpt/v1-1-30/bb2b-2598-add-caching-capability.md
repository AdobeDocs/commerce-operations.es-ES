---
title: "BB2B-2598: agrega capacidad de almacenamiento en caché a storeConfig, currency, country, countries, availableStores y consultas de GraphQl"
description: Aplique el parche BB2B-2598 para añadir la capacidad de almacenamiento en caché a las consultas storeConfig, currency, country, countries y availableStores de GraphQl.
feature: B2B, GraphQL, Cache
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# BB2B-2598: Agrega capacidad de almacenamiento en caché a `storeConfig`, `currency`, `country`, `countries` y `availableStores` consultas de GraphQl

El parche BB2B-2598 agrega capacidad de almacenamiento en caché a `storeConfig`, `currency`, `country`, `countries` y `availableStores` consultas de GraphQl. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30. El ID del parche es BB2B-2598. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7-beta1.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las consultas de GraphQL `availableStores`, `countries`, `country`, `currency`, `storeConfig` y `customAttributeMetadata` no se pueden almacenar en caché.

<u>Requisitos previos</u>:

* El servidor está apuntando a [!DNL Varnish] proxy al servidor back-end de Adobe Commerce.
* El ajuste de configuración `system/full_page_cache/caching_application` se ha establecido en *2* ([!DNL Varnish]), o bien vaya a Administración de Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > y establézcalo en [!DNL Varnish].

Una vez aplicado el parche, ejecute los siguientes pasos para asegurarse de que la capacidad de almacenamiento en caché ya esté disponible:

1. Envíe la solicitud `GET` a cualquiera de las consultas de GraphQL enumeradas anteriormente, utilizando cualquier campo arbitrario.
1. Vuelva a enviar la solicitud sin ningún cambio; notará que es mucho más rápido. Tenga en cuenta que la solicitud no se envía al servidor, pero [!DNL Varnish] la gestiona completamente como una visita de caché.
1. Si se requieren más pruebas, comente el desajuste del encabezado `X-Magento-Debug` presente en nuestro [VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227), luego reinicie [!DNL Varnish] y ejecute de nuevo los pasos anteriores.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
