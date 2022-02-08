---
title: Recommendations de optimización del rendimiento
description: Optimice el rendimiento de su implementación de Adobe Commerce siguiendo estas recomendaciones.
exl-id: c5d62e23-be43-4eea-afdb-bb1b156848f9
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Revisión de la optimización del rendimiento

Aunque la optimización del rendimiento puede proceder de muchos aspectos, hay algunas recomendaciones generales que deben tenerse en cuenta en la mayoría de los casos. Esto incluye la optimización de la configuración para elementos de infraestructura, la configuración back-end de Adobe Commerce y la planificación de la escalabilidad de la arquitectura.

## Infraestructura

Las secciones siguientes describen recomendaciones para optimizar la infraestructura.

### Búsquedas de DNS

La búsqueda de DNS es el proceso de búsqueda de la dirección IP a la que pertenece el nombre de dominio. El explorador debe esperar hasta que se complete la búsqueda de DNS para poder descargar cualquier cosa para cada solicitud. La reducción de búsquedas de DNS es importante para mejorar los tiempos generales de carga de las páginas.

### Red de distribución de contenido (CDN)

Utilice una CDN para optimizar el rendimiento de descarga de recursos. Adobe Commerce utiliza Fray. Si tiene una implementación local de Adobe Commerce, también debe considerar la posibilidad de agregar una capa de CDN.

### Latencia web

La ubicación del centro de datos afecta a la latencia web de los usuarios de front-end.

### Ancho de banda de la red

El ancho de banda de red suficiente es uno de los requisitos clave para el intercambio de datos entre nodos web, bases de datos, servidores de almacenamiento en caché/sesión y otros servicios.

Como Adobe Commerce aprovecha de forma eficaz el almacenamiento en caché para obtener un alto rendimiento, su sistema puede intercambiar datos de forma activa con servidores de almacenamiento en caché como Redis. Si Redis está ubicado en un servidor remoto, debe proporcionar un canal de red suficiente entre los nodos web y el servidor caché para evitar cuellos de botella en las operaciones de lectura y escritura.

### Sistema operativo (OS)

Las configuraciones y optimizaciones del sistema operativo son similares para Adobe Commerce en comparación con otras aplicaciones web de carga alta. A medida que aumenta el número de conexiones simultáneas gestionadas por el servidor, el número de sockets disponibles se puede asignar completamente.

### CPU de nodos web

Un núcleo de CPU puede servir entre 2 y 4 solicitudes de Adobe Commerce sin caché de forma efectiva. Para determinar cuántos nodos o núcleos web necesitaban para procesar todas las solicitudes entrantes sin ponerlas en cola, utilice la ecuación :

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### Configuración de PHP-FPM

La optimización de esta configuración depende de los resultados de la prueba de rendimiento de diferentes proyectos.

- **ByteCode**: para obtener la máxima velocidad de Adobe Commerce en PHP 7, debe activar el `opcache` y configúrelo correctamente.

- **APCU**—Recomendamos habilitar la extensión PHP APCu y configurar Composer para optimizar para el máximo rendimiento. Esta extensión almacena en caché las ubicaciones de archivos para los archivos abiertos, lo que aumenta el rendimiento de las llamadas al servidor de Adobe Commerce, incluidas las páginas, las llamadas de Ajax y los extremos.

- **Realpath_cacheconfiguration**—Optimización `realpath_cache` permite que los procesos PHP almacenen en caché las rutas a los archivos en lugar de buscarlos cada vez que se carga una página.

### Servidor web

Solo se necesita una ligera reconfiguración para usar nginx como servidor web. El servidor web nginx proporciona un mejor rendimiento y es fácil de configurar mediante el archivo de configuración de ejemplo de Adobe Commerce ([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)).

- Configuración correcta de PHP-FPM con TCP

- Habilitar HTTP/2 y Gzip

- Optimizar conexiones de trabajo

### Base de datos

Este documento no proporciona instrucciones detalladas de ajuste MySQL porque cada tienda y entorno es diferente, pero podemos hacer algunas recomendaciones generales.

La base de datos de Adobe Commerce (así como cualquier otra base de datos) es sensible a la cantidad de memoria disponible para almacenar datos e índices. Para aprovechar efectivamente la indexación de datos MySQL, la cantidad de memoria disponible debería ser, como mínimo, casi la mitad del tamaño de los datos almacenados en la base de datos.

Optimice el `innodb_buffer_pool_instances` para evitar problemas con varios subprocesos que intentan acceder a la misma instancia. El valor de la variable `max_connections` debe correlacionarse con el número total de subprocesos PHP configurados en el servidor de aplicaciones. Utilice la fórmula siguiente para calcular el mejor valor de `innodb-thread-concurrency`:

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### Almacenamiento en caché de sesión

El almacenamiento en caché de sesión es un buen candidato para configurar para una instancia separada de Redis. La configuración de memoria para este tipo de caché debe tener en cuenta la estrategia de abandono del carro de compras del sitio y el tiempo que una sesión debe esperar permanecer en la caché.

Redis debería tener suficiente memoria asignada para guardar todas las demás cachés en la memoria para un rendimiento óptimo. La caché de bloques será el factor clave para determinar la cantidad de memoria que se configurará. La caché de bloque crece en relación con el número de páginas en un sitio (número de SKU x número de vistas de tienda).

### Almacenamiento en caché de página

Recomendamos encarecidamente utilizar Varnish para la caché de página completa en su tienda Adobe Commerce. La variable `PageCache` aún está presente en la base de código, pero solo debe utilizarse para fines de desarrollo.

Instale Varnish en un servidor separado delante del nivel web. Debe aceptar todas las solicitudes entrantes y proporcionar copias de páginas en caché. Para permitir que Varnish funcione eficazmente con las páginas seguras, se puede colocar un proxy de terminación SSL delante de Varnish. Nginx puede utilizarse para este fin.

Aunque la invalidación de memoria caché de página completa de Varnish es efectiva, recomendamos asignar suficiente memoria a Varnish para guardar las páginas más populares en la memoria.

### Cola de mensajes

El marco de colas de mensajes (MQF) es un sistema que permite que un módulo publique mensajes en las colas. También define a los consumidores que reciben los mensajes de forma asíncrona. Adobe Commerce es compatible con RabbitMQ como agente de mensajería, que proporciona una plataforma escalable para enviar y recibir mensajes.

### Pruebas y monitorización del rendimiento

Siempre se recomienda realizar pruebas de rendimiento antes de cada versión de producción para obtener una estimación de la capacidad de su plataforma de comercio electrónico. Mantenga el monitoreo después del lanzamiento y tenga un plan de escalabilidad y backup para administrar las horas de mayor actividad.

>[!NOTE]
>
> Adobe Commerce en la infraestructura de la nube ya aplica todas las optimizaciones de infraestructura y arquitectura anteriores, excepto la búsqueda de DNS porque está fuera de alcance.

### Buscar

Elasticsearch es necesario desde la versión 2.4 de Adobe Commerce, pero también se recomienda habilitarlo para versiones anteriores a la 2.4.

## Modelos operativos

Además de las recomendaciones comunes de optimización de infraestructura mencionadas anteriormente, también existen enfoques para mejorar el rendimiento para modos y escalas de negocio específicos. Este documento no proporciona instrucciones de ajuste detalladas para todos ellos porque cada escenario es diferente, pero podemos proporcionar algunas opciones de alto nivel para su referencia.

### Arquitectura sin encabezado

Tenemos una sección separada dedicada a detallar qué [headless](../../architecture/headless/adobe-commerce.md) es y diferentes opciones. En resumen, separa la capa de tienda de la propia plataforma. Sigue siendo el mismo servidor, pero Adobe Commerce ya no procesa las solicitudes directamente y solo admite tiendas personalizadas a través de la API de GraphQL.

### Mantener Adobe Commerce actualizado

Adobe Commerce siempre tiene un mejor rendimiento al ejecutar la versión más reciente. Aunque no sea posible mantener Adobe Commerce actualizado después de publicar cada nueva versión, se recomienda [actualización](../../../upgrade/overview.md) cuando Adobe Commerce introduce optimizaciones de rendimiento significativas.

Por ejemplo, en 2020, Adobe lanzó una optimización en la capa de Redis, solucionando muchas ineficiencias, problemas de conexión y transferencia de datos innecesaria entre Redis y Adobe Commerce. El rendimiento general entre 2.3 y 2.4 es de noche y día y hemos visto mejoras significativas en el carro de compras, el cierre de compra y los usuarios simultáneos, solo debido a la optimización de Redis.

### Optimizar modelo de datos

Muchos problemas se originan en los datos, incluidos los modelos de datos incorrectos, los datos que no están estructurados correctamente y los datos que no tienen un índice.

Se ve bien si está probando algunas conexiones, pero se ve en producción cuando el tráfico real entra y aquí es donde entra la lentitud. Es muy importante que los integradores de sistemas sepan cómo diseñar un modelo de datos (especialmente para atributos de producto), evitar agregar atributos innecesarios y mantener atributos obligatorios que afecten a la lógica empresarial (como precios, disponibilidad de existencias y búsqueda).

Para aquellos atributos que no afectan a la lógica empresarial pero que aún necesitan estar presentes en la tienda, combínelos en algunos atributos (por ejemplo, formato JSON).

Para optimizar el rendimiento de la plataforma, si la lógica empresarial no es necesaria en la tienda a partir de datos o atributos tomados de un PIM o un ERP, no es necesario agregar ese atributo a Adobe Commerce.

### Diseño para escalabilidad

Esto es importante para las empresas que ejecutan campañas y que enfrentan tiempos de mayor actividad a menudo. Para que la arquitectura y el diseño de las aplicaciones sean fáciles de escalar, esto puede aumentar los recursos durante las horas de mayor actividad y reducirlos después.
