---
title: Información general de  [!DNL Upgrade Compatibility Tool]
description: Obtenga información acerca de  [!DNL Upgrade Compatibility Tool]  y cómo puede ayudarle con su proyecto de Adobe Commerce.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Información general de guía

{{commerce-only}}

Esta guía está dirigida a administradores e ingenieros de software de Adobe Commerce. Incluye información detallada acerca de la instalación de [!DNL Upgrade Compatibility Tool], así como su configuración y administración. Supone una comprensión básica de la configuración y la funcionalidad principales de Commerce.

## Información general de [!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool] es una herramienta que compara una instancia personalizada de Adobe Commerce con una versión específica analizando todos los módulos y el código principal instalados en ella. Devuelve una lista de problemas, errores y advertencias críticos que deben solucionarse antes de actualizar a una versión más reciente de Adobe Commerce.

## Usar [!DNL Upgrade Compatibility Tool]

Puede usar el(la) [!DNL Upgrade Compatibility Tool] mediante:

- Como herramienta independiente [interfaz de línea de comandos](../upgrade-compatibility-tool/run.md). Para obtener la lista completa de comandos disponibles, vea la referencia [`bin/uct` ](../../tools/reference/uct.md).
- Integrando [!DNL Upgrade Compatibility Tool] con [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Una configuración de ejecución dentro del [complemento Magento PHPStorm](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Flujo de trabajo

El diagrama siguiente muestra los posibles flujos de trabajo al ejecutar [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] diagrama](../../assets/upgrade-guide/uct-diagram-v5.png)

## Demostración de [!DNL Upgrade Compatibility Tool]

Vea este vídeo para obtener más información acerca de [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/344382?quality=12&captions=spa)

## Ayudar a mejorar [!DNL Upgrade Compatibility Tool]

Si necesita información o tiene preguntas que no se tratan en esta guía, utilice los siguientes recursos:

Para conectarse con el equipo [!DNL Upgrade Compatibility Tool], póngase en contacto con nosotros en el canal de Slack de ingeniería [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Queremos escuchar sus comentarios, problemas y sugerencias para ayudarnos a mejorar la herramienta.

[!DNL Upgrade Compatibility Tool] usa reglas definidas en nuestros [estándares de codificación](https://developer.adobe.com/commerce/php/coding-standards/) para garantizar que su proyecto sigue las prácticas recomendadas de Adobe Commerce y para ayudarle a mejorar y ampliar [!DNL Upgrade Compatibility Tool].

Consulte el tema [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) para obtener más información sobre cómo contribuir con estándares de codificación.

## Recursos

Consulte los siguientes recursos para comprender mejor las actualizaciones de Adobe Commerce:

- La [guía de actualización](../overview.md) proporciona información general sobre el recorrido de actualización típico de Adobe Commerce y las prácticas recomendadas a lo largo de ese recorrido.
- La página [próximas versiones](https://experienceleague.adobe.com/es/docs/commerce-operations/release/planning/schedule) proporciona las fechas para las versiones programadas y próximas.
- La página [recursos de la comunidad](https://developer.adobe.com/commerce/contributor/community/) se encuentra aquí para iniciar discusiones o encontrar más información.
- Consulte la página [herramientas relacionadas](../upgrade-compatibility-tool/related-tools.md) para obtener herramientas útiles en su recorrido de actualización habitual.
