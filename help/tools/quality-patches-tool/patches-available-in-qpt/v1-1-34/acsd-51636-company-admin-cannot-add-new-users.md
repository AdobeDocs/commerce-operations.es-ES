---
title: 'ACSD-51636: el administrador de la empresa no puede agregar nuevos usuarios desde la sección de cuenta de cliente'
description: Aplique el parche ACSD-51636 para solucionar el problema de Adobe Commerce en el que el administrador de la empresa no puede agregar nuevos usuarios desde la sección de cuenta de cliente a pesar de tener todas las funciones y permisos necesarios.
feature: Admin Workspace, B2B, Companies, Customer Service
role: Admin
exl-id: 46e79ae3-ea24-4cb2-b06e-e82cec33b16c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-51636: el administrador de la empresa no puede agregar nuevos usuarios desde la sección de cuenta de cliente

El parche ACSD-51636 corrige el problema en el que el administrador de la empresa no puede agregar nuevos usuarios desde la sección de cuenta de cliente a pesar de tener todas las funciones y permisos necesarios. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34. El ID del parche es ACSD-51636. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El administrador de la empresa no puede agregar nuevos usuarios desde la sección de cuenta de cliente a pesar de tener todas las funciones y permisos necesarios.

Requisitos previos:

* El módulo B2B está instalado.
* La funcionalidad de la empresa está habilitada.

<u>Pasos a seguir</u>:

1. Cree una nueva compañía.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Editar el tipo **[!UICONTROL Company Admin]** en *Cliente*.
1. Inicie sesión como cliente.
1. Vaya a **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** > **[!UICONTROL Add User]** y agregue detalles para el usuario y actívelo.
1. Guarde el nuevo usuario.

<u>Resultados esperados</u>

El usuario administrador puede agregar un nuevo usuario.

<u>Resultados reales</u>

* El usuario administrador recibe un mensaje de error: *Se produjo un error*.
* El usuario administrador no puede crear un cliente nuevo.
* El registro contiene el siguiente error:

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es>) en la guía [!DNL Quality Patches Tool].
