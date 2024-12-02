---
title: 'ACSD-56858: discrepancia en los permisos de funciones en el administrador de la empresa B2B'
description: Aplique el parche ACSD-56858 para corregir el problema de Adobe Commerce en el que los permisos de funciones se muestran incorrectamente para un administrador de empresa restringido en el entorno B2B.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: 28f90c8b-5d8b-4444-99ef-c91cfb5d6081
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-56858: discrepancia en los permisos de funciones en el administrador de la empresa B2B

El parche ACSD-56858 corrige el problema de que los permisos de funciones se muestran incorrectamente para un administrador de empresa restringido en el entorno B2B. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.47. El ID del parche es ACSD-56858. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los permisos de funciones para un administrador de empresa restringido en el entorno B2B se muestran de forma incorrecta.

<u>Pasos a seguir</u>:

1. Comience por configurar una empresa y agregar un administrador de empresa y usuarios de empresa.
1. Inicie sesión como administrador de la empresa en la tienda y cree varias funciones para distintos usuarios.
1. Asigne estas funciones según sea necesario, como limitar el acceso para algunas tareas y permitir el acceso completo para otras.
1. Asigne estas funciones con acceso completo a un usuario que no sea el administrador de la empresa.
1. Inicie sesión en un usuario que no sea administrador de la empresa, por ejemplo, un administrador de la empresa.
1. Vaya a **[!UICONTROL Roles and permission]** y edite el rol.
1. Observe que los permisos mostrados no coinciden con los permisos establecidos en la base de datos de la empresa para ese ID de rol.

<u>Resultados esperados</u>:

Los roles y los permisos aparecen correctamente para el usuario que no es administrador de la empresa.

<u>Resultados reales</u>:

Los roles no aparecen correctamente para el usuario administrador que no es de la empresa según los registros de la base de datos en la tabla de permisos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool]
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
