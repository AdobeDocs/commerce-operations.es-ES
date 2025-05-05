---
title: 'ACSD-57337: el usuario administrador con restricciones de acceso puede ver todas las compañías en la cuadrícula Compañías'
description: Aplique el parche ACSD-57337 para solucionar el problema de Adobe Commerce, en el que un usuario administrador con restricciones de acceso a sitios web específicos puede ver compañías de todos los sitios web en la cuadrícula Compañías.
feature: Companies, B2B, Configuration
role: Admin, Developer
exl-id: 7a05d335-5ed8-460e-80c4-dbc51d06c5bd
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-57337: el usuario administrador con restricciones de acceso podría ver todas las compañías en la cuadrícula *Compañías*

El parche ACSD-57337 corrige el problema en el que un usuario administrador con restricciones de acceso a sitios web específicos podía ver compañías de todos los sitios web en la cuadrícula *Compañías*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48. El ID del parche es ACSD-57337. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un usuario administrador con restricciones de acceso a sitios web específicos podría ver compañías de todos los sitios web en la cuadrícula *Compañías*.

<u>Pasos a seguir</u>:

1. Cree un sitio web, una tienda y una vista de tienda adicionales.
1. Cree algunas empresas asignadas a distintos sitios web.
1. Cree una función de usuario administrador y establezca el ámbito de la función en el sitio web creado.
1. Cree un administrador y asígnelo a la función creada.
1. Inicie sesión con un nuevo administrador.
1. Abra **[!UICONTROL Customers]** > **[!UICONTROL Companies]** y observe la lista de compañías.

<u>Resultados esperados</u>:

Las compañías que se han asignado al sitio web adicional están visibles en la cuadrícula *Compañías*.

<u>Resultados reales</u>:

Todas las compañías están visibles en la cuadrícula *Compañías*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
