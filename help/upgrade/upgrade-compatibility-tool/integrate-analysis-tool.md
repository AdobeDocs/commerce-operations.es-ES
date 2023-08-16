---
title: Integración de [!DNL Site-Wide Analysis Tool]
description: Siga estos pasos para recuperar la variable [!DNL Upgrade Compatibility Tool] informe desde el [!DNL Site-Wide Analysis Tool] en el proyecto de Adobe Commerce.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Integración de [!DNL Site-Wide Analysis Tool]

El [!DNL Site-Wide Analysis Tool] proporciona monitorización del rendimiento, informes y recomendaciones en tiempo real las 24 horas del día, los 7 días de la semana, para garantizar la seguridad y la operabilidad de las instancias de Adobe Commerce.

El [!DNL Upgrade Compatibility Tool] ahora está integrado con el [!DNL Site-Wide Analysis Tool] con el fin de proporcionar a las personas no técnicas la capacidad de ejecutar el [!DNL Upgrade Compatibility Tool] y obtenga una [informe](../upgrade-compatibility-tool/reports.md) que contiene una lista de problemas para cada archivo.

Consulte la [[!DNL Site-Wide Analysis Tool] guía del usuario](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) para obtener más información.

## Ejecute el [!DNL Upgrade Compatibility Tool] desde el [!DNL Site-Wide Analysis Tool]

Vaya a [!DNL Site-Wide Analysis Tool] tablero del proyecto y busque el [!DNL Upgrade Compatibility Tool] widget.

![Widget SWAT UCT - Inicial](../../assets/upgrade-guide/uct-swat-initial.png)

Haga clic **[!UICONTROL Run Upgrade Scan]**. El análisis puede tardar algún tiempo en función del tamaño del proyecto. Un control de número indica que el análisis está en curso.

![Widget SWAT de UCT: en curso](../../assets/upgrade-guide/uct-swat-progress.png)

Una vez finalizado el análisis, los resultados de alto nivel se muestran en el widget.

![Widget SWAT de UCT - Resultados](../../assets/upgrade-guide/uct-swat-results.png)

Clic **[!UICONTROL Download Report]** para recuperar el [!DNL Upgrade Compatibility Tool] [informe del HTML](../upgrade-compatibility-tool/reports.md#html-report) y revise los detalles.


>[!NOTE]
>
> Ejecución de la [!DNL Upgrade Compatibility Tool] a través de [!DNL Site-Wide Analysis Tool] optimiza los resultados y le ayuda a centrarse en problemas nuevos y críticos para la actualización de Target. Utiliza el [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) y siempre muestra los resultados comparando la versión del proyecto con la última versión publicada.
