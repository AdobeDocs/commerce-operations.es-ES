---
title: '"ACSD-51739: Error al solicitar "structure_id" en la solicitud de GraphQL de "CompanyTeam"'
description: Aplique el parche ACSD-51739 para solucionar el problema de Adobe Commerce donde se devuelve un error cuando se solicita structure_id en una solicitud de GraphQL de CompanyTeam.
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51739: error al solicitar `structure_id` en `CompanyTeam` solicitud de GraphQL

La revisión ACSD-51739 corrige el problema en el que se devuelve un error cuando se solicita `structure_id` en una solicitud GraphQL de `CompanyTeam`. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34. El ID del parche es ACSD-51739. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se devuelve un error cuando se solicita `structure_id` en una solicitud de GraphQL `CompanyTeam`.

<u>Pasos a seguir</u>

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** y establezca *[!UICONTROL Enable Company]* en *Sí*.
1. Cree una empresa junto con un usuario administrador de la empresa.
1. Cree un nuevo cliente (*customer1*) y asigne la compañía (creada anteriormente) a este cliente.
1. En el front-end, inicie sesión como el usuario administrador de la empresa.
1. Cree un equipo de empresa y asigne *cliente1* al equipo arrastrando y soltando.
1. Ejecute la siguiente consulta GraphQl de la empresa, que incluye `CompanyTeam` con `structure_id`:

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. Compruebe la respuesta de GraphQL.

<u>Resultados esperados</u>:

No se devuelve ningún error y todos los datos solicitados están presentes en la respuesta de GraphQL.

<u>Resultados reales</u>:

* La respuesta contiene un *error interno del servidor*.
* `var/log/exception.log` contiene:

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
