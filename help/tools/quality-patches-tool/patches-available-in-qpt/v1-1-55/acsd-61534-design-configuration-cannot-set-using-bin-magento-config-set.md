---
title: 'ACSD-61534: la configuración de diseño no se puede establecer con bin/magento config:set, y los valores bloqueados se pueden modificar mediante la manipulación de formularios'
description: Aplique el parche ACSD-61534 para corregir el problema de Adobe Commerce en el que la configuración de diseño no se puede establecer con el comando bin/magento config:set y los valores bloqueados se pueden modificar mediante la manipulación de formularios.
feature: Configuration
role: Admin, Developer
source-git-commit: ef00c05593ad319caab8bb9e0f5090959786513f
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-61534: la configuración de diseño no se puede establecer con `bin/magento config:set` y los valores bloqueados se pueden modificar mediante la manipulación de formularios

El parche ACSD-61534 corrige el problema en el que la configuración de diseño no se puede establecer con el comando `bin/magento config:set` y los valores bloqueados se pueden modificar mediante la manipulación de formularios. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. El ID del parche es ACSD-61534. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La configuración de diseño no se puede establecer con el comando `bin/magento config:set`, y los valores bloqueados se pueden modificar mediante la manipulación de formularios. Con esta revisión, los valores bloqueados establecidos desde la herramienta de línea de comandos (CLI) con `--lock-env` o `--lock-conf` no se pueden actualizar.

<u>Pasos a seguir</u>:

1. Bloquee un valor de configuración usando una variable de entorno de nube, como `CONFIG_WEBSITESBASEDESIGNHEAD_INCLUDES`.
1. Vaya al panel *[!UICONTROL Admin]*.
1. Vaya a **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Haga clic en **[!UICONTROL Edit]** cerca de **[!UICONTROL Global/Main website]** en la segunda fila.
1. Editar tema para una vista de tienda.
1. Abra la cabeza del HTML.
1. Habilite el campo **[!UICONTROL Scripts and Style Sheets]** deshabilitado con las herramientas para desarrolladores.
1. Cambie el valor y guárdelo.

<u>Resultados esperados</u>:

No se puede guardar un valor bloqueado.

<u>Resultados reales</u>:

La tabla `core_config_data` contiene un valor actualizado para `design/head/includes`.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
