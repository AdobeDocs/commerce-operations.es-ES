---
title: '[!DNL Dashboard]'
description: Obtenga información acerca de [!DNL Dashboard] en la pestaña [!DNL Site-Wide Analysis Tool], elementos, cuándo usar, ventajas y prácticas recomendadas.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

El [!UICONTROL Dashboard] La página muestra de un vistazo [!DNL widgets] que proporcionan un &quot;único panel de vista&quot; del estado y el estado actual del sitio web de Adobe Commerce. Cada [!DNL widget] contiene un vínculo de acceso a la página de cada función, a cada herramienta o a los informes (en función de la variable [!DNL widget]).
También hay una lista de [!UICONTROL External Resources] vínculos para Adobe Commerce, incluido el [Base de conocimiento de asistencia del Centro de ayuda de Adobe Commerce (Centro de ayuda)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentación para desarrolladores de Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Centro de seguridad](https://helpx.adobe.com/security.html), y [Observación para Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## Elementos

* **[!UICONTROL Recommendations]**: muestra las recomendaciones de prácticas recomendadas para el sitio. Recommendations (problemas encontrados y recomendaciones que corregir) se ordenan por prioridad: de P0 (crítico) a P4 (notificación).
Recommendations incluye Descripción, Recomendación, Impacto del sitio, Causa raíz, Escenarios/Condiciones previas y Herramientas utilizadas.

* **[!UICONTROL Upgrade Compatibility Tool]**: comprueba una instancia personalizada de Adobe Commerce en una versión específica analizando todos los módulos y el código principal instalados en ella. Devuelve una lista de problemas, errores y advertencias críticos que deben solucionarse antes de actualizar a la versión más reciente de Adobe Commerce. También identifica posibles problemas que deben solucionarse en el código antes de intentar actualizar a una versión más reciente de Adobe Commerce.
El [!UICONTROL Upgrade Compatibility Tool] le permite identificar cuándo se han realizado cambios en el código principal de las funciones personalizadas.

* **[!UICONTROL Security Center Widget]**: muestra información de seguridad del sitio.
La información de seguridad que se muestra incluye [Tecnología [!DNL Stack] Cumplimiento de la versión con [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] Prácticas recomendadas de seguridad de Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
El [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) supervisa los sitios de Adobe Commerce en busca de riesgos de seguridad. Puede detectar de forma proactiva y eficaz el malware en las tiendas comerciales y notificar a los comerciantes si hay algún riesgo de seguridad, malware o amenazas, y puede identificar los parches y actualizaciones de Adobe Commerce que faltan.

* **[!UICONTROL Extensions]**: Muestra las extensiones instaladas actualmente en la instancia de Adobe Commerce. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) se proporciona información, si está disponible, sobre las extensiones enumeradas allí.

* **[!UICONTROL Alerts]**: muestra la última versión [!DNL New Relic Managed Alerts] para la instancia de Adobe Commerce. Más información sobre [Alertas administradas para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) y cómo [Acceso a servicios de New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) en la Base de conocimiento de asistencia de Adobe Commerce.

* **[!UICONTROL Non-recommended software in use]**: Muestra el software no recomendado que está utilizando la instancia de Adobe Commerce en ese momento, en función de la versión de Adobe Commerce. El software no recomendado se enumera por [!UICONTROL Name], [!UICONTROL Installed Version], y [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: Muestra una breve lista de los parches recomendados en función de los parches que ya haya instalado y de la versión de Adobe Commerce. La lista completa de parches recomendados se encuentra en la **[!UICONTROL Patches]** pestaña característica, que también se encuentra dentro de [!DNL Site-Wide Analysis Tool]. Los parches los proporciona el [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Todos los parches enumerados son compatibles con su instancia de Adobe Commerce actual.
Si no hay parches recomendados que mostrar para su instancia de Adobe Commerce, esto [!DNL widget] se mostrará, **[!UICONTROL No Recommended Patches]**.

## Cuándo usar

El **[!UICONTROL Dashboard]** es el centro de comandos de un vistazo en la [!DNL Site-Wide Analysis Tool] para no solo ver fácilmente la &quot;imagen general&quot; del estado del sitio en su conjunto, sino que también puede ver y acceder a herramientas, recomendaciones e informes específicos para el sitio web de Adobe Commerce a través de cada una [!DNL widget].

## Ventajas

* El [!DNL widgets] para [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions], y [!UICONTROL Security Scan] todos utilizan gráficos circulares interactivos, codificados por colores y fáciles de leer, con leyendas de gráficos a un lado y cuentan los totales en el centro para indicar cuántos [!UICONTROL Recommendations], [!UICONTROL Extensions], y [!UICONTROL Security Scan Tool] elementos que tiene cada función. [!UICONTROL Recommendations] y [!UICONTROL Security Scan Tool] Los gráficos de están separados por gravedad. [!UICONTROL Extensions] se separan en cuatro clasificaciones: versión actual, versión antigua, deshabilitada y desconocida.

* [!DNL New Relic Alerts] se muestran con la alerta más reciente encima, incluida una breve descripción y hace cuánto tiempo se produjo la alerta.

* El [!UICONTROL Recommendations] y [!UICONTROL Extensions] [!DNL widgets] Tendrá acceso a la página completa de datos de cada función haciendo clic en **[!UICONTROL View All]**.

* El [!UICONTROL Security Scan Tool] tiene un **[!UICONTROL View Report]** vínculo en el [!DNL widget] que le lleva a la [!UICONTROL Recommendations] página.

* El [!DNL Upgrade Compatibility Tool] tiene un **[!UICONTROL Run Upgrade Scan]** botón en el [!DNL widget] ventana.

## Prácticas recomendadas para usar [!UICONTROL Dashboard]

* Haga clic en cada [!DNL widget] para acceder a los datos detallados que proporciona y obtener información y comprensión sobre la seguridad, el estado, las recomendaciones y las prácticas recomendadas de su sitio web para mejorarlo.

* Vaya a la [!UICONTROL Security Scan Tool] [!DNL widget] y haga clic en [!UICONTROL View Report] para ver una [!UICONTROL Recommendations] para el sitio.

* Utilice el [!DNL External Resources] vínculos para obtener más información, mantenerse actualizado sobre parches de seguridad, actualizaciones y prácticas recomendadas, o aprovechar la perspectiva del [Base de conocimiento de asistencia del Centro de ayuda de Adobe Commerce (Centro de ayuda)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentación para desarrolladores de Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Centro de seguridad](https://helpx.adobe.com/security.html), y [Observación para Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
