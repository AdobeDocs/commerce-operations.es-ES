---
title: 'MDVA-39043: Los usuarios administradores reciben un error al añadir un widget a la página de CMS'
description: El parche MDVA-39043 corrige el problema en el que los usuarios administradores con acceso limitado obtienen un error al añadir el widget "Productos" a la página de CMS. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. El ID del parche es MDVA-39043. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: Admin Workspace, CMS, Products
role: Admin
exl-id: 82488249-cca3-4a28-bdc1-fa93a4c9dc2f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-39043: Los usuarios administradores reciben un error al añadir un widget a la página de CMS

El parche MDVA-39043 corrige el problema en el que los usuarios administradores con acceso limitado obtienen un error al añadir el widget &quot;Productos&quot; a la página de CMS. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. El ID del parche es MDVA-39043. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.4 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios administradores con acceso limitado obtienen un error al añadir el widget &quot;Productos&quot; a la página de CMS.

<u>Pasos a seguir</u>:

1. Inicie sesión en el servidor utilizando el administrador con acceso solo para editar contenido.
1. Vaya a **Contenido** > **Páginas**.
1. Abra cualquier página para editarla.
1. Edite el contenido con **Page Builder**.
1. Agregar el widget **Producto** de la sección **Agregar contenido**.
1. Haga clic en **Configurar** en el widget **Producto**.

<u>Resultados esperados</u>:

No se muestra ningún error.

<u>Resultados reales</u>:

Se recibe el siguiente mensaje de error:

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
