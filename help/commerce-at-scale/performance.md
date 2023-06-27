---
title: AEM Optimización del rendimiento de
description: Optimice la configuración predeterminada de Adobe Experience Manager para admitir cargas altas en Adobe Commerce.
exl-id: 923a709f-9048-4e67-a5b0-ece831d2eb91
feature: Integration, Cache
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '2248'
ht-degree: 0%

---

# AEM Optimización del rendimiento de la

AEM El Dispatcher es un proxy inverso, que ayuda a ofrecer un entorno que es rápido y dinámico. Funciona como parte de un servidor HTML estático, como Apache HTTP Server, con el objetivo de almacenar (o &quot;almacenar en caché&quot;) la mayor parte posible del contenido del sitio, en forma de recursos estáticos. AEM Este método pretende minimizar en la medida de lo posible la necesidad de acceder a la funcionalidad de renderización de páginas de la y al servicio GraphQL de Adobe Commerce. El resultado de servir gran parte de las páginas como HTML estático, CSS y JS ofrece ventajas de rendimiento a los usuarios y reduce los requisitos de infraestructura en el entorno. Cualquier página o consulta que probablemente se repita de forma idéntica de usuario a usuario debe considerarse para el almacenamiento en caché.

AEM Las secciones siguientes muestran a alto nivel el área de enfoque técnico recomendada que se debe revisar para permitir un almacenamiento en caché efectivo de los recursos en un entorno de CIF/Adobe Commerce.

## AEM Almacenamiento en caché basado en TTL en Dispatcher de

AEM El almacenamiento en caché de la mayor parte posible del sitio en las instancias de Dispatcher es una práctica recomendada para cualquier proyecto de. El uso de la invalidación de caché basada en el tiempo almacenará en caché las páginas del CIF procesadas del lado del servidor, durante un tiempo limitado establecido. AEM Una vez transcurrido el tiempo establecido, la siguiente solicitud reconstruirá la página desde el editor de y Adobe Commerce GraphQL y la almacenará de nuevo en la caché de Dispatcher hasta la siguiente invalidación.

AEM AEM La función de almacenamiento en caché de TTL se puede configurar de forma predeterminada mediante el uso del componente &quot;TTL de Dispatcher&quot; en el paquete ACS Commons y la configuración /enableTTL &quot;1&quot; en el archivo de configuración dispatcher.any.

Si se habilita, Dispatcher evaluará los encabezados de respuesta del backend y, si contienen una fecha Cache-Control max-age o Expires, se creará un archivo auxiliar vacío junto al archivo de caché, con una hora de modificación igual a la fecha de caducidad. Cuando se solicita el archivo en caché pasado el tiempo de modificación, se vuelve a solicitar automáticamente desde el backend. Esto proporciona un mecanismo de almacenamiento en caché efectivo que no requiere intervención manual ni mantenimiento, una vez que las partes interesadas empresariales han reconocido y aceptado el retraso de la actualización del producto (TTL).

## Almacenamiento en caché del explorador

El método TTL del distribuidor anterior reducirá en gran medida las solicitudes y la carga en el editor, pero hay algunos recursos que es muy improbable que cambien y, por lo tanto, incluso las solicitudes al distribuidor se pueden reducir almacenando en caché los archivos relevantes localmente en el explorador del usuario. Por ejemplo, el logotipo del sitio, que se muestra en todas las páginas del sitio en la plantilla del sitio, no tendría que solicitarse cada vez al distribuidor. En su lugar, esto se puede almacenar en la caché del explorador del usuario. La reducción en los requisitos de ancho de banda para cada carga de página tendría un gran impacto en la capacidad de respuesta del sitio y los tiempos de carga de la página.

El almacenamiento en caché a nivel de explorador se suele realizar mediante el encabezado de respuesta &quot;Cache-Control: max-age=&quot;. La configuración maxage indica al explorador durante cuántos segundos debe almacenar el archivo en caché antes de intentar &quot;revalidarlo&quot; o solicitarlo de nuevo desde el sitio. Este concepto de max-age de caché se conoce comúnmente como &quot;Caducidad de caché&quot; o TTL (&quot;Tiempo de vida&quot;). Entrega de experiencias de comercio a escala: con Adobe Experience Manager, Commerce Integration Framework, Adobe Commerce 7

AEM Algunas áreas de un sitio del CIF/Adobe Commerce, que se puede configurar para que se almacene en caché en el explorador del cliente, son las siguientes:

- AEM Las imágenes (dentro de la plantilla de la plantilla en sí, por ejemplo, las imágenes de diseño de plantilla y logotipo del sitio; las imágenes de producto del catálogo se solicitarían desde Adobe Commerce a través de Fastly y se analiza más adelante el almacenamiento en caché de estas imágenes)
- Archivos de HTML (para páginas poco cambiadas: página de términos y condiciones, etc.)
- Archivos CSS
- Todos los archivos JavaScript del sitio, incluidos los archivos JavaScript del CIF

## Optimización del nivel de estado y período de gracia de Dispatcher

La configuración predeterminada de Dispatcher utiliza la configuración /statfilelevel &quot;0&quot;, lo que significa que se coloca un solo archivo &quot;.stat&quot; en la raíz del directorio htdocs (directorio raíz del documento). AEM Si se realiza un cambio en una página o archivo en, el tiempo de modificación de este archivo .stat se actualiza al tiempo del cambio. Si la hora es posterior a la hora de modificación del recurso, Dispatcher considerará que todos los recursos están invalidados y cualquier solicitud posterior de un recurso invalidado almacenará en déclencheur una llamada a la instancia de publicación. Básicamente, con esta configuración, cada activación invalidará toda la caché.

Para cualquier sitio, especialmente los sitios de comercio con una carga pesada, esto colocaría una cantidad innecesaria de carga en el nivel de publicación de AEM para que toda la estructura del sitio se invalide con una sola actualización de página.

En su lugar, la configuración statfilelevel se puede modificar a un valor mayor, correspondiente a la profundidad de los subdirectorios del directorio htdocs desde el directorio raíz del documento, de modo que cuando se invalide un archivo ubicado en un nivel determinado, solo se actualicen los archivos de ese nivel de directorio .stat y posteriores.

Por ejemplo: supongamos que tiene una plantilla de página de producto en:

```
content/ecommerce/us/en/products/product-page.html
```

Cada nivel de carpeta tendría &quot;nivel de estado&quot;, como se muestra desglosado en la tabla anterior.

| content (docroot) | comercio electrónico | us | en | products | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2 | 3 | 4 | - |

AEM En este caso, si ha dejado la propiedad statfilelevel establecida en el valor predeterminado &quot;0&quot;, y la plantilla product-page.html se actualiza y activa activando una invalidación, todos los archivos .stat desde docroot hasta el nivel 4 se tocarán y los archivos se invalidarán, lo que provocará una solicitud adicional de las instancias de publicación para todas las páginas del sitio (incluidos otros sitios web, países e idiomas) a partir de ese cambio único.

Sin embargo, si la propiedad statfilelevel está establecida en el nivel 4 y se realiza un cambio en el archivo product-page.html, solo se tocará el archivo .stat en el directorio de productos de ese sitio web, país o idioma específico.

Tenga en cuenta que el nivel del archivo .stat no debe configurarse en un nivel demasiado alto; superar los 20 puede afectar al rendimiento. La ejecución de una activación masiva de archivos mientras se ejecuta una prueba de rendimiento debe proporcionarle el nivel correcto al que debe ajustar el nivel de estado.

Otra configuración de Dispatcher para optimizar al configurar statfilelevel es gracePeriod. Define la cantidad de segundos que un recurso obsoleto e invalidado automáticamente se puede seguir usando desde la caché después de que se produjo la última activación. Los recursos invalidados automáticamente se invalidan con cualquier activación (cuando su ruta coincida con la sección Dispatcher /invalidate y con el nivel especificado en la propiedad statfileslevel). Si establece gracePeriod en 2 segundos, se puede evitar un escenario en el que se envíen varias solicitudes al editor de forma continua, incluso mientras el editor esté todavía en el proceso de crear la nueva página.

>[!NOTE]
>
> Encontrará más información detallada sobre este tema en la [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) Repositorio de GitHub.

## CIF: almacenamiento en caché de GraphQL a través de componentes

AEM Los componentes individuales dentro de los componentes se pueden configurar para que se almacenen en caché, lo que significa que la solicitud de GraphQL a Adobe Commerce AEM se llama una vez y, a continuación, las solicitudes subsiguientes, hasta el límite de tiempo configurado, se recuperan de la caché de la y no se volverán a cargar en Adobe Commerce. Algunos ejemplos son la navegación del sitio basada en un árbol de categorías que se muestra en todas las páginas y las opciones dentro de una funcionalidad de búsqueda con facetas: estas son solo dos áreas que requieren consultas que consuman muchos recursos en Adobe Commerce para crearlas; sin embargo, es poco probable que cambien con regularidad y, por lo tanto, serían buenas opciones para el almacenamiento en caché. De este modo, por ejemplo, incluso cuando el editor está reconstruyendo un PDP o PLP, la solicitud de GraphQL que consume muchos recursos para la compilación de navegación no afectaría a Adobe Commerce y se podría recuperar de la caché de GraphQL AEM en el CIF en el que se encuentra el.

Un ejemplo siguiente es para que el componente de navegación se almacene en caché porque envía la misma consulta de GraphQL a todas las páginas del sitio. La solicitud siguiente almacena en caché las 100 entradas pasadas durante 10 minutos para la estructura de navegación:

```
venia/components/structure/navigation:true:100:600
```

El ejemplo siguiente almacena en caché las últimas 100 opciones de búsqueda con facetas en una página de búsqueda durante 1 hora:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

La solicitud, incluidos todos los encabezados http y variables personalizadas, debe coincidir exactamente para que la caché sea &quot;hit&quot; y para evitar que se repita la llamada a Adobe Commerce. Debe tenerse en cuenta que una vez configurada, no hay una manera fácil de invalidar manualmente esta caché. Esto podría significar que, si se agrega una nueva categoría en Adobe Commerce, no empezaría a aparecer en la navegación hasta que la hora de caducidad establecida en la caché anterior haya caducado y se actualice la solicitud de GraphQL. Lo mismo para las facetas de búsqueda. Sin embargo, dadas las ventajas de rendimiento que se pueden conseguir con este almacenamiento en caché, este suele ser un compromiso aceptable.

Las opciones de almacenamiento en caché anteriores se pueden configurar mediante la consola de configuración OSGi de la aplicación en &quot;GraphQL Client Configuration Factory&quot; (Fábrica de configuración del cliente de AEM). Cada entrada de configuración de caché se puede especificar con el siguiente formato:

```
* NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## Almacenamiento en caché híbrido: solicitudes de GraphQL del lado del cliente dentro de páginas de Dispatcher en caché

También es posible un enfoque híbrido para el almacenamiento en caché de páginas: es posible que una página de CIF contenga componentes que siempre soliciten la información más reciente de Adobe Commerce directamente desde el explorador del cliente. Esto puede resultar útil para áreas específicas de la página dentro de una plantilla que son importantes para mantenerse actualizadas con información en tiempo real: precios de productos dentro de una PDP, por ejemplo. Cuando los precios cambian con frecuencia debido a la coincidencia dinámica de precios, esa información se puede configurar para que no se almacene en caché en el despachante, sino que los precios se pueden recuperar del lado del cliente en el explorador del cliente desde Adobe Commerce directamente a través de las API de GraphQL AEM con los componentes web del CIF de la.

AEM Esto se puede configurar a través de la configuración de componentes del producto: para obtener información sobre el precio en las páginas de lista de productos, esto se puede configurar en la plantilla de lista de productos, seleccionando el componente de lista de productos en la configuración de página y marcando la opción &quot;cargar precios&quot;. El mismo enfoque funcionaría para los niveles de existencias.

Los métodos anteriores solo deben utilizarse en caso de que se requiera información actualizada constantemente en tiempo real. En el ejemplo anterior con precios, se podría acordar con las partes interesadas empresariales actualizar los precios solo diariamente en tiempos de bajo tráfico y realizar la operación de vaciado de caché en ese momento. Esto eliminaría la necesidad de las solicitudes de información de precios en tiempo real y la carga adicional posterior en Adobe Commerce al crear cada página que muestra información de precios.

## Solicitudes de GraphQL no almacenables en caché

Los componentes de datos dinámicos específicos de las páginas no deben almacenarse en caché y siempre requerirán una llamada de GraphQL a Adobe Commerce, como para el carro de compras y las llamadas a través de las páginas de cierre de compra. Esta información es específica de un usuario y cambia constantemente debido a la actividad del cliente en el sitio, por ejemplo, al añadir productos al carro de compras.

Los resultados de la consulta de GraphQL no deben almacenarse en caché para los clientes que iniciaron sesión si el diseño del sitio proporcionara respuestas diferentes según la función del usuario. Por ejemplo, puede crear varios grupos de clientes y configurar diferentes precios de productos o visibilidad de categorías de productos para cada grupo. Almacenar en caché resultados como estos puede hacer que los clientes vean los precios de otro grupo de clientes o que se muestren categorías incorrectas.

## AEM Ignorar los parámetros de seguimiento en la caché de Dispatcher de

Los sitios de comercio electrónico pueden dirigir el tráfico a su sitio mediante anuncios de búsqueda de PPC o campañas de medios sociales.

El uso de estos medios significará que se agrega un ID de seguimiento al vínculo de salida desde esa plataforma. Por ejemplo, Facebook agregará un ID de clic de Facebook (fbclid) a la dirección URL, Google Adverts agregará un ID de clic de Google AEM (gclid), lo que hará que los vínculos entrantes al front-end de la aparezcan como los siguientes, por ejemplo:

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

AEM gclid y fbclid cambiarán con cada usuario que haga clic en el anuncio. Se ha diseñado con fines de seguimiento, pero con su configuración predeterminada, los usuarios verán cada solicitud como una página única, lo que evitará al despachante y generará una carga adicional innecesaria en el editor y en Adobe Commerce.

AEM Durante un evento de sobrecarga, esto incluso puede provocar que los editores de la se sobrecarguen y no respondan. Cuando se establece que un parámetro se ignore para una página, la página se almacena en caché la primera vez que se solicita. Las solicitudes posteriores para la página se proporcionan en la página en caché, independientemente del valor del parámetro en la solicitud.

>[!NOTE]
>
>Más información sobre la importancia de la configuración `ignoreUrlParams` está disponible en la [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) Repositorio de GitHub.

Por lo tanto, debe configurarse para que ignore todos los parámetros de forma predeterminada en &quot;ignoreUrlParams&quot;, excepto cuando se utilice un parámetro de GET que cambie la estructura del HTML de una página. Un ejemplo de esto sería con una página de búsqueda donde el término de búsqueda está en la URL como parámetro de GET GET - en este caso debe configurar manualmente ignoreUrlParams para ignorar parámetros como gclid, fbclid y cualquier otro parámetro de seguimiento que estén utilizando sus canales publicitarios, dejando los parámetros necesarios para las operaciones normales del sitio sin verse afectados.

## Límites de trabajadores de MPM en Dispatcher

La configuración de trabajadores de MPM es una configuración avanzada de servidor HTTP Apache que requeriría pruebas exhaustivas para optimizar en función de la CPU y la RAM disponibles de Dispatcher. Sin embargo, en el ámbito de este documento técnico sugerimos que ServerLimit y MaxRequestWorkers, se aumenten a un nivel que admitan la CPU y la RAM disponibles del servidor y, a continuación, se aumenten los MinSpareThreads y MaxSpareThreads a un nivel que coincida con MaxRequestWorkers.

Esta configuración dejaría a Apache HTTP en una &quot;configuración de preparación completa&quot; que es una configuración de alto rendimiento para servidores con una RAM significativa y varios núcleos de CPU. Esta configuración producirá los mejores tiempos de respuesta posibles de Apache HTTP al mantener conexiones abiertas persistentes listas para servir solicitudes y eliminaría cualquier retraso en la generación de nuevos procesos en respuesta a aumentos repentinos del tráfico, como durante las ventas flash.
