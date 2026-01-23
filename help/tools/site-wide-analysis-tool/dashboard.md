---
title: '[!DNL Dashboard]'
description: Obtenga información acerca de la ficha  [!DNL Dashboard] en [!DNL Site-Wide Analysis Tool], elementos, cuándo usar, beneficios y prácticas recomendadas.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

La página [!UICONTROL Dashboard] muestra de un vistazo [!DNL widgets] que proporciona una &quot;única vista de cristal&quot; del estado y el estado actual del sitio web de Adobe Commerce. Cada [!DNL widget] contiene un vínculo de acceso a la página de cada característica, a cada herramienta o a los informes (dependiendo de [!DNL widget]).
También hay una lista de [!UICONTROL External Resources] vínculos para Adobe Commerce, entre los que se incluyen [Base de conocimiento de soporte técnico del Centro de ayuda de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentación para desarrolladores de Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Centro de seguridad](https://helpx.adobe.com/security.html) y [Observación para Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## Elementos

* **[!UICONTROL Recommendations]**: muestra las recomendaciones de prácticas recomendadas para el sitio. Las recomendaciones (problemas encontrados y recomendaciones que corregir) se ordenan por prioridad: de P0 (Crítico) a P4 (Notificación).
Las recomendaciones incluyen Descripción, Recomendación, Impacto del sitio, Causa raíz, Escenarios/Condiciones previas y Herramientas utilizadas.

* **[!UICONTROL Upgrade Compatibility Tool]**: comprueba una instancia personalizada de Adobe Commerce con una versión específica analizando todos los módulos y el código principal instalados en ella. Devuelve una lista de problemas, errores y advertencias críticos que deben solucionarse antes de actualizar a la versión más reciente de Adobe Commerce. También identifica posibles problemas que deben solucionarse en el código antes de intentar actualizar a una versión más reciente de Adobe Commerce.
[!UICONTROL Upgrade Compatibility Tool] le permite identificar cuándo se han realizado cambios en el código principal de las funciones personalizadas.

* **[!UICONTROL Security Center Widget]**: muestra información de seguridad del sitio.
La información de seguridad que se muestra incluye [Cumplimiento técnico [!DNL Stack] de la versión con [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] Recomendaciones de seguridad de prácticas recomendadas](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
[[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) supervisa los sitios de Adobe Commerce en busca de riesgos de seguridad. Puede detectar de forma proactiva y eficaz el malware en las tiendas comerciales y notificar a los comerciantes si hay algún riesgo de seguridad, malware o amenazas, y puede identificar los parches y actualizaciones de Adobe Commerce que faltan.

* **[!UICONTROL Extensions]**: muestra las extensiones instaladas actualmente en la instancia de Adobe Commerce. Se proporciona información de [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com//extensions.html), donde esté disponible, para las extensiones que se enumeran allí.

* **[!UICONTROL Alerts]**: muestra el último [!DNL New Relic Managed Alerts] para la instancia de Adobe Commerce. Obtenga más información sobre [Alertas administradas para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) y cómo [acceder a los servicios de New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) en la Base de conocimiento de asistencia de Adobe Commerce.

* **[!UICONTROL Non-recommended software in use]**: muestra el software no recomendado que está usando su instancia de Adobe Commerce en este momento, según su versión de Adobe Commerce. El software no recomendado está listado por [!UICONTROL Name], [!UICONTROL Installed Version] y [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: muestra una breve lista de las revisiones recomendadas en función de las revisiones que ya haya instalado y de su versión de Adobe Commerce. La lista completa de revisiones recomendadas se encuentra en la ficha de características **[!UICONTROL Patches]**, que también se encuentra en [!DNL Site-Wide Analysis Tool]. [[!DNL Quality Patches Tool] proporciona las revisiones: Buscar revisiones](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Todos los parches enumerados son compatibles con su instancia de Adobe Commerce actual.
Si no hay revisiones recomendadas para mostrar en la instancia de Adobe Commerce, se mostrará este(a) [!DNL widget], **[!UICONTROL No Recommended Patches]**.

## Cuándo usar

La página **[!UICONTROL Dashboard]** es el centro de comandos que tiene a su disposición de un vistazo en [!DNL Site-Wide Analysis Tool] para no solo ver fácilmente el &quot;panorama general&quot; del estado del sitio en su conjunto, sino que también puede ver y acceder a herramientas, recomendaciones e informes específicos para el sitio web de Adobe Commerce a través de cada [!DNL widget].

## Ventajas

* Los [!DNL widgets] de [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions] y [!UICONTROL Security Scan] utilizan gráficos circulares interactivos, codificados por colores y fáciles de leer, con leyendas de gráficos en los lados y totales de recuento en el centro para indicar cuántos elementos de [!UICONTROL Recommendations], [!UICONTROL Extensions] y [!UICONTROL Security Scan Tool] tiene cada característica. Los gráficos [!UICONTROL Recommendations] y [!UICONTROL Security Scan Tool] están separados por gravedad. [!UICONTROL Extensions] se han separado en cuatro clasificaciones: versión actual, versión antigua, deshabilitada y desconocida.

* [!DNL New Relic Alerts] se muestran con la alerta más reciente arriba, incluida una breve descripción y hace cuánto tiempo se produjo la alerta.

* [!UICONTROL Recommendations] y [!UICONTROL Extensions] [!DNL widgets] tienen acceso a la página completa de datos de cada característica al hacer clic en **[!UICONTROL View All]**.

* [!UICONTROL Security Scan Tool] tiene un vínculo **[!UICONTROL View Report]** en la ventana [!DNL widget] que lo lleva a la página [!UICONTROL Recommendations].

* [!DNL Upgrade Compatibility Tool] tiene un botón **[!UICONTROL Run Upgrade Scan]** en la ventana [!DNL widget].

## Prácticas recomendadas para usar [!UICONTROL Dashboard]

* Insight Haga clic en cada [!DNL widget] para acceder a los datos detallados que proporciona y conocer mejor la seguridad, el estado, las recomendaciones y las prácticas recomendadas de su sitio web para mejorarlo.

* Vaya a [!UICONTROL Security Scan Tool] [!DNL widget] y haga clic en [!UICONTROL View Report] para ver un informe de [!UICONTROL Recommendations] para su sitio.

* Use los vínculos de [!DNL External Resources] para obtener más información, mantenerse al día sobre los parches de seguridad, las actualizaciones y las prácticas recomendadas, o aproveche las ventajas de insight de la [Base de conocimiento de soporte técnico del Centro de ayuda de Adobe Commerce (Centro de ayuda)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), la [documentación para desarrolladores de Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: busque parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, el [Centro de seguridad](https://helpx.adobe.com/security.html) y la [Observación de Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
