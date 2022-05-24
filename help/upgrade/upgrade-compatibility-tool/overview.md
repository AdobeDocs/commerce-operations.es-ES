---
title: Información general sobre [!DNL Upgrade Compatibility Tool]
description: Obtenga información sobre [!DNL Upgrade Compatibility Tool] y cómo puede ayudarle con su proyecto de Adobe Commerce.
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# Información general de la guía

Esta guía está diseñada para administradores e ingenieros de software de Adobe Commerce. Incluye información detallada sobre la instalación del [!DNL Upgrade Compatibility Tool], así como su configuración y administración. Supone una comprensión básica de la configuración y funcionalidad de Commerce principal.

## Información general sobre [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

La variable [!DNL Upgrade Compatibility Tool] es una herramienta de línea de comandos que comprueba una instancia personalizada de Adobe Commerce en una versión específica analizando todos los módulos y el código principal instalados en ella. Devuelve una lista de problemas, errores y advertencias críticos que deben solucionarse antes de actualizar a una versión más reciente de Adobe Commerce.

Consulte [Ejecutar la herramienta](../upgrade-compatibility-tool/run.md) para obtener más información.

Consulte [Instalar](../upgrade-compatibility-tool/install.md) para los primeros pasos con el [!DNL Upgrade Compatibility Tool].

Consulte esta [tutorial de vídeo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) para obtener más información sobre la variable [!DNL Upgrade Compatibility Tool].

### Flujo de trabajo

El diagrama siguiente muestra los posibles flujos de trabajo al ejecutar el [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagrama](../../assets/upgrade-guide/uct-diagram-v5.png)

### La variable [!DNL Upgrade Compatibility Tool] caso de uso

El siguiente caso de uso describe el proceso típico para que un socio de Adobe Commerce actualice una instancia de cliente:

1. Descargue el [!DNL Upgrade Compatibility Tool] desde el repositorio de Adobe Commerce (`https://repo.magento.com/`). Consulte la [Descargue el [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) para obtener más información.
1. Ejecute el [!DNL Upgrade Compatibility Tool] durante el [beta](https://devdocs.magento.com/release/beta-program.html) fase del más reciente [Versión de Adobe Commerce](https://devdocs.magento.com/release/).
1. Genere una instancia de vainilla para la versión específica de Adobe Commerce que está instalada actualmente. Consulte la [Guía del colaborador](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) para obtener más información sobre el uso de la variable `instance` para generar una instalación de vainilla.

   >[!NOTE]
   >
   >Una instancia de vainilla es una instalación limpia de una rama o etiqueta de versión especificada para una versión específica.

1. La variable [!DNL Upgrade Compatibility Tool] Identifica los problemas de actualización que ayudarán a los ingenieros de software a comprender la complejidad y estimar el esfuerzo de la actualización.
1. Esta información se comparte con las partes interesadas.
1. Se definirá un presupuesto y una cronología para la actualización.
1. Los ingenieros de software pueden trabajar en las modificaciones de código necesarias para corregir los módulos rotos.
1. La variable [!DNL Upgrade Compatibility Tool] se puede ejecutar para realizar un seguimiento del progreso de la actualización.
1. Todo lo que se cierra la compra y la ingeniería ahora puede insertar el código en un entorno de ensayo en el que las pruebas de regresión confirman que todas las pruebas son verdes, lo que les permite publicar la última versión de Adobe Commerce en producción el mismo día en el que se lanza el lanzamiento previo de Adobe Commerce.

   ![[!DNL Upgrade Compatibility Tool] audiencia](../../assets/upgrade-guide/audience-uct-v3.png)

### Ayuda a mejorar el [!DNL Upgrade Compatibility Tool]

Si necesita información o tiene preguntas que no están incluidas en esta guía, utilice los siguientes recursos:

Para conectarse con el [!DNL Upgrade Compatibility Tool] equipo, póngase en contacto con nosotros en el canal Slack de ingeniería [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Queremos escuchar sus comentarios, problemas y sugerencias para ayudarnos a mejorar la herramienta.

La variable [!DNL Upgrade Compatibility Tool] usa reglas definidas dentro de nuestro [Normas de codificación](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) para garantizar que el proyecto sigue las prácticas recomendadas de Adobe Commerce y para ayudarle a mejorar y ampliar el [!DNL Upgrade Compatibility Tool].

Consulte la [Contribute](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  para obtener más información sobre cómo contribuir a los estándares de codificación.

### Recursos

Hemos desarrollado los siguientes recursos para ayudarle a comprender las actualizaciones de Adobe Commerce:

- [Guía de actualización](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [Próximas versiones](https://devdocs.magento.com/release/)
- [Recursos de la comunidad](https://devdocs.magento.com/community/resources/resources.html) para obtener más información.
- [Herramientas relacionadas](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/related-tools.html)
