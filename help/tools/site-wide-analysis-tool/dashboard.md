---
title: "[!DNL Dashboard]"
description: Obtenga información sobre [!DNL Dashboard] en la ficha [!DNL Site-Wide Analysis Tool], elementos, cuándo usar, beneficios y prácticas recomendadas.
source-git-commit: d176b6a82fbea2f3c611be0fbea85814086feed9
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

La variable [!UICONTROL Dashboard] La página se muestra de un vistazo [!DNL widgets] que proporcionan un &quot;panel único de vista de vidrio&quot; del estado actual de su sitio web de Adobe Commerce. Estos [!DNL widgets] cada una de ellas contiene un vínculo de acceso a la página de cada función, a cada herramienta o a los informes (en función del [!DNL widget]).
También hay una lista de [!UICONTROL External Resources] vínculos para Adobe Commerce, incluido el [Base de conocimientos de asistencia del Centro de ayuda de Adobe Commerce (Centro de ayuda)](https://support.magento.com/), [Documentación para desarrolladores de Adobe Commerce (DevDocs)](https://devdocs.magento.com/), [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}, [Centro de seguridad](https://magento.com/security)y [Observación para Adobe Commerce (OAC)](https://support.magento.com/hc/en-us/articles/4402379845901-Use-Observation-for-Adobe-Commerce).

## Elementos

* **[!UICONTROL Recommendations]**: Muestra recomendaciones de prácticas recomendadas para el sitio. Recommendations (problemas encontrados y recomendaciones para solucionar) se ordenan por prioridad: P0 (crítico) a P4 (notificación).
Recommendations incluye Descripción, Recomendación, Impacto en el sitio, Causa principal, Escenarios/Condiciones previas y Herramientas utilizadas.

* **[!UICONTROL Upgrade Compatibility Tool]**: Comprueba una instancia personalizada de Adobe Commerce para una versión específica analizando todos los módulos y el código principal instalados en ella. Devuelve una lista de problemas, errores y advertencias críticos que deben solucionarse antes de actualizar a la versión más reciente de Adobe Commerce. También identifica posibles problemas que deben solucionarse en el código antes de intentar actualizar a una versión más reciente de Adobe Commerce.
La variable [!UICONTROL Upgrade Compatibility Tool] le permite identificar cuándo se han realizado cambios en el código principal en las funciones personalizadas.

* **[!UICONTROL Security Scan Tool]**: Supervisa los sitios de Adobe Commerce para detectar riesgos de seguridad. Puede detectar de forma proactiva y eficiente malware en tiendas comerciales, notificar a los comerciantes si existe algún riesgo de seguridad, malware o amenaza, y puede identificar parches y actualizaciones faltantes de Adobe Commerce.

* **[!UICONTROL Extensions]**: Muestra las extensiones instaladas actualmente en la instancia de Adobe Commerce. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) se proporciona información, cuando está disponible, sobre las extensiones enumeradas allí.

* **[!UICONTROL Alerts]**: Muestra la última [!DNL New Relic Managed Alerts] para la instancia de Adobe Commerce. Más información sobre [Alertas administradas para Adobe Commerce](https://support.magento.com/hc/en-us/articles/360045806832) y cómo [Acceso a nuevos servicios de reliquia](https://support.magento.com/hc/en-us/articles/360039127712) en la Base de conocimientos de soporte de Adobe Commerce.

* **[!UICONTROL Non-recommended software in use]**: Muestra el software no recomendado que está utilizando la instancia de Adobe Commerce en función de su versión de Adobe Commerce. El software no recomendado está listado por [!UICONTROL Name], [!UICONTROL Installed Version]y [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: Muestra una breve lista de todos los parches recomendados en función de ambos parches que ya haya instalado y de su versión de Adobe Commerce. La lista completa de parches recomendados se encuentra en la **[!UICONTROL Patches]** , que también se encuentra dentro de la pestaña [!DNL Site-Wide Analysis Tool]. Los parches los proporciona el [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}. Todos los parches que aparecen son compatibles con la instancia actual de Adobe Commerce.
Si no hay parches recomendados para mostrar para su instancia de Adobe Commerce, este [!DNL widget] se mostrará, **[!UICONTROL No Recommended Patches]**.

## Cuándo se utiliza

La variable **[!UICONTROL Dashboard]** es el centro de comandos de at-a-glance en la variable [!DNL Site-Wide Analysis Tool] no solo para ver fácilmente el &quot;panorama general&quot; del estado de su sitio en general, sino también para ver y acceder a herramientas, recomendaciones e informes específicos para su sitio web de Adobe Commerce a través de cada [!DNL widget].

## Ventajas

* La variable [!DNL widgets] para [!UICONTROL Recommendations], [!UICONTROL Extensions]y [!UICONTROL Security Scan] todos utilizan gráficos circulares interactivos, codificados por color y fáciles de leer, con leyendas de gráficos a los lados y cuentan los totales en el centro para indicar cuántas [!UICONTROL Recommendations], [!UICONTROL Extensions]y [!UICONTROL Security Scan Tool] elementos que cada función tiene. [!UICONTROL Recommendations] y [!UICONTROL Security Scan Tool] los gráficos se separan por gravedad. [!UICONTROL Extensions] se separan en cuatro clasificaciones: versión actual, versión anterior, deshabilitada y desconocida.

* [!DNL New Relic Alerts] aparecen con la alerta más reciente en la parte superior, incluida una breve descripción y cuánto tiempo atrás se produjo la alerta.

* La variable [!UICONTROL Recommendations] y [!UICONTROL Extensions] [!DNL widgets] tener acceso a la página completa de datos de cada función haciendo clic en **[!UICONTROL View All]**.

* La variable [!UICONTROL Security Scan Tool] tiene un **[!UICONTROL View Report]** en el [!DNL widget] que le lleva a la ventana [!UICONTROL Recommendations] página.

* La variable [!DNL Upgrade Compatibility Tool] tiene un **[!UICONTROL Run Upgrade Scan]** en el [!DNL widget] ventana.

## Prácticas recomendadas para usar la variable [!UICONTROL Dashboard]

* Haga clic en cada [!DNL widget] para acceder a los datos detallados que proporciona, a fin de conocer y comprender el estado del sitio web, las recomendaciones y las prácticas recomendadas para mejorarlo.

* Vaya a la [!UICONTROL Security Scan Tool] [!DNL widget] y haga clic en [!UICONTROL View Report] para ver una [!UICONTROL Recommendations] informe del sitio.

* Utilice la variable [!DNL External Resources] vínculos para obtener más información, mantenerse actualizado sobre parches de seguridad, actualizaciones y prácticas recomendadas, o aprovechar la perspectiva de la [Base de conocimientos de asistencia del Centro de ayuda de Adobe Commerce (Centro de ayuda)](https://support.magento.com/), [Documentación para desarrolladores de Adobe Commerce (DevDocs)](https://devdocs.magento.com/), [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}, [Centro de seguridad](https://helpx.adobe.com/security.html)y [Observación para Adobe Commerce (OAC)](https://support.magento.com/hc/en-us/articles/4402379845901-Use-Observation-for-Adobe-Commerce).
