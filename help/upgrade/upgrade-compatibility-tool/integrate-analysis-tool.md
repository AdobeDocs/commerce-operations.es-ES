---
title: Integrar  [!DNL Site-Wide Analysis Tool]
description: Siga estos pasos para recuperar el informe  [!DNL Upgrade Compatibility Tool] del tablero [!DNL Site-Wide Analysis Tool] de su proyecto de Adobe Commerce.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Integrar [!DNL Site-Wide Analysis Tool]

[!DNL Site-Wide Analysis Tool] proporciona supervisión de rendimiento, informes y recomendaciones en tiempo real las 24 horas del día, los 7 días de la semana para garantizar la seguridad y la operabilidad de las instancias de Adobe Commerce.

El [!DNL Upgrade Compatibility Tool] está ahora integrado con el [!DNL Site-Wide Analysis Tool] para proporcionar a los usuarios no técnicos la capacidad de ejecutar el [!DNL Upgrade Compatibility Tool] y obtener un [informe](../upgrade-compatibility-tool/reports.md) que contenga una lista de problemas para cada archivo.

Consulte la [[!DNL Site-Wide Analysis Tool] guía del usuario](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access) para obtener más información.

## Ejecutar [!DNL Upgrade Compatibility Tool] desde [!DNL Site-Wide Analysis Tool]

Vaya al panel [!DNL Site-Wide Analysis Tool] de su proyecto y busque el widget [!DNL Upgrade Compatibility Tool].

![Widget SWAT UCT - Inicial](../../assets/upgrade-guide/uct-swat-initial.png)

Haga clic en **[!UICONTROL Run Upgrade Scan]**. El análisis puede tardar algún tiempo en función del tamaño del proyecto. Un control de número indica que el análisis está en curso.

![Widget SWAT de UCT - En curso](../../assets/upgrade-guide/uct-swat-progress.png)

Una vez finalizado el análisis, los resultados de alto nivel se muestran en el widget.

![Widget SWAT de UCT - Resultados](../../assets/upgrade-guide/uct-swat-results.png)

Haga clic en **[!UICONTROL Download Report]** para recuperar [!DNL Upgrade Compatibility Tool] [informe de HTML](../upgrade-compatibility-tool/reports.md#html-report) y revise los detalles.


>[!NOTE]
>
> Al ejecutar [!DNL Upgrade Compatibility Tool] a través de [!DNL Site-Wide Analysis Tool], se optimizan los resultados y se ayuda a centrarse en los problemas que son nuevos y críticos para la actualización de destino. Utiliza la opción [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) y siempre muestra los resultados comparando la versión del proyecto con la última versión lanzada.
