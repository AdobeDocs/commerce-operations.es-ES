---
title: '[!DNL Dashboard]'
description: Obtenga información sobre [!DNL Dashboard] en la ficha [!DNL Site-Wide Analysis Tool], elementos, cuándo usar, beneficios y prácticas recomendadas.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

La variable [!UICONTROL Dashboard] La página se muestra de un vistazo [!DNL widgets] que proporcionan un &quot;panel único de vista de vidrio&quot; del estado actual de su sitio web de Adobe Commerce. Cada [!DNL widget] contiene un vínculo de acceso a la página de cada función, a cada herramienta o a los informes (en función del [!DNL widget]).
También hay una lista de [!UICONTROL External Resources] vínculos para Adobe Commerce, incluido el [Base de conocimientos de asistencia del Centro de ayuda de Adobe Commerce (Centro de ayuda)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentación para desarrolladores de Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Centro de seguridad](https://helpx.adobe.com/security.html)y [Observación para Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## Elementos

* **[!UICONTROL Recommendations]**: Muestra recomendaciones de prácticas recomendadas para el sitio. Recommendations (problemas encontrados y recomendaciones para solucionar) se ordenan por prioridad: P0 (crítico) a P4 (notificación).
Recommendations incluye Descripción, Recomendación, Impacto en el sitio, Causa principal, Escenarios/Condiciones previas y Herramientas utilizadas.

* **[!UICONTROL Upgrade Compatibility Tool]**: Comprueba una instancia personalizada de Adobe Commerce para una versión específica analizando todos los módulos y el código principal instalados en ella. Devuelve una lista de problemas, errores y advertencias críticos que deben solucionarse antes de actualizar a la versión más reciente de Adobe Commerce. También identifica posibles problemas que deben solucionarse en el código antes de intentar actualizar a una versión más reciente de Adobe Commerce.
La variable [!UICONTROL Upgrade Compatibility Tool] le permite identificar cuándo se han realizado cambios en el código principal en las funciones personalizadas.

* **[!UICONTROL Security Center Widget]**: Muestra perspectivas de seguridad para el sitio.
La información de seguridad mostrada incluye [Tech [!DNL Stack] Cumplimiento de versiones con [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] Práctica recomendada Seguridad Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
La variable [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) supervisa los sitios de Adobe Commerce para detectar riesgos de seguridad. Puede detectar de forma proactiva y eficiente malware en tiendas comerciales, notificar a los comerciantes si existe algún riesgo de seguridad, malware o amenaza, y puede identificar parches y actualizaciones faltantes de Adobe Commerce.

* **[!UICONTROL Extensions]**: Muestra las extensiones instaladas actualmente en la instancia de Adobe Commerce. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) se proporciona información, cuando está disponible, sobre las extensiones enumeradas allí.

* **[!UICONTROL Alerts]**: Muestra la última [!DNL New Relic Managed Alerts] para la instancia de Adobe Commerce. Más información sobre [Alertas administradas para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) y cómo [Acceso a los servicios de New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) en la Base de conocimientos de soporte de Adobe Commerce.

* **[!UICONTROL Non-recommended software in use]**: Muestra el software no recomendado que está utilizando la instancia de Adobe Commerce en función de su versión de Adobe Commerce. El software no recomendado está listado por [!UICONTROL Name], [!UICONTROL Installed Version]y [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: Muestra una breve lista de todos los parches recomendados en función de ambos parches que ya haya instalado y de su versión de Adobe Commerce. La lista completa de parches recomendados se encuentra en la **[!UICONTROL Patches]** , que también se encuentra dentro de la pestaña [!DNL Site-Wide Analysis Tool]. Los parches los proporciona el [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Todos los parches que aparecen son compatibles con la instancia actual de Adobe Commerce.
Si no hay parches recomendados para mostrar para su instancia de Adobe Commerce, este [!DNL widget] se mostrará, **[!UICONTROL No Recommended Patches]**.

## Cuándo se utiliza

La variable **[!UICONTROL Dashboard]** es el centro de comandos de at-a-glance en la variable [!DNL Site-Wide Analysis Tool] no solo para ver fácilmente el &quot;panorama general&quot; del estado de su sitio en general, sino también para ver y acceder a herramientas, recomendaciones e informes específicos para su sitio web de Adobe Commerce a través de cada [!DNL widget].

## Ventajas

* La variable [!DNL widgets] para [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions]y [!UICONTROL Security Scan] todos utilizan gráficos circulares interactivos, codificados por color y fáciles de leer, con leyendas de gráficos a los lados y cuentan los totales en el centro para indicar cuántas [!UICONTROL Recommendations], [!UICONTROL Extensions]y [!UICONTROL Security Scan Tool] elementos que cada función tiene. [!UICONTROL Recommendations] y [!UICONTROL Security Scan Tool] los gráficos se separan por gravedad. [!UICONTROL Extensions] se separan en cuatro clasificaciones: versión actual, versión anterior, deshabilitada y desconocida.

* [!DNL New Relic Alerts] aparecen con la alerta más reciente en la parte superior, incluida una breve descripción y cuánto tiempo atrás se produjo la alerta.

* La variable [!UICONTROL Recommendations] y [!UICONTROL Extensions] [!DNL widgets] tener acceso a la página completa de datos de cada función haciendo clic en **[!UICONTROL View All]**.

* La variable [!UICONTROL Security Scan Tool] tiene un **[!UICONTROL View Report]** en el [!DNL widget] que le lleva a la ventana [!UICONTROL Recommendations] página.

* La variable [!DNL Upgrade Compatibility Tool] tiene un **[!UICONTROL Run Upgrade Scan]** en el [!DNL widget] ventana.

## Prácticas recomendadas para usar la variable [!UICONTROL Dashboard]

* Haga clic en cada [!DNL widget] para acceder a los datos detallados que proporciona, a fin de conocer y comprender la seguridad, el estado, las recomendaciones y las prácticas recomendadas de su sitio web y mejorarlo.

* Vaya a la [!UICONTROL Security Scan Tool] [!DNL widget] y haga clic en [!UICONTROL View Report] para ver una [!UICONTROL Recommendations] informe del sitio.

* Utilice la variable [!DNL External Resources] vínculos para obtener más información, mantenerse actualizado sobre parches de seguridad, actualizaciones y prácticas recomendadas, o aprovechar la perspectiva de la [Base de conocimientos de asistencia del Centro de ayuda de Adobe Commerce (Centro de ayuda)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentación para desarrolladores de Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Centro de seguridad](https://helpx.adobe.com/security.html)y [Observación para Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
