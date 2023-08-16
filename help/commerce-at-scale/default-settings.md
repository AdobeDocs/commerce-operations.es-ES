---
title: Optimización del rendimiento de Adobe Commerce
description: Prepare su proyecto de Adobe Commerce para utilizar Adobe Experience Manager as a CMS cambiando algunas configuraciones predeterminadas.
exl-id: 55d77af7-508c-4ef7-888b-00911cc6e920
feature: Integration, Cache
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---

# Optimización del rendimiento de Adobe Commerce

## AEM Ubicación geográfica de la infraestructura de Adobe Commerce y de la infraestructura de

AEM Para reducir la latencia entre el editor y Adobe Commerce GraphQL al crear páginas, el aprovisionamiento inicial de las dos infraestructuras independientes debe alojarse en la misma región de AWS (o Azure). La ubicación geográfica elegida para ambas nubes también debe ser la más cercana a la mayoría de la base de clientes, de modo que las solicitudes de GraphQL del lado del cliente se atiendan desde una ubicación geográficamente cercana a la mayoría de los clientes.

## Almacenamiento en caché de GraphQL en Adobe Commerce

AEM Cuando el explorador o el editor del usuario llama a GraphQL de Adobe Commerce, ciertas llamadas se almacenan en caché en Fastly. Las consultas que se almacenan en caché son generalmente las que contienen datos no personales y no es probable que cambien a menudo. Son, por ejemplo: categorías, categoryList y products. Las que no se almacenan explícitamente en caché son las que cambian regularmente y si se almacenan en caché podrían suponer riesgos para los datos personales y las operaciones del sitio, por ejemplo consultas como cart y customerPaymentTokens.

GraphQL le permite realizar varias consultas en una sola llamada. Es importante tener en cuenta que si especifica incluso una consulta que Adobe Commerce no almacena en caché con muchas otras que no se pueden almacenar en caché, Adobe Commerce omitirá la caché para todas las consultas de la llamada. Los desarrolladores deben tener esto en cuenta esto al combinar varias consultas para garantizar que las consultas potencialmente almacenables en caché no se omitan de forma involuntaria‡.

>[!NOTE]
>
> Para obtener más información sobre las consultas almacenables en caché y no almacenables en caché, consulte Adobe Commerce [documentación para desarrolladores](https://devdocs.magento.com/guides/v2.4/graphql/caching.html).

## Tabla plana del catálogo

No se recomienda el uso de mesas planas para productos y categorías. El uso de esta función obsoleta puede provocar degradaciones del rendimiento y problemas de indexación, por lo que el catálogo plano debe desactivarse a través del administrador de Adobe Commerce, en la sección de la tienda. Algunos módulos y personalizaciones de terceros no requieren tablas planas para funcionar correctamente. Se recomienda realizar una evaluación para comprender los impactos y los riesgos asociados con el uso de tablas planas al elegir utilizar estas extensiones o personalizaciones.

## Protección de origen rápido

De forma predeterminada, el blindaje de origen de Fastly no está habilitado. El propósito del blindaje de origen de Fastly es reducir el tráfico directamente al origen de Adobe Commerce: cuando se recibe una solicitud, una ubicación de Fastly edge (o &quot;punto de presencia&quot;/POP) comprueba el contenido almacenado en caché y lo proporciona. Si no se almacena en caché, continúa a Shield POP para comprobar si se almacena en caché allí (si el contenido se ha solicitado anteriormente incluso desde otro POP global, se almacenará en caché). Por último, si no se almacena en caché en el POP de escudo, solo entonces se dirigirá al servidor de origen.

El blindaje de origen de Fastly se puede habilitar en la configuración del servidor de administración de Adobe Commerce Fastly. Debe elegir una ubicación de blindaje más cercana al centro de datos de origen de Adobe Commerce para obtener el mejor rendimiento.

## Optimización rápida de imágenes

Una vez habilitado el blindaje de origen de Fastly, esto le permite activar también Fastly Image Optimizer. Cuando las imágenes del catálogo de productos se almacenan en Adobe Commerce, este servicio permite descargar todo el procesamiento de transformación de imágenes del catálogo de productos, que consume muchos recursos, en Rápido y fuera del origen de Adobe Commerce. Los tiempos de respuesta del usuario final también se mejoran para los tiempos de carga de la página, ya que las imágenes se transforman en la ubicación del perímetro, lo que elimina la latencia al reducir el número de solicitudes de vuelta al origen de Adobe Commerce.

La optimización de imágenes de Fastly se puede habilitar mediante &quot;habilitar la optimización de imágenes profundas&quot; en la configuración de Fastly en la administración, aunque solo después de que se haya activado el escudo de origen. Encontrará más detalles sobre las configuraciones para la optimización de imágenes rápida en Adobe Commerce [documentación para desarrolladores](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html).

![Captura de pantalla de la configuración de optimización de imágenes de Fastly en el administrador de Adobe Commerce](../assets/commerce-at-scale/image-optimization.svg)

## Deshabilitar módulos no utilizados

Si se ejecuta Adobe Commerce sin encabezado, solo se atienden solicitudes a través del extremo GraphQL y no se atienden páginas de tienda front-end directamente desde Adobe Commerce, entonces muchos módulos se vuelven redundantes y no se utilizan. Al deshabilitar los módulos no utilizados, el código base de Adobe Commerce se vuelve más pequeño, menos complejo y, por lo tanto, podría ofrecer mejoras de rendimiento. La desactivación de módulos en Adobe Commerce se puede administrar mediante Composer. Los módulos que se pueden deshabilitar dependerían de los requisitos del sitio y, por lo tanto, no se puede dar ninguna lista recomendada, ya que sería específica de la implementación de Adobe Commerce de cada cliente.

## Activación de la conexión MySQL y Redis

De forma predeterminada, las conexiones MySQL y Redis Slave no están activadas en Adobe Commerce en la nube. Esto se debe a que esta configuración solo es adecuada para clientes que esperan cargas muy altas. La latencia Cross-AZ (cross-Availability Zones) es mayor con conexiones esclavas activadas y, por lo tanto, esta configuración reduce el rendimiento de una Adobe Commerce en la instancia de la nube en el caso de que la instancia solo reciba niveles de carga regulares.

Si la instancia de Adobe Commerce espera una carga extrema, la activación del maestro-esclavo para MySQL y Redis ayudará al rendimiento al distribuir la carga en la base de datos MySQL o Redis en diferentes nodos.

Como guía, en entornos con carga normal, habilitar Slave Connections ralentiza el rendimiento en un 10-15 %. Sin embargo, en los clústeres con carga y tráfico intensos, existe un aumento del rendimiento de alrededor del 10-15 %. Por lo tanto, es importante cargar y probar el entorno con los niveles de tráfico esperados para evaluar si esta configuración sería beneficiosa para los tiempos de rendimiento bajo carga.

Para habilitar/deshabilitar conexiones esclavas para mysql y redis debe editar su `.magento.env.yaml` para incluir lo siguiente:

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

Para la arquitectura escalada (arquitectura dividida: consulte a continuación), las conexiones esclavas de Redis no deben habilitarse, ya que esto hará que aparezcan errores. En el caso de una arquitectura dividida, se recomienda implementar el almacenamiento en caché L2 para Redis.

## Migración a una Adobe Commerce con arquitectura escalada (dividida) en la nube

Si después de todas las configuraciones anteriores, los resultados de las pruebas de carga o el análisis del rendimiento de la infraestructura activa siguen indicando que los niveles de carga para Adobe Commerce son de un nivel que maximiza de manera consistente la CPU y otros recursos del sistema, entonces se debe considerar el cambio a una arquitectura escalada (dividida).

Con una arquitectura Pro estándar, hay 3 nodos, cada uno de los cuales contiene una pila tecnológica completa. Al convertir a la arquitectura de nivel dividido, esto cambia a un mínimo de 6 nodos: 3 de los cuales contienen Elasticsearch, MariaDB, Redis y otros servicios principales; los otros 3 para procesar tráfico web contienen phpfpm y NGINX. Existen mayores posibilidades de escalado con el nivel dividido: los nodos principales que contienen bases de datos se pueden escalar verticalmente; los nodos web se pueden escalar horizontal y verticalmente, lo que proporciona una gran flexibilidad para ampliar la infraestructura bajo demanda durante un período determinado de actividad de carga alta y en nodos donde se necesitan los recursos adicionales.

Si se ha tomado la decisión de cambiar a una arquitectura de nivel dividido debido a las expectativas de carga pesada para su sitio, se debe hablar con el equipo de cuenta de Adobe sobre los pasos para habilitar esto.
