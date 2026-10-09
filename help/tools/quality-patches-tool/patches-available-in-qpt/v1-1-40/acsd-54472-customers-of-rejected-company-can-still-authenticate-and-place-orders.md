---
title: 'ACSD-54472: los clientes de una compañía rechazada aún pueden autenticarse'
description: Aplique el parche ACSD-54472 para corregir el problema de Adobe Commerce en el que los clientes de una compañía rechazada aún pueden autenticarse y los clientes de una compañía bloqueada y rechazada pueden realizar pedidos.
feature: B2B
role: Admin, Developer
exl-id: c0bd960f-609b-4253-9fc8-dc47fbbddc93
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '473'
ht-degree: 0%
---
# ACSD-54472: los clientes de una compañía rechazada aún pueden autenticarse

El parche ACSD-54472 corrige el problema en el que los clientes de una compañía rechazada aún pueden autenticarse, y los clientes de una compañía bloqueada y rechazada aún pueden realizar pedidos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.40. El ID del parche es ACSD-54472. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los clientes de una compañía rechazada aún pueden autenticarse, y los clientes de una compañía bloqueada y rechazada pueden realizar pedidos.

<u>Pasos a seguir</u>:

1. Cree una empresa.
1. Agregar productos al carro de compras mediante [!DNL GraphQL].
1. Cambie el estado de la compañía a *Bloqueado*.
1. Envíe una solicitud [!DNL GraphQL] para realizar el pedido y crear una oferta negociable.
1. Cambie el estado de la compañía a *Rechazado*.
1. Envíe una solicitud [!DNL GraphQL] para obtener el token de autorización de usuario de la compañía.
1. Definir el estado del cliente en *Inactivo*.
1. Envíe una solicitud [!DNL GraphQL] para obtener el token de autorización de usuario de la compañía.

<u>Resultados esperados</u>:

* El usuario de la compañía *Bloqueada* no realiza el pedido ni la oferta negociable.
* No se obtuvo el token de autorización para el usuario de la compañía *Rechazada*.
* No se obtuvo el token de autorización para el cliente *Inactivo*.

<u>Resultados reales</u>:

* El pedido y la cotización negociable los hace el usuario de la compañía *Bloqueada*.
* Se obtuvo el token de autorización para el usuario de la compañía *Rechazada*.
* Se ha obtenido el token de autorización para el cliente *Inactivo*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
