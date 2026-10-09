---
title: 'ACSD-53204: * El producto no se puede guardar * error en solicitudes simultáneas para añadir imágenes a la galería'
description: Aplique el parche ACSD-53204 para corregir el problema de Adobe Commerce en el que se produce el error *El producto no se puede guardar* al realizar solicitudes simultáneas para agregar imágenes a la galería de productos mediante el punto final rest/V1/products/<sku>/media.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: 7fdf41e5-46ef-4505-b8ce-c330bd899fa1
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '411'
ht-degree: 0%
---
# ACSD-53204: Error &quot;*El producto no se puede guardar*&quot; en solicitudes simultáneas para agregar imágenes a la galería

La revisión ACSD-53204 corrige el problema en el que se produce el error &quot;*El producto no se puede guardar*&quot; al realizar solicitudes simultáneas para agregar imágenes a la galería de productos mediante el extremo `rest/V1/products/<sku>/media`. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.39. El ID del parche es ACSD-53204. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Error &quot;*El producto no se puede guardar*&quot; al realizar solicitudes simultáneas para agregar imágenes a la galería de productos mediante el extremo `rest/V1/products/<sku>/media`.

<u>Pasos a seguir</u>:

1. Inicie sesión en el panel de administración.
1. Cree un producto con el SKU p1.
1. Realice varias solicitudes simultáneas al extremo `rest/V1/products/<sku>/media` para cargar varias imágenes simultáneamente.

<u>Resultados esperados</u>:

Las imágenes se guardan sin errores.

<u>Resultados reales</u>:

El error &quot;*El producto no se puede guardar*&quot; se devuelve de vez en cuando.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
