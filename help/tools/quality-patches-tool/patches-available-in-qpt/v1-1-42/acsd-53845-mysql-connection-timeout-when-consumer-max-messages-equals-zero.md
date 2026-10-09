---
title: 'ACSD-53845: problema de tiempo de espera de conexión MySQL cuando el consumidor max_messages = 0'
description: Aplique el parche ACSD-53845 para corregir el problema de Adobe Commerce donde la conexión MySQL excede el tiempo de espera cuando el consumidor "max_messages = 0".
feature: REST, Configuration
role: Admin, Developer
exl-id: 437e29f4-b11a-466c-9928-3867821d2b8d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
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
source-wordcount: '353'
ht-degree: 0%
---
# ACSD-53845: problema de tiempo de espera de conexión MySQL cuando el consumidor `max_messages = 0`

El parche ACSD-53845 corrige el problema en el que la conexión MySQL se agota cuando el consumidor `max_messages = 0`. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.42. El ID del parche es ACSD-53845. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La conexión MySQL agota el tiempo de espera cuando el consumidor `max_messages = 0`.

Sin embargo, la conexión con la base de datos se restaurará al iniciar una transacción.

<u>Pasos a seguir</u>:

1. Envíe una solicitud para actualizar productos en lote mediante el extremo de la API REST `async/bulk/V1/products`.
1. Comprobar el estado en la tabla `magento_operation`.

<u>Resultados esperados</u>:

Los productos se han actualizado.

<u>Resultados reales</u>:

1. Se registra un error:

   ```yaml
   report.CRITICAL: Message has been rejected: SQLSTATE[HY000]: General error: 2006 MySQL server has gone away [] []
   ```

1. *status* para esta operación permanece *4* en la tabla `magento_operation`.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool]
* [Prácticas recomendadas para modificar tablas de base de datos](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
