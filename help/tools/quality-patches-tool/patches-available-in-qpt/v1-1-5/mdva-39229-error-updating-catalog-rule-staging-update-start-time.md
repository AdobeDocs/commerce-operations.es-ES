---
title: 'MDVA-39229: Error tras actualizar la hora de inicio de la actualización de ensayo de la regla de catálogo'
description: El parche MDVA-39229 corrige el problema en el que los usuarios reciben un error después de actualizar la hora de inicio de la actualización del ensayo de la regla del catálogo. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. El ID del parche es MDVA-39229. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: Catalog Management, Staging
role: Admin
exl-id: 633123bc-634c-4943-a2f1-9a48999774f4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-39229: Error tras actualizar la hora de inicio de la actualización de ensayo de la regla de catálogo

El parche MDVA-39229 corrige el problema en el que los usuarios reciben un error después de actualizar la hora de inicio de la actualización del ensayo de la regla del catálogo. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. El ID del parche es MDVA-39229. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.4-p2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios reciben un error después de actualizar la hora de inicio de la actualización de ensayo de la regla de catálogo.

<u>Pasos a seguir</u>:

1. Cree una regla de precio de catálogo.
1. Cree y ejecute cualquier actualización de ensayo.
1. Ejecute la consulta y compruebe que se ha creado el indicador de ensayo.


   `select * from flag;`


1. Cree una nueva actualización de ensayo para que se inicie pasados cinco minutos.
1. Abra **Contenido** > **Ensayo** > **Tablero** > **Nueva actualización** y retrase la hora de inicio en un minuto.
1. Espera seis minutos.
1. Corre cron.

<u>Resultados esperados</u>:

La hora de inicio de la actualización cambia y se aplica la actualización. La actualización anterior se eliminó de la tabla `staging_update`.

<u>Resultados reales</u>:

Los usuarios reciben el siguiente error:

*report.ERROR: el trabajo cron staging_sync_entities_period tiene un error: no se puede eliminar la actualización activa.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
