---
title: 'ACSD-61103: el recuento de errores no se restablece a cero después del inicio de sesión correcto del cliente mediante la API'
description: Aplique el parche ACSD-61103 para corregir el problema de Adobe Commerce en el que el recuento de errores de la tabla customer_entity no se restablece a cero después de que un cliente inicie sesión correctamente a través de los extremos de la API.
feature: GraphQL, REST, Customers
role: Admin, Developer
exl-id: 9f5aac1f-c8a3-4255-8ebc-2268283b3384
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
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
source-wordcount: '398'
ht-degree: 0%
---
# ACSD-61103: el recuento de errores no se restablece a cero después del inicio de sesión correcto del cliente mediante la API

El parche ACSD-61103 resuelve el problema en el que el recuento de errores de la tabla `customer_entity` no se restablece a cero después de que un cliente inicie sesión correctamente a través de los extremos de la API. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. El ID del parche es ACSD-61103. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El recuento de errores de la tabla `customer_entity` no se restablece a cero incluso después de que un cliente inicie sesión correctamente a través de los extremos de la API.

<u>Pasos a seguir</u>:

1. Cree una cuenta de cliente.
1. Generar un token de cliente mediante API con detalles incorrectos.
1. Compruebe la columna `failures_num` en la tabla de la base de datos `customer_entity` para el cliente anterior.
1. Genere un token de cliente mediante API con los detalles correctos.
1. Compruebe la columna `failures_num` en la tabla de la base de datos `customer_entity` para el cliente anterior.

<u>Resultados esperados</u>:

La columna `failures_num` debe restablecerse a 0 después de usar las credenciales correctas para generar un token de cliente mediante API.

<u>Resultados reales</u>:

La columna `failures_num` no se restablece a 0 después de usar las credenciales correctas para generar un token de cliente mediante API.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
