---
title: 'ACSD-54026: Mensaje de error incorrecto para la solicitud de GraphQL updateCompanyRole'
description: Aplique el parche ACSD-54026 para corregir el problema de Adobe Commerce donde haya un mensaje de error incorrecto para una solicitud de GraphQL updateCompanyRole para un usuario no autorizado.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 21695333-5f18-48db-acde-246f269dd691
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54026: mensaje de error incorrecto para la solicitud de GraphQL `updateCompanyRole`

La revisión ACSD-54026 corrige el problema donde hay un mensaje de error incorrecto para una solicitud de GraphQL de `updateCompanyRole` para un usuario no autorizado. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.39. El ID del parche es ACSD-54026. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Obteniendo un mensaje de error incorrecto para una solicitud de GraphQL de `updateCompanyRole` para un usuario no autorizado.

<u>Pasos a seguir</u>:

1. Habilite la empresa B2B en la configuración.
1. Cree una empresa.
1. Envíe una solicitud de GraphQL `updateCompanyRole` sin pasar un token de portador o con un token de portador no válido.
1. Observe el mensaje de error en la respuesta de GraphQL.

<u>Resultados esperados</u>:

Recibe el siguiente mensaje de error: *El cliente actual no está autorizado.*

<u>Resultados reales</u>:

Recibe el siguiente mensaje de error: *El cliente no es un usuario de la compañía.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
