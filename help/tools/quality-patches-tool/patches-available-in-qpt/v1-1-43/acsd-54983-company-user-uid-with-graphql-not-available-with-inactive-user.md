---
title: 'ACSD-54983: El UID del usuario de la empresa con GraphQL no está disponible con el usuario inactivo'
description: Aplique el parche ACSD-54983 para corregir el problema de Adobe Commerce en el que no es posible obtener el UID del usuario de la empresa con la solicitud de GraphQL cuando el estado del usuario se establece en inactivo.
feature: GraphQL
role: Admin, Developer
exl-id: b188270f-5454-41c9-8370-f4c396095297
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54983: El UID del usuario de la empresa con GraphQL no está disponible con el usuario inactivo

El parche ACSD-54983 corrige el problema en el que no es posible obtener el UID del usuario de la empresa con la solicitud de GraphQL cuando el estado del usuario se establece en inactivo. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43. El ID del parche es ACSD-54983. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se puede obtener el usuario de la empresa UID con la solicitud de GraphQL cuando el estado del usuario se establece en inactivo.

<u>Pasos a seguir</u>:

1. Cree una compañía con un usuario administrador. Por ejemplo, company@test.com.
1. Crear un cliente nuevo.
1. Asigne el nuevo cliente a una compañía.
1. Obtener un **[!UICONTROL company admin token]**.
1. Usando **[!UICONTROL company admin token]**, recupere la estructura de la compañía. Consulte [Devolver la estructura de la empresa](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) en nuestra documentación para desarrolladores.
1. La respuesta contiene solamente *clientes ACTIVOS* con sus ID.
1. Actualice el usuario de la compañía a *INACTIVO*.
1. Recupere la estructura de la compañía de nuevo.

<u>Resultados esperados</u>:

Es posible obtener el UID del usuario de la empresa cuando el estado se establece en inactivo.

<u>Resultados reales</u>:

Los clientes inactivos no están en la lista. No se puede obtener el UID del usuario de la empresa cuando el estado se establece en inactivo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
