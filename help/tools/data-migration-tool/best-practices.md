---
title: Prácticas recomendadas para la migración de datos
description: Siga estas prácticas recomendadas de migración de datos para garantizar una actualización correcta del Magento 1 al Magento 2.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Prácticas recomendadas para la migración de datos

Esta sección proporciona las mejores recomendaciones para acelerar y simplificar la migración, así como instrucciones sobre cuánto tiempo puede tardar.

* **Usar una copia de la base de datos de una instancia de Magento 1** al realizar pruebas de migración. No utilice la instancia de producción de la base de datos del almacén de Magento 1.

* **Eliminación de datos redundantes y obsoletos** de la base de datos de Magento 1 antes de la migración.

Estos datos pueden incluir registros, presupuestos de pedidos, productos vistos recientemente o comparados, visitantes, categorías específicas del evento y reglas promocionales.

* **Siga las [reglas generales para una migración correcta](migrate-data/overview.md#migration-overview)**.

* Para mejorar el rendimiento, **habilite el `direct_document_copy` option** en su `config.xml` archivo:

   ```xml
   <direct_document_copy>1</direct_document_copy>
   ```

>[!NOTE]
>
>Las bases de datos Magento 1 y Magento 2 deben estar ubicadas en el mismo servidor MySQL y la cuenta de la base de datos debe tener acceso a ambas bases de datos.

## Estimaciones de referencia

Adobe ha probado la migración de datos en el siguiente sistema:

* VM de caja virtual, CentOS 6, 2,5 GB de RAM, CPU 1 núcleo 2,6 GHz
* Base de datos con 177.000 productos, 355.000 pedidos y 214.000 clientes

## Resultados de rendimiento

* Tiempo de migración de la configuración: ~10 minutos
* Tiempo de migración de datos: ~9 horas (todos los datos excepto reescrituras de URL, ~85% de los datos totales)
* Estimación del tiempo de inactividad del sitio: unos minutos para reindexar y cambiar la configuración de DNS. Tiempo adicional necesario para calentar la caché de la página.
