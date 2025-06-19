---
title: 'ACSD-61366: el comando `bin/magento setup:static-content:deploy —jobs 4` encuentra varios errores de trabajo con un error'
description: Aplique el parche ACSD-61366 para corregir el problema de Adobe Commerce en el que el comando `bin/magento setup:static-content:deploy —jobs 4` encuentra varios errores de trabajo con el error *Port debe configurarse dentro del parámetro host*, a pesar de especificar el puerto para la conexión DB.
feature: SCD
role: Admin, Developer
exl-id: d71a4833-a236-429b-a4e5-7d7d51c2caeb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61366: el comando `bin/magento setup:static-content:deploy --jobs 4` encuentra varios errores de trabajo con un error

El parche ACSD-61366 corrige el problema en el que el comando `bin/magento setup:static-content:deploy --jobs 4` encuentra varios errores de trabajo con el error *El puerto debe configurarse dentro del parámetro de host*, a pesar de que se haya especificado el puerto para la conexión DB. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52. El ID del parche es ACSD-61366. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El comando `bin/magento setup:static-content:deploy --jobs 4` encuentra varios errores de trabajo con el error *El puerto debe configurarse dentro del parámetro de host*, a pesar de que se haya especificado el puerto para la conexión DB.

<u>Pasos a seguir</u>:

1. Especifique un puerto en la conexión de base de datos en `app/etc/env.php`.
1. Ejecute el comando `bin/magento setup:static-content:deploy --jobs 4`.

<u>Resultados esperados</u>:

La implementación de contenido estático finaliza correctamente.

<u>Resultados reales</u>:

El comando falla con el error *Port must be configured into host parameter*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
