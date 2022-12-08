---
title: "El [!DNL Infra] tab"
description: La variable [!DNL Infra] aísla los problemas y las causas de los problemas de infraestructura.
source-git-commit: 38467ebd2ec29f9e1679182fb1ee7076d738664b
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# La variable [!DNL Infra] ficha

La variable **[!DNL Infra]** aísla los problemas y las causas de los problemas de infraestructura. A continuación, se describen los marcos que se pueden ver en la pestaña .

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Alertas de servicio](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

La variable **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** el gráfico muestra las alertas de servicio recopiladas por [!DNL New Relic] agente de infraestructura. Esto mostrará los reinicios del servicio, muchos de ellos asociados con implementaciones.

## [!UICONTROL Inode usage by mount]

![Uso de nodos por montaje](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

La variable **[!UICONTROL Inode usage by mount]** muestras de marco [!DNL inode] uso por montaje en el intervalo de tiempo seleccionado. Aunque puede haber mucho almacenamiento libre, si un nodo se queda sin [!DNL inodes], mostrará una falta de almacenamiento disponible. La eliminación de archivos (especialmente pequeños) liberará espacio y creará [!DNL inodes] disponible.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![Vista de nivel de vCPU en la cronología BUENAS 2 semanas](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

La variable **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** frame muestra la vista de nivel de vCPU en el intervalo de tiempo seleccionado de más de dos semanas. Este marco observa el número de vCPUs asignadas al [!DNL New Relic] nombre de aplicación mostrado.

## [!UICONTROL vCPU tier view over timeline]

![Vista de nivel de vCPU en la cronología](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

La variable **[!UICONTROL vCPU tier view over timeline]** frame muestra la vista de nivel de vCPU en el intervalo de tiempo seleccionado de más de 24 horas. Este marco observa el número de vCPUs asignadas al [!DNL New Relic] nombre de aplicación mostrado. Mostrará tanto el tamaño ascendente como el bajo del clúster.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![Vista de nivel de vCPU en la cronología por NODE](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

La variable **[!UICONTROL vCPU tier view over timeline BY NODE]** frame muestra las vistas de nivel de vCPU en el intervalo de tiempo seleccionado por nodo. Este fotograma es útil para detectar la pérdida de nodos o cuando los nodos se actualizan o se reducen. La vista de nivel de vCPU sobre la cronología POR NODO, debería mirar la cronología MENOS de 24 horas.

## [!UICONTROL Instance details]

![Detalles de instancias](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

La variable **[!UICONTROL Instance details]** la tabla muestra los detalles de cada instancia [!DNL New Relic] aplicación.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![nodo no interactivo](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

La variable **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** frame muestra nodos no interactivos a lo largo de un período de tiempo.
