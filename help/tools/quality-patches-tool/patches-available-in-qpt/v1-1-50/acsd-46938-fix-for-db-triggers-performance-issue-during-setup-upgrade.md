---
title: 'ACSD-46938: Problemas de rendimiento con déclencheur de BD durante "setup:upgrade"'
description: Aplique el parche ACSD-46938 para corregir el problema de Adobe Commerce donde el comando "setup:upgrade" cambia el modo del indexador de la programación a la hora de guardar, lo que provoca ralentizaciones significativas del rendimiento.
feature: Upgrade
role: Admin, Developer
exl-id: a4e88329-c5bb-4666-8738-b78b86056b71
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-46938: problemas de rendimiento con déclencheur de BD durante `setup:upgrade`

El parche ACSD-46938 corrige el problema en el que el comando `setup:upgrade` cambia el modo del indizador de la programación a guardar, lo que provoca ralentizaciones significativas del rendimiento. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50. El ID del parche es ACSD-46938. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Degradación de rendimiento durante la recreación del déclencheur de la base de datos en `setup:upgrade`.

<u>Pasos a seguir</u>:

1. Cree un catálogo grande con muchos productos y categorías.
1. Inicie sesión en [!UICONTROL Admin].
1. Establezca todos los indizadores en el modo [!UICONTROL Update By Schedule].
1. Abra cualquier producto.
1. Actualízalo.. Por ejemplo, asígnele una nueva categoría.
1. Haga clic en [!UICONTROL Save].
1. Ejecute `bin/magento setup:upgrade` y `bin/magento cron:run` comandos en paralelo.

<u>Resultados esperados</u>:

El tiempo de ejecución del comando `bin/magento setup:upgrade` aumenta significativamente cuando el comando `bin/magento cron:run` se ejecuta simultáneamente.

<u>Resultados reales</u>:

El tiempo de ejecución del comando no aumenta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
