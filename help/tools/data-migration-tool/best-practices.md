---
title: Prácticas recomendadas de migración de datos
description: Siga estas prácticas recomendadas de migración de datos para garantizar una actualización correcta de Magento 1 a Magento 2.
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Prácticas recomendadas de migración de datos

En esta sección se proporcionan recomendaciones recomendadas para acelerar y simplificar la migración, así como instrucciones sobre la cantidad de tiempo que puede tardar.

* **Use una copia de la base de datos de una instancia de Magento 1** al realizar las pruebas de migración. No utilice la instancia de producción de la base de datos de la tienda Magento 1.

* **Elimine los datos redundantes y obsoletos** de la base de datos de Magento 1 antes de la migración.

Estos datos pueden incluir registros, presupuestos de pedidos, productos vistos o comparados recientemente, visitantes, categorías específicas de eventos y reglas promocionales.

* **Siga las [reglas generales para una migración correcta](migrate-data/overview.md#migration-overview)**.

* Para mejorar el rendimiento, **habilite la opción `direct_document_copy`** en el archivo `config.xml`:

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>Las bases de datos Magento 1 y Magento 2 deben estar ubicadas en el mismo servidor MySQL y la cuenta de la base de datos debe tener acceso a ambas.

## Estimaciones comparativas

Adobe ha probado la migración de datos en el siguiente sistema:

* Virtual Box VM, CentOS 6, 2,5 GB de RAM, CPU 1 núcleo a 2,6 GHz
* Base de datos con 177 000 productos, 355 000 pedidos y 214 000 clientes

## Resultados de rendimiento

* Tiempo de migración de la configuración: ~10 minutos
* Tiempo de migración de datos: ~9 horas (todos los datos excepto las reescrituras de URL, ~85% del total de datos)
* Cálculo del tiempo de inactividad del sitio: unos minutos para reindexar y cambiar la configuración de DNS. Tiempo adicional necesario para calentar la caché de la página.
