---
title: 'ACSD-54472: los clientes de una compañía rechazada aún pueden autenticarse'
description: Aplique el parche ACSD-54472 para corregir el problema de Adobe Commerce en el que los clientes de una compañía rechazada aún pueden autenticarse y los clientes de una compañía bloqueada y rechazada pueden realizar pedidos.
feature: B2B
role: Admin, Developer
exl-id: c0bd960f-609b-4253-9fc8-dc47fbbddc93
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-54472: los clientes de una compañía rechazada aún pueden autenticarse

El parche ACSD-54472 corrige el problema en el que los clientes de una compañía rechazada aún pueden autenticarse, y los clientes de una compañía bloqueada y rechazada aún pueden realizar pedidos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40. El ID del parche es ACSD-54472. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
