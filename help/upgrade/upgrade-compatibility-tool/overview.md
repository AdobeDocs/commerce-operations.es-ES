---
title: Descripción general de [!DNL Upgrade Compatibility Tool]
description: Obtenga información acerca de [!DNL Upgrade Compatibility Tool] y cómo puede ayudarle con su proyecto de Adobe Commerce.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: fc1be3362863d3b0fa3468380fe62ca698abac43
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Información general de guía

{{commerce-only}}

Esta guía está dirigida a administradores e ingenieros de software de Adobe Commerce. Incluye información detallada sobre la instalación del [!DNL Upgrade Compatibility Tool], así como su configuración y administración. Supone una comprensión básica de la configuración y funcionalidad principales de Commerce.

## Descripción general de [!DNL Upgrade Compatibility Tool]

El [!DNL Upgrade Compatibility Tool] es una herramienta que compara una instancia personalizada de Adobe Commerce con una versión específica analizando todos los módulos y el código principal instalados en ella. Devuelve una lista de problemas, errores y advertencias críticos que deben solucionarse antes de actualizar a una versión más reciente de Adobe Commerce.

## Utilice el [!DNL Upgrade Compatibility Tool]

Puede usar el complemento [!DNL Upgrade Compatibility Tool] mediante:

- Como independiente [interfaz de línea de comandos](../upgrade-compatibility-tool/run.md) herramienta. Para ver la lista completa de comandos disponibles, consulte la [`bin/uct` reference](../../tools/reference/uct.md).
- Integración de [!DNL Upgrade Compatibility Tool] con el [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Una configuración de ejecución dentro de [Complemento Magento PHPStorm](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Flujo de trabajo

El diagrama siguiente muestra los posibles flujos de trabajo al ejecutar el [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagrama](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] demostración

Vea este vídeo para obtener más información sobre [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## Ayude a mejorar el [!DNL Upgrade Compatibility Tool]

Si necesita información o tiene preguntas que no se tratan en esta guía, utilice los siguientes recursos:

Para conectar con [!DNL Upgrade Compatibility Tool] Equipo, póngase en contacto con nosotros en el canal del Slack de ingeniería [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Queremos escuchar sus comentarios, problemas y sugerencias para ayudarnos a mejorar la herramienta.

El [!DNL Upgrade Compatibility Tool] utiliza reglas definidas dentro de su [Estándares de codificación](https://developer.adobe.com/commerce/php/coding-standards/) para asegurarse de que el proyecto sigue las prácticas recomendadas de Adobe Commerce y para ayudarle a mejorar y ampliar el [!DNL Upgrade Compatibility Tool].

Consulte la [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) para obtener más información sobre cómo contribuir a los estándares de codificación.

## Recursos

Consulte los siguientes recursos para comprender mejor las actualizaciones de Adobe Commerce:

- El [guía de actualización](../overview.md) proporciona información general sobre el recorrido de actualización típico de Adobe Commerce y las prácticas recomendadas que deben seguirse a lo largo de ese recorrido.
- El [próximas versiones](https://devdocs.magento.com/release/) proporciona las fechas para las versiones programadas y próximas.
- El [recursos comunitarios](https://developer.adobe.com/commerce/contributor/community/) página es un lugar para iniciar discusiones o encontrar más información.
- Compruebe la [herramientas relacionadas](../upgrade-compatibility-tool/related-tools.md) para obtener herramientas útiles en su recorrido de actualización habitual.
