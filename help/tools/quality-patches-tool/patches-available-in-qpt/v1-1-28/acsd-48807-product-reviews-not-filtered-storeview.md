---
title: 'ACSD-48807: Reseñas de productos no filtradas por storeview'
description: Aplique el parche ACSD-48807 para corregir el problema de Adobe Commerce en el que las críticas de productos no se filtran por la vista de tienda a través de GraphQL.
feature: Admin Workspace, Products
role: Admin
exl-id: ce2cf5a1-a650-4eaa-8caf-f34dd0111c36
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-48807: Reseñas de productos no filtradas por storeview

El parche ACSD-48807 corrige el problema en el que las críticas de productos no se filtran por la vista de tienda a través de GraphQL. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28. El ID del parche es ACSD-48807. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las críticas de productos no se filtran por la vista de tienda a través de GraphQL.

<u>Pasos a seguir</u>:

1. Cree una vista de tienda adicional.
1. Cree una cuenta de cliente e inicie sesión.
1. En la vista de tienda predeterminada, cree una revisión para un producto.
1. Cambie a otra vista de tienda y cree otra revisión para un producto.
1. Apruebe ambas revisiones en el administrador de Adobe Commerce.
1. Envíe una consulta de GraphQL al cliente para recuperar las críticas de producto mientras especifica la vista de tienda creada en el paso uno del encabezado.
1. Observe la respuesta.

<u>Resultados esperados</u>:

En la respuesta solo se devuelve la revisión del producto para la vista de tienda especificada.

<u>Resultados reales</u>:

Ambas revisiones se devuelven en la respuesta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
