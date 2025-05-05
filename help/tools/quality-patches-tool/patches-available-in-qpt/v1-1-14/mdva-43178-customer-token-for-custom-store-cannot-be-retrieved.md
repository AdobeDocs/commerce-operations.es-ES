---
title: 'MDVA-43178: el token de cliente para la tienda personalizada no se puede recuperar en GraphQL'
description: El parche MDVA-43178 corrige el problema en el que el token de cliente para una tienda personalizada no se puede recuperar en GraphQL. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14. El ID del parche es MDVA-43178. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: GraphQL
role: Admin
exl-id: 8dd9c9e7-573c-4c7a-8fd0-3b3886649af3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-43178: el token de cliente para la tienda personalizada no se puede recuperar en GraphQL

El parche MDVA-43178 corrige el problema en el que el token de cliente para una tienda personalizada no se puede recuperar en GraphQL. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14. El ID del parche es MDVA-43178. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El token de cliente de una tienda personalizada no se puede recuperar en GraphQL.

<u>Pasos a seguir</u>:

1. Cree dos vistas de tienda para la tienda predeterminada.
1. Crear un sitio web, una tienda y una vista de tienda nuevos. Asigne a esta vista de tienda el nombre &quot;test3&quot;.
1. Cree un cliente para el nuevo sitio web.
1. Generar token de administración de API:

   `http://domain/rest/all/V1/integration/admin/token`

   <pre>
    <code class="language-graphql">
    &lbrace;
      "username": "login",
      "password": "password"
    &rbrace;
    </code>
    </pre>

1. Envíe GraphQL para recuperar el token de cliente como administrador y utilice el token de administrador para la autorización. En el encabezado, &quot;store&quot; = &quot;test3&quot;:

   <pre>
    <customer_email>
      </pre>

<u>Resultados esperados</u>:

Se genera el token del cliente.

<u>Resultados reales</u>:

No se ha generado el token de cliente. Los comerciantes reciben *el correo electrónico del cliente proporcionado no existe* en respuesta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
