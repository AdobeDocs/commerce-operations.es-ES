---
title: 'ACSD-47027: actualización lenta de la consulta B2B [!UICONTROL CompanyRole] [!DNL GraphQL] '
description: Aplique el parche ACSD-47027 para corregir el problema de Adobe Commerce en el que haya una actualización B2B [!UICONTROL CompanyRole] [!DNL GraphQL]  de consulta lenta.
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
exl-id: 91eb0297-1ba8-47b7-9581-29bee835843c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-47027: actualización lenta de la consulta B2B [!UICONTROL CompanyRole] [!DNL GraphQL]

El parche ACSD-47027 resuelve el problema en el que la actualización lenta de la consulta B2B [!UICONTROL CompanyRole] [!DNL GraphQL] no funciona como se esperaba. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23. El ID del parche es ACSD-47027. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La actualización de la consulta lenta B2B [!UICONTROL CompanyRole] [!DNL GraphQL] no funciona como se esperaba.

<u>Requisitos previos</u>:

Instale el módulo B2B.

<u>Pasos a seguir</u>:

1. En Adobe Commerce Admin, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** y establezca **[!UICONTROL Enable Company]** en _Sí_.
1. Vaya al front-end y cree una compañía.
1. Después de iniciar sesión como usuario de la compañía, vaya a **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** y agregue una función nueva.
1. Habilitar el registro de consultas [!UICONTROL dev] mediante `bin/magento dev:que:enab`.
1. Ahora envíe la siguiente solicitud [!DNL GraphQL] (el ID es el ID de rol codificado [!UICONTROL base64]):

   <pre><code>
   mutation &lbrace;
   updateCompanyRole(
      input: &lbrace;
         id: "Mg=="
         permissions: &lbrack;
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        &rbrack;
      &rbrace;
    ) &lbrace;
      role &lbrace;
         id

         name

         permissions &lbrace;
         id

         text

         children &lbrace;
            id

            text

            children &lbrace;
               id

               text
             &rbrace;
           &rbrace;
         &rbrace;
       &rbrace;
     &rbrace;
   &rbrace;
   </code></pre>

1. Compruebe el registro de consultas.
1. Puede ver que se ejecuta la consulta anterior. Esta consulta se ejecuta en `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Resultados esperados</u>:

`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` debe optimizarse para evitar cargar todos los datos disponibles en la tabla de base de datos **[!UICONTROL company_permissions]**.

<u>Resultados reales</u>:

Adobe Commerce ejecuta una consulta sin ningún filtro. Cuando hay un gran número de registros, Adobe Commerce tarda mucho tiempo en preparar la recopilación de datos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube. 

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
