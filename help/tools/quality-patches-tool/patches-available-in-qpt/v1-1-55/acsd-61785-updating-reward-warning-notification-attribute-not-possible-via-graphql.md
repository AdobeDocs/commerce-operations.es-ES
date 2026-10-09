---
title: 'ACSD-61785: la actualización del atributo premio_advertencia_notificación no es posible mediante la mutación de GraphQL y las llamadas a la API REST'
description: Aplique el parche ACSD-61785 para solucionar el problema de Adobe Commerce donde la actualización del atributo "premio_advertencia_notificación" no es posible mediante la mutación de GraphQL y las llamadas a la API REST.
feature: REST, GraphQL, Rewards
role: Admin, Developer
exl-id: 41f40452-4240-4b4a-b1bc-0da23139f19f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4069cee6-4dc8-5a83-81de-232af6a7c9e9
    internal-label: Rewards
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
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
source-wordcount: '335'
ht-degree: 0%
---
# ACSD-61785: la actualización del atributo premio_advertencia_notificación no es posible mediante la mutación de GraphQL y las llamadas a la API REST

El parche ACSD-61785 corrige el problema en el cual la actualización del atributo `reward_warning_notification` no es posible mediante la mutación de GraphQL y las llamadas a la API REST. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. El ID del parche es ACSD-61785. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No es posible actualizar el atributo `reward_warning_notification` mediante la mutación de GraphQL y las llamadas a la API REST.

<u>Pasos a seguir</u>:

1. Consulte el esquema/documentación de la API de GraphQL y REST para *Suscribirse a las actualizaciones de saldo* y *Suscribirse a las notificaciones de caducidad de puntos*.

<u>Resultados esperados</u>:

Es posible suscribirse a *Actualizaciones de saldo de recompensas* y a *Notificaciones de caducidad de puntos* mediante GraphQL y la API de REST.

<u>Resultados reales</u>:

GraphQL y la API de REST carecen de esta funcionalidad.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
