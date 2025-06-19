---
title: 'MDVA-40619: Los cambios de jerarquía rompen la edición en línea de la página de CMS y generan un error 500'
description: El parche MDVA-40619 resuelve el problema en el que los cambios en la jerarquía de páginas de CMS rompen la edición en línea de la página de CMS y emiten "Error 500". Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. El ID del parche es MDVA-40619. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: CMS
role: Admin
exl-id: 148cb0a5-5a6c-4cfa-bf95-4bafc57beec6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-40619: Los cambios de jerarquía rompen la edición en línea de la página de CMS y generan un error 500

El parche MDVA-40619 resuelve el problema en el que los cambios en la jerarquía de páginas de CMS rompen la edición en línea de la página de CMS y emiten &quot;Error 500&quot;. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. El ID del parche es MDVA-40619. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los cambios en la jerarquía de páginas de CMS rompen la edición en línea de la página de CMS y lanzan &quot;Error 500&quot;.

<u>Pasos a seguir</u>:

1. Vaya al Panel de administración > **Contenido** > **Jerarquía**.
1. Seleccione &quot;Vista de tienda predeterminada&quot;.
1. Desmarque &quot;Usar la jerarquía de nodos principal&quot;.
1. Seleccione la página manualmente y haga clic en **Guardar**.
1. A Continuación, Vaya A **Contenido** > **Páginas**.
1. Intente editar cualquier página de CMS de la cuadrícula.
1. Haga clic en **Guardar**.

<u>Resultados esperados</u>:

Página guardada correctamente.

<u>Resultados reales</u>:

Se obtiene el siguiente error:

*Un problema técnico con el servidor creó un error. Intenta de nuevo continuar lo que estabas haciendo. Si el problema persiste, inténtelo de nuevo más tarde.*

`Error: Call to a member function getData() on null in /magento2ee/app/code/Magento/VersionsCms/Controller/Adminhtml/Cms/Page/InlineEdit/Plugin.php:62`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
