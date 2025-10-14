---
title: 'ACSD-49970: Gestión incorrecta de errores de GraphQL'
description: Aplique el parche ACSD-49970 para corregir el problema de Adobe Commerce en el que hay un control incorrecto de los errores de GraphQL cuando se activa [!UICONTROL New Relic Reporting].
feature: GraphQL, Observability
role: Admin
exl-id: f06f6cbf-ea85-406a-850d-f63e1001ff82
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-49970: Gestión incorrecta de errores de GraphQL

La revisión ACSD-49970 corrige el problema en el que hay un control incorrecto de los errores de GraphQL cuando se activa *[!UICONTROL New Relic Reporting]*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-49970. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La clave `GraphQLOperationNames` no se administra correctamente si `logDataHelper` contiene o no esta clave.

<u>Pasos a seguir</u>:

1. Ejecutar `bin/magento deploy:mode:set developer`.
1. Inicie sesión en Admin.
1. Habilitar **[!UICONTROL New Relic Integration]** desde **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]**
(Nota: Aunque se muestre un error que indica que la extensión [!DNL New Relic] no está disponible, la configuración se guardará).
1. Ejecute esta mutación de *GraphQL* en `http://yourMagentoDomain/graphql` desde el cliente *[!DNL Altair]* o desde cualquier otro cliente o a través de cURL.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (Nota: establezca **[!UICONTROL Header]** en [!UICONTROL Content-Currency:CA] antes de ejecutarlo).

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>Resultados esperados</u>:

No hay *500 excepción* en los registros, la clave `GraphQLOperationNames` se está administrando correctamente.

<u>Resultados reales</u>:

Hay una excepción *500* en los registros, la clave `GraphQLOperationNames` no se está gestionando correctamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
