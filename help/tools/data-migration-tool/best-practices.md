---
title: Prácticas recomendadas de migración de datos
description: Siga estas prácticas recomendadas de migración de datos para garantizar una actualización correcta de Magento 1 a Magento 2.
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Prácticas recomendadas de migración de datos

En esta sección se proporcionan recomendaciones recomendadas para acelerar y simplificar la migración, así como instrucciones sobre la cantidad de tiempo que puede tardar.

* **Utilizar una copia de la base de datos desde una instancia de Magento 1** al realizar pruebas de migración. No utilice la instancia de producción de la base de datos del almacén de Magento 1.

* **Eliminación de datos obsoletos y redundantes** de la base de datos de Magento 1 antes de la migración.

Estos datos pueden incluir registros, presupuestos de pedidos, productos vistos o comparados recientemente, visitantes, categorías específicas de eventos y reglas promocionales.

* **Siga las [reglas generales para una migración correcta](migrate-data/overview.md#migration-overview)**.

* Para mejorar el rendimiento, **habilite el `direct_document_copy` opción** en su `config.xml` archivo:

   ```xml
   <direct_document_copy>1</direct_document_copy>
   ```

>[!NOTE]
>
>Las bases de datos de Magento 1 y Magento 2 deben estar ubicadas en el mismo servidor MySQL y la cuenta de la base de datos debe tener acceso a ambas.

## Estimaciones comparativas

El Adobe ha probado la migración de datos en el siguiente sistema:

* Virtual Box VM, CentOS 6, 2,5 GB de RAM, CPU 1 núcleo a 2,6 GHz
* Base de datos con 177 000 productos, 355 000 pedidos y 214 000 clientes

## Resultados de rendimiento

* Tiempo de migración de la configuración: ~10 minutos
* Tiempo de migración de datos: ~9 horas (todos los datos excepto las reescrituras de URL, ~85% del total de datos)
* Cálculo del tiempo de inactividad del sitio: unos minutos para reindexar y cambiar la configuración de DNS. Tiempo adicional necesario para calentar la caché de la página.
