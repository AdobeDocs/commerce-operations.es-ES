---
title: El [!DNL Infra] pestaña
description: El [!DNL Infra] La pestaña aísla los problemas y las causas de los problemas de infraestructura.
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# El [!DNL Infra] pestaña

El **[!DNL Infra]** La pestaña aísla los problemas y las causas de los problemas de infraestructura. Más adelante se describen los marcos que puede ver en la pestaña.

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Alertas de servicio](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

El **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** El gráfico muestra las alertas de servicio recopiladas por [!DNL New Relic] agente de infraestructura. Esto mostrará los reinicios del servicio, muchos asociados con las implementaciones.

## [!UICONTROL Inode usage by mount]

![Uso del nodo por montaje](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

El **[!UICONTROL Inode usage by mount]** muestra de cuadros [!DNL inode] uso por montaje en todo el periodo de tiempo seleccionado. Aunque puede haber mucho almacenamiento libre, si un nodo se queda sin [!DNL inodes], se mostrará una falta de almacenamiento disponible. La eliminación de archivos (especialmente los pequeños) liberará espacio y hará que [!DNL inodes] disponible.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![Vista del nivel de vCPU en el cronograma en las BUENAS dos semanas](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

El **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** El fotograma muestra la vista del nivel de vCPU en el periodo de tiempo seleccionado de más de dos semanas. Este marco examina el número de vCPU asignadas a la [!DNL New Relic] nombre de la aplicación mostrado.

## [!UICONTROL vCPU tier view over timeline]

![Vista de nivel de vCPU en línea de tiempo](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

El **[!UICONTROL vCPU tier view over timeline]** El fotograma muestra la vista del nivel de vCPU en el periodo de tiempo seleccionado de más de 24 horas. Este marco examina el número de vCPU asignadas a la [!DNL New Relic] nombre de la aplicación mostrado. Se mostrarán tanto las ampliaciones como las reducciones de tamaño de los clústeres.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![Vista del nivel de vCPU en la cronología por NODO](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

El **[!UICONTROL vCPU tier view over timeline BY NODE]** El marco muestra las vistas del nivel de vCPU en el periodo de tiempo seleccionado por nodo. Este marco es útil para detectar la pérdida de nodos o cuando los nodos se convierten o se reducen. La vista del nivel de vCPU sobre la línea de tiempo POR NODO, debería mirar la línea de tiempo MENOS de 24 horas.

## [!UICONTROL Instance details]

![Detalles de instancia](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

El **[!UICONTROL Instance details]** La tabla muestra los detalles de instancia de cada [!DNL New Relic] aplicación.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![non-responsive-node](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

El **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** el fotograma muestra nodos no adaptables a lo largo de un período de tiempo.
