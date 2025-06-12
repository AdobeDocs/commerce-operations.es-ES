---
title: 'B2B-2674: Añade la capacidad de almacenamiento en caché a la consulta customAttributeMetadata de GraphQL'
description: Aplique el parche B2B-2674 para añadir la capacidad de almacenamiento en caché a la consulta customAttributeMetadata de GraphQL.
feature: Attributes, B2B, Cache, GraphQL
role: Admin
exl-id: b49633f3-b144-405f-a21d-726e222a7bfe
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# B2B-2674: Agrega la capacidad de almacenamiento en caché a la consulta de GraphQL `customAttributeMetadata`

El parche B2B-2674 agrega capacidad de almacenamiento en caché a las consultas de GraphQL `customAttributeMetadata`. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30. El ID del parche es B2B-2674. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7-beta1.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La consulta de GraphQL `customAttributeMetadata` no se puede almacenar en caché.

<u>Requisitos previos</u>:

* El servidor está apuntando a [!DNL Varnish] proxy al servidor back-end de Adobe Commerce.
* El ajuste de configuración `system/full_page_cache/caching_application` se ha establecido en *2* ([!DNL Varnish]), o bien vaya a Administración de Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > y establézcalo en [!DNL Varnish].

Una vez aplicado el parche, ejecute los siguientes pasos para asegurarse de que la capacidad de almacenamiento en caché ya esté disponible:

1. Envíe la solicitud `GET` a la consulta de GraphQL que se ha mencionado anteriormente, utilizando cualquier campo arbitrario.
1. Vuelva a enviar la solicitud sin ningún cambio; notará que es mucho más rápido. Tenga en cuenta que la solicitud no se envía al servidor, pero [!DNL Varnish] la gestiona completamente como una visita de caché.
1. Si se requieren más pruebas, comente el desajuste del encabezado `X-Magento-Debug` presente en nuestro [VCL](https://github.com/magento/magento2/blob/2.4-develop/app/code/Magento/PageCache/etc/varnish6.vcl#L239), luego reinicie [!DNL Varnish] y ejecute de nuevo los pasos anteriores.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
