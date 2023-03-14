---
title: Recommendations de optimización de rendimiento
description: Optimice el rendimiento de su implementación de Adobe Commerce siguiendo estas recomendaciones.
exl-id: c5d62e23-be43-4eea-afdb-bb1b156848f9
source-git-commit: 821ef18c1b0f00a6b9574be968ad76f0c230335c
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 0%

---

# Revisión de optimización de rendimiento

Aunque la optimización del rendimiento puede provenir de muchos aspectos, hay algunas recomendaciones generales que deben tenerse en cuenta en la mayoría de los casos. Esto incluye la optimización de la configuración para elementos de infraestructura, la configuración del back-end de Adobe Commerce y la planificación de la escalabilidad de la arquitectura.

## Infraestructura

Las secciones siguientes describen recomendaciones para optimizaciones de infraestructura.

### Búsquedas DNS

La búsqueda DNS es el proceso de encontrar a qué dirección IP pertenece el nombre de dominio. El explorador debe esperar hasta que se complete la búsqueda de DNS para poder descargar cualquier elemento para cada solicitud. Reducir las búsquedas DNS es importante para mejorar los tiempos generales de carga de las páginas.

### Red de entrega de contenido (CDN)

Utilice una CDN para optimizar el rendimiento de descarga de recursos. Adobe Commerce utiliza Fastly. Si tiene una implementación local de Adobe Commerce, también debe considerar la posibilidad de agregar una capa de CDN.

### Latencia web

La ubicación del centro de datos afecta a la latencia web de los usuarios de front-end.

### Ancho de banda de red

Un ancho de banda de red suficiente es uno de los requisitos clave para el intercambio de datos entre nodos web, bases de datos, servidores de almacenamiento en caché/sesión y otros servicios.

Dado que Adobe Commerce aprovecha de forma eficaz el almacenamiento en caché para obtener un alto rendimiento, su sistema puede intercambiar datos de forma activa con servidores de almacenamiento en caché como Redis. Si Redis se encuentra en un servidor remoto, debe proporcionar un canal de red suficiente entre los nodos web y el servidor de almacenamiento en caché para evitar cuellos de botella en las operaciones de lectura y escritura.

### Sistema operativo (SO)

Las configuraciones y optimizaciones del sistema operativo son similares para Adobe Commerce en comparación con otras aplicaciones web de alta carga. A medida que aumenta el número de conexiones simultáneas gestionadas por el servidor, el número de sockets disponibles puede asignarse por completo.

### CPU de nodos web

Un núcleo de CPU puede servir alrededor de 2-4 solicitudes de Adobe Commerce sin caché de manera efectiva. Para determinar cuántos nodos/núcleos web se necesitan para procesar todas las solicitudes entrantes sin ponerlas en cola, utilice la ecuación:

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### Configuración de PHP-FPM

La optimización de esta configuración depende de los resultados de las pruebas de rendimiento de los distintos proyectos.

- **ByteCode**—Para obtener la máxima velocidad de Adobe Commerce en PHP 7, debes activar el `opcache` y configúrelo correctamente.

- **APCU**—Recomendamos activar la extensión PHP APCu y configurar Composer para optimizar el rendimiento máximo. Esta extensión almacena en caché las ubicaciones de los archivos abiertos, lo que aumenta el rendimiento de las llamadas al servidor de Adobe Commerce, incluidas las páginas, las llamadas de Ajax y los extremos.

- **Realpath_cacheconfiguration**—Optimizando `realpath_cache` permite que los procesos de PHP almacenen en caché las rutas a los archivos en lugar de buscarlos cada vez que se carga una página.

### Servidor web

Solo se necesita una ligera reconfiguración para utilizar nginx como servidor web. El servidor web nginx proporciona un mejor rendimiento y es fácil de configurar mediante el archivo de configuración de muestra de Adobe Commerce ([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)).

- Configurar PHP-FPM con TCP correctamente

- Habilitar HTTP/2 y Gzip

- Optimización de conexiones de trabajo

### Base de datos

Este documento no proporciona instrucciones detalladas de ajuste MySQL porque cada tienda y entorno es diferente, pero podemos hacer algunas recomendaciones generales.

La base de datos de Adobe Commerce (así como cualquier otra base de datos) es sensible a la cantidad de memoria disponible para almacenar datos e índices. Para aprovechar eficazmente la indexación de datos MySQL, la cantidad de memoria disponible debe ser, como mínimo, cercana a la mitad del tamaño de los datos almacenados en la base de datos.

Optimización del `innodb_buffer_pool_instances` configuración para evitar problemas con varios subprocesos que intentan acceder a la misma instancia. El valor del `max_connections` Este parámetro debe correlacionarse con el número total de hilos PHP configurados en el servidor de aplicaciones. Utilice la siguiente fórmula para calcular el mejor valor para `innodb-thread-concurrency`:

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### Almacenamiento en caché de sesión

El almacenamiento en caché de sesión es un buen candidato para configurar para una instancia independiente de Redis. La configuración de memoria para este tipo de caché debe tener en cuenta la estrategia de abandono del carro de compras del sitio y el tiempo que debe esperar una sesión para permanecer en la caché.

Redis debería tener suficiente memoria asignada para guardar todas las demás cachés en la memoria para un rendimiento óptimo. La caché de bloques será el factor clave para determinar la cantidad de memoria que se va a configurar. La caché de bloques aumenta en relación con el número de páginas de un sitio (número de SKU x número de vistas de tiendas).

### Almacenamiento en caché de página

Recomendamos encarecidamente usar Barnish para almacenar toda la información de la página en su tienda Adobe Commerce. El `PageCache` El módulo de sigue presente en el código base, pero solo debe utilizarse para fines de desarrollo.

Instale Varnish en un servidor separado frente al nivel web. Debe aceptar todas las solicitudes entrantes y proporcionar copias de las páginas en caché. Para permitir que Varnish funcione eficazmente con páginas seguras, se puede colocar un proxy de terminación SSL delante de Varnish. Nginx se puede utilizar para este fin.

Aunque la invalidación de la memoria caché de la página completa de Varnish es efectiva, recomendamos asignar suficiente memoria a Varnish para guardar las páginas más populares en la memoria.

### Colas de mensajes

Message Queue Framework (MQF) es un sistema que permite a un módulo publicar mensajes en colas. También define los consumidores que reciben los mensajes de forma asincrónica. Adobe Commerce admite [!DNL RabbitMQ] como agente de mensajería, que proporciona una plataforma escalable para enviar y recibir mensajes.

### Pruebas y monitorización del rendimiento

Siempre se recomienda realizar pruebas de rendimiento antes de cada versión de producción para obtener una estimación de la capacidad de su plataforma de comercio electrónico. Mantenga la monitorización después del lanzamiento y tenga un plan de escalabilidad y copia de seguridad para administrar las horas de mayor actividad.

>[!NOTE]
>
> Adobe Commerce en la infraestructura de la nube ya aplica todas las optimizaciones de infraestructura y arquitectura anteriores, excepto la búsqueda de DNS porque está fuera de ámbito.

### Buscar {#search-heading}

Se requiere Elasticsearch (o OpenSearch) a partir de la versión 2.4 de Adobe Commerce, pero también se recomienda habilitarlo para las versiones anteriores a la 2.4.

## Modelos operativos

Aparte de las recomendaciones comunes de optimización de la infraestructura mencionadas anteriormente, también existen enfoques para mejorar el rendimiento para modos y escalas de negocio específicos. Este documento no proporciona instrucciones de ajuste detalladas para todos ellos porque cada escenario es diferente, pero podemos proporcionar algunas opciones de alto nivel para su referencia.

### Arquitectura sin encabezado

Tenemos una sección separada dedicada a detallar lo que [acéfalo](../../architecture/headless/adobe-commerce.md) es y diferentes opciones. En resumen, separa la capa de tienda de la propia plataforma. Sigue siendo el mismo servidor, pero Adobe Commerce ya no procesa solicitudes directamente y, en su lugar, solo admite tiendas personalizadas a través de la API de GraphQL.

### Mantener Adobe Commerce actualizado

Adobe Commerce siempre tiene un mejor rendimiento cuando se ejecuta la versión más reciente. Aunque no sea posible mantener Adobe Commerce actualizado después de cada nueva versión del lanzamiento, se recomienda [actualización](../../../upgrade/overview.md) cuando Adobe Commerce introduce optimizaciones de rendimiento significativas.

Por ejemplo, en 2020, Adobe lanzó una optimización para la capa de Redis, que corrigió muchas ineficiencias, problemas de conexión y transferencias de datos innecesarias entre Redis y Adobe Commerce. El rendimiento general entre 2.3 y 2.4 es de noche y de día y hemos visto mejoras significativas en el carro de compras, el cierre de compra y los usuarios simultáneos, solo por la optimización de Redis.

### Optimizar modelo de datos

Muchos de los problemas se originan en los datos, incluidos los modelos de datos incorrectos, los datos que no están estructurados correctamente y los datos a los que les falta un índice.

Se ve bien si está probando algunas conexiones, pero se ve en producción cuando el tráfico real llega y aquí es donde entra en juego la lentitud. Es muy importante que los integradores de sistemas sepan cómo diseñar un modelo de datos (especialmente para los atributos de producto), evitar añadir atributos innecesarios y mantener atributos obligatorios que afecten a la lógica empresarial (como precios, disponibilidad de existencias y búsqueda).

Para aquellos atributos que no afectan a la lógica empresarial pero que aún necesitan estar presentes en la tienda, combínelos en unos pocos atributos (por ejemplo, formato JSON).

Para optimizar el rendimiento de la plataforma, si no se requiere lógica empresarial en la tienda a partir de datos o atributos tomados de un PIM o un ERP, no es necesario agregar ese atributo a Adobe Commerce.

### Diseño para escalabilidad

Esto es importante para las empresas que ejecutan campañas y que afrontan horas punta con frecuencia. Para que la arquitectura y el diseño de aplicaciones sean fáciles de escalar, esto puede aumentar los recursos durante las horas de mayor actividad y reducirlos después.
