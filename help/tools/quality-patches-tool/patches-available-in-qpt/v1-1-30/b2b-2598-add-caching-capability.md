---
title: 'B2B-2598: Añade la capacidad de almacenamiento en caché a storeConfig, moneda, país, países, availableStores y consultas de GraphQl'
description: Aplique el parche B2B-2598 para añadir la capacidad de almacenamiento en caché a las consultas de GraphQl storeConfig, currency, country, countries y availableStores.
feature: B2B, GraphQL, Cache
role: Admin
type: Troubleshooting
autotag-review: '2026-05-22T20:21:20.687Z'
TQID: 'https://experienceleague.adobe.com/DQWkSrUHcUhOTn3fWdnRPVQUK6jRkPGCAnIKPRHkebQ'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
industry_v2:
  - id: aad1e361-483a-40cf-9a88-144325515074
source-git-commit: 17c3f587a16209876a9713881eff0034d872581e
workflow-type: tm+mt
source-wordcount: 457
ht-degree: 0%

---

# B2B-2598: Agrega la capacidad de almacenamiento en caché a `storeConfig`, `currency`, `country`, `countries` y `availableStores` consultas de GraphQl

El parche B2B-2598 agrega capacidad de almacenamiento en caché a `storeConfig`, `currency`, `country`, `countries` y `availableStores` consultas de GraphQl. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30. El ID del parche es B2B-2598. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7-beta1.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool]


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool]
