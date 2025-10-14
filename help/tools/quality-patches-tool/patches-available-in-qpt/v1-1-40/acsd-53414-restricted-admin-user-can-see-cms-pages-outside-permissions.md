---
title: 'ACSD-53414: los usuarios administradores restringidos pueden ver páginas de CMS fuera de su ámbito de permisos'
description: Aplique el parche ACSD-53414 para corregir el problema de Adobe Commerce en el que un usuario administrador restringido puede ver páginas de CMS fuera de su ámbito de permisos.
feature: CMS
role: Admin, Developer
exl-id: 86658336-679b-4fe0-9d26-56064ff0c604
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-53414: los usuarios administradores restringidos pueden ver páginas de CMS fuera de su ámbito de permisos

El parche ACSD-53414 corrige el problema en el que un usuario administrador restringido puede ver páginas de CMS fuera de su ámbito de permisos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40. El ID del parche es ACSD-53414. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios administradores restringidos pueden ver páginas de CMS más allá de su ámbito de permisos.

<u>Pasos a seguir</u>:

1. Cree un nuevo sitio web (sub_website), tienda (sub_store) y vista de tienda (sub_storeview).
1. Cree una función sub_expert, que permita el ámbito de sub_website y sub_store. Asigne solo los permisos siguientes: [!UICONTROL Dashboard] y [!UICONTROL Pages].
1. Cree un nuevo usuario administrador y asígnelo al rol sub_expert.
1. Asigne las siguientes páginas de CSM a la vista de subtienda y a la vista de tienda predeterminada.

   * [!UICONTROL 404 Not Found] > Vista de subtienda
   * [!UICONTROL 503 Service Unavailable] > Vista de tienda predeterminada

1. Inicie sesión en el administrador con el usuario administrador creado en el paso 3.
1. Compruebe la cuadrícula de la página de CMS.

<u>Resultados esperados</u>:

La página *[!UICONTROL 503 Service Unavailable]* no es visible para el administrador web.

<u>Resultados reales</u>:

*[!UICONTROL 503 Service Unavailable]* es visible para el administrador web.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
