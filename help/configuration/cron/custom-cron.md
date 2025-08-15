---
title: Trabajos cron
description: Obtenga información acerca de los grupos de cron y la creación de un trabajo de cron personalizado.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Trabajos cron

En estos temas se explica cómo configurar un trabajo cron personalizado y, opcionalmente, un grupo cron personalizado. Si la extensión de Commerce requiere que las tareas programadas se ejecuten periódicamente, puede utilizar estos temas para configurar un _trabajo_ cron (la tarea programada) y, opcionalmente, un _grupo_ cron, que ejecuta tareas personalizadas al mismo tiempo.

Si utiliza un grupo cron proporcionado por Commerce, no tiene que definir un grupo cron personalizado; sin embargo, si desea que sus trabajos cron se ejecuten en una programación diferente o desea que todos se ejecuten juntos, debe definir un grupo cron

La aplicación de Commerce proporciona los siguientes grupos cron:

- `default`, que contiene la mayoría de los trabajos cron
- `index`, que actualiza [indexadores](../cli/manage-indexers.md)
- `consumers`, que ejecuta la cola de mensajes [consumidores](../cli/start-message-queues.md)
- Estos temas solo están disponibles en Adobe Commerce
   - `staging`, que ejecuta [tareas relacionadas con el ensayo](https://experienceleague.adobe.com/es/docs/commerce-admin/content-design/staging/content-staging)
   - `catalog_event`, que ejecuta tareas para el destino y reglas del carro de compras
