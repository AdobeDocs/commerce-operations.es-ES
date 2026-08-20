---
title: Información general de almacenamiento en caché y opciones de configuración
description: Obtenga información acerca del almacenamiento en caché en Adobe Commerce, incluido el almacenamiento back-end, la configuración de front-end y el almacenamiento en caché de página completa con Varnish, Redis, Valkey y caché L2.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8c5dc151b00fd73e939c32fdc083fb0e8fc41dc8
workflow-type: tm+mt
source-wordcount: 536
ht-degree: 0%

---

# Información general de almacenamiento en caché y opciones de configuración

Adobe Commerce utiliza varias capas de almacenamiento en caché para reducir el procesamiento repetido, reducir la carga de la base de datos y mejorar los tiempos de respuesta. Estas capas funcionan en diferentes puntos de la solicitud y la entrega de recursos:

- **El almacenamiento en caché de aplicaciones** almacena datos generados o procesados mediante tipos de caché de Commerce.
- **El almacenamiento en caché de página completa HTTP** almacena respuestas HTTP completas antes de que lleguen a la aplicación Commerce.
- **El almacenamiento en caché L2** puede agregar una caché local en cada nodo web delante del almacenamiento de caché remoto compartido.
- El **almacenamiento en caché de contenido estático** permite a los navegadores reutilizar CSS, JavaScript, imágenes y otros recursos estáticos.

Esta página proporciona información general conceptual sobre estas capas y vínculos a sus directrices de configuración. Para obtener opciones de servidor, detalles de implementación y configuración específica de la versión, consulte [Opciones de servidor de caché y referencia de almacenamiento](cache-options.md).

## Almacenamiento en caché de capas

### Almacenamiento en caché de aplicaciones

El almacenamiento en caché de la aplicación Commerce está organizado como:

>[!BEGINSHADEBOX]

tipo de caché → caché front-end → back-end de caché

>[!ENDSHADEBOX]

Un tipo de caché **1&rbrace; identifica el tipo de datos que se almacenan en caché, como la configuración, el diseño, el bloque de HTML o el contenido de página completa.** Un **front-end de caché** conecta uno o más tipos de caché al almacenamiento. Un back-end de **caché** proporciona la implementación de almacenamiento.

Puede asignar diferentes tipos de caché a diferentes front-end cuando se requiera una configuración de caché o almacenamiento independiente. Para obtener detalles de configuración, consulte [Configurar tipos y front-end de caché](cache-types.md).

### Almacenamiento en caché HTTP de página completa

El almacenamiento en caché de página completa HTTP almacena las respuestas completas en la capa HTTP o CDN. Para implementaciones de producción:

- **Adobe Commerce local**—Adobe recomienda [Varnish](config-varnish.md) para el almacenamiento en caché de página completa. El barniz funciona como un proxy inverso delante del servidor web.
- **Adobe Commerce en la infraestructura de la nube** usa [Fastly](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/cdn/fastly){target="_blank"} para el nivel de almacenamiento en caché de Edge y de página completa. La infraestructura en la nube no utiliza un servicio Varnish administrado por separado.

>[!NOTE]
>
>El cambio del backend de la caché de la aplicación de Commerce no configura Barniz ni Fastly. El almacenamiento en caché HTTP de página completa se configura y administra de forma independiente de la caché de aplicaciones de bajo nivel.

### Almacenamiento en caché L2

El almacenamiento en caché L2, o de dos niveles, agrega una caché local en cada nodo web de Commerce mientras mantiene el almacenamiento de caché remoto compartido. Los datos a los que se accede con frecuencia se pueden servir localmente, lo que reduce la comunicación con la caché remota en implementaciones de varios nodos.

La configuración de L2 y las implementaciones admitidas varían según la versión y el tipo de implementación de Commerce. Para obtener más información, consulte [Configuración de caché L2](level-two-cache.md).

### Almacenamiento en caché de contenido estático

Commerce puede mejorar el almacenamiento en caché del explorador para recursos estáticos como CSS, JavaScript e imágenes añadiendo una versión de implementación a sus direcciones URL. Cuando el contenido cambia, la dirección URL cambia, lo que provoca que el explorador solicite el nuevo recurso en lugar de utilizar una copia en caché anterior.

## Configuración específica de la implementación

Las siguientes tareas de configuración varían según el tipo de implementación.

| Tarea | On-Premise | Infraestructura en nube |
| --- | --- | --- |
| Backends de caché de aplicaciones | [Opciones de servidor de caché y referencia de almacenamiento](cache-options.md) | [Prácticas recomendadas para la configuración de los servicios Valkey y Redis](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md) |
| Almacenamiento en caché de página completa HTTP | [Configurar barniz](config-varnish.md) | [Resumen de servicios de Fastly](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/cdn/fastly) |

Las siguientes tareas se aplican a todos los tipos de implementación:

- **Configurar tipos y frontends de caché** [Configurar frontends y tipos de caché](cache-types.md) para asociar tipos de caché con frontends de caché.
- **Configurar el almacenamiento en caché L2**—[Configuración de caché L2](level-two-cache.md).
- **Configurar la invalidación de caché del explorador para el contenido estático**—[Firma de contenido estático e invalidación de caché del explorador](static-content-signing.md).
