---
title: "ACSD-49013: confirmación por correo electrónico no traducida a la configuración regional del sitio web"
description: Aplique el parche ACSD-49013 para corregir el problema de Adobe Commerce en el que la confirmación por correo electrónico no se traduce a la configuración regional del sitio web al crear clientes mediante una API masiva.
feature: Admin Workspace, Communications
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-49013: confirmación por correo electrónico no traducida a la configuración regional del sitio web

El parche ACSD-49013 corrige el problema en el que la confirmación por correo electrónico no se traduce a la configuración regional del sitio web al crear clientes mediante una API masiva. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27. El ID del parche es ACSD-49013. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La confirmación por correo electrónico no se traduce a la configuración regional del sitio web al crear clientes mediante una API masiva.

<u>Pasos a seguir</u>:

1. Instale una configuración regional diferente como `de_DE`.
1. Configurar *RabbitMQ*.
1. Ejecute `bin/magento setup:upgrade` para instalar las colas en RabbitMQ y configurar el paquete de idioma.
1. Crear un sitio web adicional en [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Establezca la configuración regional de este nuevo sitio web en `de_DE` en [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale Options]**.
1. Ejecute una llamada de API para crear una cuenta de cliente mediante una API masiva. Usar el(la) `website_id` correspondiente.

   `Endpoint: /rest/async/bulk/V1/customers`

   ```
   [{
       "customer": {
       "email": "test@example.com",
       "firstname": "test",
       "lastname": "test",
       "website_id": 2
       },
       "password": "Passw0rd!"
   }]
   ```

1. Ejecutar `bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10`.
1. Puede ver que la cuenta de cliente se ha creado correctamente en el sitio web especificado.
1. Compruebe el correo electrónico recibido para el registro de clientes.

<u>Resultados esperados</u>:

Dado que el cliente se crea en un sitio web especificado, el correo electrónico de registro se envía utilizando la configuración regional de ese sitio web.

<u>Resultados reales</u>:

El cliente se crea correctamente en el sitio web especificado, pero el correo electrónico de registro se envía mediante la configuración regional predeterminada cuando se utiliza la API en bloque.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
