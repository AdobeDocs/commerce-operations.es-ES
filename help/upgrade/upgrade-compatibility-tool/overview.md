---
title: '"Descripción general de la variable [!DNL Upgrade Compatibility Tool]"'
description: Obtenga información sobre [!DNL Upgrade Compatibility Tool] y cómo puede ayudarle con su proyecto de Adobe Commerce.
source-git-commit: fd624a97d74c7f6a9e29223227dae425bb6fa68c
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# Información general de la guía

{{commerce-only}}

Esta guía está diseñada para administradores e ingenieros de software de Adobe Commerce. Incluye información detallada sobre la instalación del [!DNL Upgrade Compatibility Tool], así como su configuración y administración. Supone una comprensión básica de la configuración y funcionalidad de Commerce principal.

## Información general sobre [!DNL Upgrade Compatibility Tool]

La variable [!DNL Upgrade Compatibility Tool] es una herramienta que comprueba una instancia personalizada de Adobe Commerce con una versión específica analizando todos los módulos y el código principal instalados en ella. Devuelve una lista de problemas, errores y advertencias críticos que deben solucionarse antes de actualizar a una versión más reciente de Adobe Commerce.

## Utilice la variable [!DNL Upgrade Compatibility Tool]

Puede usar la variable [!DNL Upgrade Compatibility Tool] mediante:

- Como independiente [interfaz de línea de comandos](../upgrade-compatibility-tool/run.md) herramienta.
- Integración de [!DNL Upgrade Compatibility Tool] con la variable [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Una configuración de ejecución dentro de la variable [Complemento PHPStorm Magento](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Flujo de trabajo

El diagrama siguiente muestra los posibles flujos de trabajo al ejecutar el [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagrama](../../assets/upgrade-guide/uct-diagram-v5.png)

## Ayuda a mejorar el [!DNL Upgrade Compatibility Tool]

Si necesita información o tiene preguntas que no están incluidas en esta guía, utilice los siguientes recursos:

Para conectarse con el [!DNL Upgrade Compatibility Tool] equipo, póngase en contacto con nosotros en el canal Slack de ingeniería [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Queremos escuchar sus comentarios, problemas y sugerencias para ayudarnos a mejorar la herramienta.

La variable [!DNL Upgrade Compatibility Tool] usa reglas definidas dentro de nuestro [Normas de codificación](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) para garantizar que el proyecto sigue las prácticas recomendadas de Adobe Commerce y para ayudarle a mejorar y ampliar el [!DNL Upgrade Compatibility Tool].

Consulte la [Contribute](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html) para obtener más información sobre cómo contribuir a los estándares de codificación.

## Recursos

Consulte los siguientes recursos para comprender las actualizaciones de Adobe Commerce:

- La variable [guía de actualización](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) proporciona información general sobre el recorrido de actualización típico de Adobe Commerce o Magento Open Source y prácticas recomendadas para seguir ese recorrido.
- La variable [próximas versiones](https://devdocs.magento.com/release/) proporciona las fechas de las versiones programadas y futuras.
- La variable [recursos de la comunidad](https://developer.adobe.com/commerce/contributor/community/) es para iniciar discusiones o para encontrar más información.
- Marque la [herramientas relacionadas](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/related-tools.html) para obtener herramientas útiles en el recorrido de actualización típico.
