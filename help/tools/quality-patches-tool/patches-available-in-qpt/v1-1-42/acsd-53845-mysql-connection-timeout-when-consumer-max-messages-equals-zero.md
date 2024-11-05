---
title: "ACSD-53845: problema de tiempo de espera de conexión MySQL cuando el consumidor max_messages = 0"
description: Aplique el parche ACSD-53845 para corregir el problema de Adobe Commerce donde la conexión MySQL excede el tiempo de espera cuando el consumidor "max_messages = 0".
feature: REST, Configuration
role: Admin, Developer
source-git-commit: 809defe75d7b218d8085f85ff815472a531040cf
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-53845: problema de tiempo de espera de conexión MySQL cuando el consumidor `max_messages = 0`

El parche ACSD-53845 corrige el problema en el que la conexión MySQL se agota cuando el consumidor `max_messages = 0`. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.42. El ID del parche es ACSD-53845. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La conexión MySQL agota el tiempo de espera cuando el consumidor `max_messages = 0`.

Sin embargo, la conexión con la base de datos se restaurará al iniciar una transacción.

<u>Pasos a seguir</u>:

1. Envíe una solicitud para actualizar productos en lote mediante el extremo de la API REST `async/bulk/V1/products`.
1. Comprobar el estado en la tabla `magento_operation`.

<u>Resultados esperados</u>:

Los productos se han actualizado.

<u>Resultados reales</u>:

1. Se registra un error:

   ```
   report.CRITICAL: Message has been rejected: SQLSTATE[HY000]: General error: 2006 MySQL server has gone away [] []
   ```

1. *status* para esta operación permanece *4* en la tabla `magento_operation`.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool]
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
