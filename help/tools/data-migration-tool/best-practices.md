---
title: Prácticas recomendadas de migración de datos
description: Siga estas prácticas recomendadas de migración de datos para garantizar una actualización correcta de Magento 1 a Magento 2.
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%
---
# Prácticas recomendadas de migración de datos

En esta sección se proporcionan recomendaciones recomendadas para acelerar y simplificar la migración, así como instrucciones sobre la cantidad de tiempo que puede tardar.

* **Use una copia de la base de datos de una instancia de Magento 1** al realizar las pruebas de migración. No utilice la instancia de producción de la base de datos de la tienda Magento 1.

* **Elimine datos redundantes y obsoletos** de la base de datos de Magento 1 antes de la migración.

Estos datos pueden incluir registros, presupuestos de pedidos, productos vistos o comparados recientemente, visitantes, categorías específicas de eventos y reglas promocionales.

* **Siga las [reglas generales para una migración correcta](migrate-data/overview.md#migration-overview)**.

* Para mejorar el rendimiento, **habilite la opción `direct_document_copy`** en el archivo `config.xml`:

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>Las bases de datos de Magento 1 y Magento 2 deben estar ubicadas en el mismo servidor MySQL y la cuenta de la base de datos debe tener acceso a ambas bases de datos.

## Estimaciones comparativas

Adobe ha probado la migración de datos en el siguiente sistema:

* Virtual Box VM, CentOS 6, 2,5 GB de RAM, CPU 1 núcleo a 2,6 GHz
* Base de datos con 177 000 productos, 355 000 pedidos y 214 000 clientes

## Resultados de rendimiento

* Tiempo de migración de la configuración: ~10 minutos
* Tiempo de migración de datos: ~9 horas (todos los datos excepto las reescrituras de URL, ~85% del total de datos)
* Cálculo del tiempo de inactividad del sitio: unos minutos para reindexar y cambiar la configuración de DNS. Tiempo adicional necesario para calentar la caché de la página.
