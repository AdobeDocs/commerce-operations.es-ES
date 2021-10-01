---
title: Optimización del rendimiento del comercio de Adobe
description: Prepare su proyecto de Adobe Commerce para utilizar Adobe Experience Manager como CMS cambiando algunos ajustes predeterminados.
source-git-commit: 63f153365398c3ae7dc7e6214b67705c8a4c7686
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Optimización del rendimiento de Adobe Commerce

## Ubicación geográfica de la infraestructura de comercio de AEM y Adobe

Para reducir la latencia entre el editor de AEM y Adobe Commerce GraphQL al crear páginas, el aprovisionamiento inicial de las dos infraestructuras independientes debe alojarse en la misma región de AWS (o Azure). La ubicación geográfica elegida para ambas nubes también debe ser la más cercana a la mayoría de la base de clientes, de modo que las solicitudes de GraphQL del lado del cliente se proporcionen desde una ubicación geográficamente cercana a la mayoría de sus clientes.

## Almacenamiento en caché de GraphQL en Adobe Commerce

Cuando el navegador del usuario o AEM editor llama a GraphQL de Adobe Commerce, determinadas llamadas se almacenan en caché
en último lugar. Las consultas que se almacenan en caché generalmente son aquellas que contienen datos no personales y no es probable que cambien con frecuencia. Estos son, por ejemplo: categorías, categoryList y productos. Aquellos que explícitamente no se almacenan en caché son aquellos que cambian regularmente y si se almacenan en caché podrían representar riesgos para los datos personales y las operaciones del sitio, por ejemplo, consultas como cart y customerPaymentTokens.

GraphQL permite realizar varias consultas en una sola llamada. Es importante tener en cuenta que si especifica incluso una consulta que Adobe Commerce no almacena en caché con muchas otras que no se pueden almacenar en caché, Adobe Commerce omitirá la caché para todas las consultas de la llamada. Los desarrolladores deben tener esto en cuenta al combinar varias consultas para garantizar que las consultas que puedan almacenarse en caché no se omitan de forma involuntaria }.

>[!NOTE]
>
> Para obtener más información sobre las consultas almacenables en caché y no almacenables en caché, consulte la documentación para desarrolladores de Adobe Commerce [a1/>.](https://devdocs.magento.com/guides/v2.4/graphql/caching.html)

## Tabla plana del catálogo

No se recomienda el uso de tablas planas para productos y categorías. El uso de esta función obsoleta puede provocar problemas de degradación del rendimiento y de indexación, por lo que el catálogo plano debe deshabilitarse a través del administrador de comercio de Adobe, en la sección de tienda. Algunos módulos y personalizaciones de terceros requieren tablas planas para funcionar correctamente - se recomienda realizar una evaluación para comprender los impactos y riesgos asociados con tener que usar tablas planas al elegir utilizar estas extensiones o personalizaciones.

## Protector de origen rápido

De forma predeterminada, la protección de origen rápido no está activada. El objetivo de la protección de origen de Finfinidad es reducir el tráfico directamente al origen del comercio de Adobe: cuando se recibe una solicitud, una ubicación de borde de infinito (o &quot;punto de presencia&quot;/POP) comprueba el contenido en caché y lo proporciona. Si no se almacena en caché, continúa con el Shield POP para comprobar si se almacena en caché allí (si el contenido se ha solicitado anteriormente incluso desde otro POP global, se almacenará en caché). Por último, si no se almacena en caché en el Shield POP, solo entonces procederá al servidor de origen.

El blindaje de origen rápido se puede habilitar en la configuración del servidor back-end de administración de Adobe Commerce. Debe elegir una ubicación de escudo que esté más cerca de su centro de datos de origen de Adobe Commerce para obtener el mejor rendimiento.

## Optimización de imágenes más rápidas

Una vez habilitado el blindaje de origen rápido, esto le permite activar también el Optimizador de imagen rápido. Cuando las imágenes del catálogo de productos se almacenan en Adobe Commerce, este servicio permite descargar todos los recursos intensivos, el procesamiento de la transformación de las imágenes del catálogo de productos en Finfinito y fuera del origen de Adobe Commerce. Los tiempos de respuesta del usuario final también se mejoran para los tiempos de carga de las páginas, ya que las imágenes se transforman en la ubicación perimetral, lo que elimina la latencia al reducir el número de solicitudes de vuelta al origen de Adobe Commerce.

La optimización de imágenes más rápida se puede habilitar &quot;habilitar la optimización de imágenes profundas&quot; en la configuración de FAdministración, aunque solo después de activar el blindaje de origen. Encontrará más información sobre las configuraciones para la optimización de FAdministración de imágenes en la [documentación para desarrolladores](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) de Adobe Commerce.

![Captura de pantalla de los ajustes de optimización de imágenes de Adobe Commerce Admin](../assets/commerce-at-scale/image-optimization.svg)

## Deshabilitar módulos no utilizados

Si se ejecuta Adobe Commerce sin encabezado, solo se sirven solicitudes a través del extremo GraphQL y no se proporcionan páginas de tienda de front-end directamente desde Adobe Commerce, entonces muchos módulos se vuelven redundantes y no se utilizan. Al deshabilitar los módulos no utilizados, la base de código de comercio de Adobe se vuelve más pequeña, menos compleja y, por lo tanto, podría ofrecer mejoras de rendimiento. La desactivación de módulos en Adobe Commerce se puede administrar con el compositor. Los módulos que se pueden deshabilitar dependerán de los requisitos del sitio y, por lo tanto, no se puede proporcionar ninguna lista recomendada, ya que sería específica para la implementación de Adobe Commerce por parte de cada cliente.

## Activación de conexión MySQL y Redis

De forma predeterminada, las conexiones esclavas MySQL y Redis no están activadas en Adobe Commerce en la nube. Esto se debe a que estos ajustes solo son adecuados para clientes que esperan una carga muy alta. La latencia entre zonas de disponibilidad es mayor con las conexiones esclavas activadas y, por lo tanto, esta configuración reduce el rendimiento de un comercio de Adobe en la instancia de nube en el caso de que la instancia solo reciba niveles de carga normales.

Si la instancia de Adobe Commerce espera una carga extrema, la activación del maestro esclavo para MySQL y Redis ayudará con el rendimiento al distribuir la carga en la base de datos MySQL o Redis en diferentes nodos.

Como guía, en entornos con carga normal, habilitar Conexiones esclavas reducirá el rendimiento en un 10-15%. Sin embargo, en los clústeres con una carga y un tráfico elevados, existe un aumento del rendimiento de alrededor del 10-15%. Por lo tanto, es importante que cargue la prueba del entorno con los niveles de tráfico esperados para evaluar si esta configuración sería beneficiosa para los tiempos de rendimiento en carga.

Para habilitar/deshabilitar conexiones esclavas para mysql y redis, debe editar su archivo `.magento.env.yaml` para incluir lo siguiente:

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

En el caso de la arquitectura escalada (arquitectura dividida, consulte a continuación), las conexiones esclavas de Redis no deben estar habilitadas, ya que esto provocará que aparezcan errores. En el caso de una arquitectura dividida, se recomienda implementar el almacenamiento en caché L2 para Redis.

## Migración a un Adobe Commerce en una arquitectura escalada en la nube (dividida)

Si después de todas las configuraciones anteriores, los resultados de las pruebas de carga o el análisis del rendimiento de la infraestructura activa siguen indicando que los niveles de carga en Adobe Commerce son de un nivel que maximice constantemente la CPU y otros recursos del sistema, entonces se debe considerar el paso a una arquitectura escalada (dividida).

Con una arquitectura Pro estándar, hay 3 nodos, cada uno de los cuales contiene una pila de tecnología completa. Al convertir en arquitectura de niveles divididos, esto cambia a un mínimo de 6 nodos: 3 de los cuales contienen Elasticsearch, MariaDB, Redis y otros servicios principales; los otros 3 para procesar tráfico web contienen phpfpm y NGINX. Existen buenas posibilidades de escalado con el nivel dividido: los nodos principales que contienen bases de datos pueden escalarse verticalmente; los nodos web se pueden escalar horizontal y verticalmente, lo que proporciona una gran flexibilidad para expandir la infraestructura bajo demanda durante un período de actividad de carga alta y en los nodos donde se necesitan los recursos adicionales.

Si se ha tomado la decisión de cambiar a una arquitectura de niveles divididos debido a las grandes expectativas de carga de su sitio, entonces debería realizarse un análisis con su gestor de éxito de clientes sobre los pasos para habilitarlo.