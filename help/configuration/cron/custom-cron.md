---
title: Trabajos de cron
description: Obtenga información sobre los grupos cron y la creación de un trabajo cron personalizado.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# Trabajos de cron

Estos temas tratan sobre cómo configurar un trabajo cron personalizado y, opcionalmente, un grupo cron personalizado. Si la extensión de comercio requiere que las tareas programadas se ejecuten periódicamente, puede utilizar estos temas para configurar un cron _trabajo_ (la tarea programada) y, opcionalmente, un cron _grupo_, que ejecuta tareas personalizadas al mismo tiempo.

Si utiliza un grupo cron proporcionado por Commerce, no tiene que definir un grupo cron personalizado; sin embargo, si desea que sus trabajos cron se ejecuten en una programación diferente o quiere que todos se ejecuten juntos, debe definir un grupo cron

La aplicación Commerce proporciona los siguientes grupos cron:

- `default`, que contiene la mayoría de los trabajos cron
- `index`, que se actualiza [indexadores](../cli/manage-indexers.md)
- `consumers`, que ejecuta la cola de mensajes [consumidores](../cli/start-message-queues.md)
- Estos temas solo están disponibles en Adobe Commerce
   - `staging`, que se ejecuta [Relacionado con ensayo](https://docs.magento.com/user-guide/cms/content-staging.html) tasks
   - `catalog_event`, que ejecuta tareas para reglas de segmentación y carro de compras
