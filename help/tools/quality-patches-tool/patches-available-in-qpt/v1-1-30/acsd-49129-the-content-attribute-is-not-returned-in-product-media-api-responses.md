---
title: 'ACSD-49129: Atributo "Contenido" no devuelto en las respuestas de API de medios del producto'
description: Aplique el parche ACSD-49129 para corregir el problema de Adobe Commerce en el que el atributo *content* (*código de imagen base64*) no se devuelve en las respuestas de API de medios de producto rest/V1/products/sku/media.
feature: REST, Attributes, Media, Page Content, Products
role: Admin
exl-id: 5235b7d1-4ebf-4cfb-8605-47614306a122
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-49129: Atributo &quot;Contenido&quot; no devuelto en las respuestas de API de medios del producto

El parche ACSD-49129 corrige el problema en el que el atributo *content* (*[!UICONTROL base64 image code]*) no se devuelve en las respuestas de la API de medios del producto `rest/V1/products/sku/media`. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.30. El ID del parche es ACSD-49129. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El atributo *content* (*[!UICONTROL base64 image code]*) no se devuelve en las respuestas de la API de medios del producto `rest/V1/products/sku/media`.

<u>Pasos a seguir</u>:

1. Cree un producto con una imagen.
1. Enviar *solicitud de API de REST de GET* a `rest/V1/products/<sku>/media` y `rest/V1/products/<sku>/media/<entryId>`.
1. Compruebe las respuestas de la API.

<u>Resultados esperados</u>

El atributo *content* con los datos está disponible a través de la API de REST.

<u>Resultados reales</u>

El atributo *content* no está presente en las respuestas de API.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
