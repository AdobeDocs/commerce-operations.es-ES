---
title: Optimización del rendimiento AEM
description: Optimice la configuración predeterminada de Adobe Experience Manager para admitir altas cargas en Adobe Commerce.
source-git-commit: 63f153365398c3ae7dc7e6214b67705c8a4c7686
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# AEM optimización del rendimiento

El AEM Dispatcher es un proxy inverso que ayuda a proporcionar un entorno rápido y dinámico. Funciona como parte de un servidor HTML estático, como Apache HTTP Server, con el objetivo de almacenar (o &quot;almacenar en caché&quot;) todo el contenido del sitio que sea posible, en forma de recursos estáticos. Este método pretende minimizar en la medida de lo posible la necesidad de acceder a la funcionalidad de renderización de páginas AEM y al servicio de Adobe Commerce GraphQL. El resultado de servir gran parte de las páginas como HTML estático, CSS y JS ofrece beneficios de rendimiento a los usuarios y reduce los requisitos de infraestructura en el entorno. Cualquier página o consulta que probablemente se repita de forma idéntica de un usuario a otro debe considerarse para el almacenamiento en caché.

Las secciones siguientes muestran a un alto nivel el área de enfoque técnico recomendada que se debe revisar para permitir el almacenamiento en caché efectivo de los AEM en un entorno de CIF/comercio de Adobe.

## Almacenamiento en caché basado en TTL en AEM distribuidores

El almacenamiento en caché de la mayor parte posible del sitio en los distribuidores es una práctica recomendada para cualquier proyecto AEM. El uso de la invalidación de caché basada en el tiempo almacenará en caché las páginas del CIF procesadas por el servidor durante una cantidad de tiempo limitada establecida. Una vez que la hora establecida haya caducado, la siguiente solicitud reconstruirá la página del publicador de AEM y de Adobe Commerce GraphQL y la almacenará de nuevo en la caché de Dispatcher hasta la siguiente invalidación.

La función de almacenamiento en caché TTL se puede configurar en AEM utilizando el componente &quot;TTL Dispatcher&quot; dentro del paquete ACS AEM Commons y configurando /enableTTL &quot;1&quot; en el archivo de configuración dispatcher.any.

Si está habilitado, Dispatcher evaluará los encabezados de respuesta del servidor y, si contienen una fecha de max-age o Expires de Cache-Control, se creará un archivo auxiliar vacío junto al archivo de caché, con una hora de modificación igual a la fecha de caducidad. Cuando se solicita el archivo en caché más allá del tiempo de modificación, se vuelve a solicitar automáticamente desde el servidor. Esto proporciona un mecanismo de almacenamiento en caché eficaz que no requiere ninguna intervención manual ni mantenimiento, una vez que las partes interesadas del negocio han reconocido y aceptado el retraso en la actualización del producto (TTL).

## Almacenamiento en caché del explorador

El método TTL de Dispatcher anterior reducirá en gran medida las solicitudes y se cargará en el editor. Sin embargo, hay algunos recursos que es muy poco probable que cambien y, por lo tanto, incluso las solicitudes al despachante se pueden reducir almacenando en caché los archivos relevantes localmente en el explorador de un usuario. Por ejemplo, el logotipo del sitio, que se muestra en todas las páginas del sitio en la plantilla del sitio, no tendría que solicitarse cada vez a Dispatcher. Esto se puede almacenar en la caché del explorador del usuario. La reducción en los requisitos de ancho de banda para cada carga de página tendría un gran impacto en la capacidad de respuesta del sitio y los tiempos de carga de las páginas.

El almacenamiento en caché a nivel de navegador se realiza normalmente a través de &quot;Cache-Control: max-age=&quot; . La configuración máxima indica al explorador cuántos segundos debe almacenar el archivo en caché antes de intentar &quot;revalidar&quot; o solicitarlo de nuevo desde el sitio. Este concepto de caché max-age se conoce comúnmente como &quot;Cache Expiration&quot; o TTL (&quot;Time to Live&quot;). Entrega de experiencias comerciales a escala: con Adobe Experience Manager, Commerce Integration Framework, Adobe Commerce 7

Algunas áreas de un sitio de AEM/CIF/Adobe Commerce que se pueden configurar para que se almacenen en caché en el explorador del cliente incluyen:

- Imágenes (dentro de la plantilla de AEM misma, por ejemplo el logotipo del sitio y las imágenes de diseño de plantilla - las imágenes de producto del catálogo se llamarían desde Adobe Commerce a través de Finfinito, el almacenamiento en caché de estas imágenes se discute más adelante)
- Archivos HTML (para páginas que cambian con poca frecuencia: página de términos y condiciones, etc.)
- Archivos CSS
- Todos los archivos JavaScript del sitio, incluidos los archivos JavaScript del CIF

## Optimización del periodo de gracia y el nivel de estatus de Dispatcher

La configuración predeterminada de Dispatcher utiliza el ajuste /statfilelevel &quot;0&quot;, lo que significa que un solo archivo &quot;.stat&quot; se coloca en la raíz del directorio htdocs (directorio raíz del documento). Si se realiza un cambio en una página o archivo de AEM, el tiempo de modificación de este archivo .stat se actualiza al momento del cambio. Si la hora es más reciente que la hora de modificación del recurso, Dispatcher considerará que todos los recursos se invalidan y cualquier solicitud posterior de un recurso invalidado déclencheur una llamada a la instancia de publicación. Básicamente, con esta configuración, cada activación invalidará toda la caché.

Para cualquier sitio, especialmente los sitios de comercio con una carga pesada, esto colocaría una cantidad innecesaria de carga en el nivel de AEM Publish para toda la estructura del sitio para invalidarse con una sola actualización de página.

En su lugar, la configuración de statfilelevel puede modificarse a un valor mayor, que corresponde a la profundidad de los subdirectorios en el directorio htdocs del directorio raíz del documento, de modo que cuando se invalida un archivo ubicado en un nivel determinado, solo se actualizan los archivos en ese nivel de directorio .stat e inferior.

Por ejemplo: supongamos que tiene una plantilla de página de producto en:

```
content/ecommerce/us/en/products/product-page.html
```

Cada nivel de carpeta tendría &quot;nivel de estadísticas&quot;, como se muestra desglosado en la tabla anterior.

| content (docroot) | comercio electrónico | us | en | products | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2 | 3 | 4 | - |

En este caso, si ha dejado la propiedad statfilelevel establecida en el &quot;0&quot; predeterminado y la plantilla product-page.html se actualiza y activa activando una invalidación, todos los archivos .stat desde docroot hasta el nivel 4 se tocarán y los archivos se invalidarán, lo que provocará una solicitud adicional de las instancias de publicación de AEM para todas las páginas del sitio (incluidos otros sitios web, países e idiomas) a partir de ese cambio único.

Sin embargo, si la propiedad statfilelevel se establece en el nivel 4 y se realiza un cambio en product-page.html , solo se tocará el archivo .stat en el directorio de productos para ese sitio web, país o idioma específico.

Tenga en cuenta que el nivel del archivo .stat no debe establecerse en un nivel demasiado alto, ya que superar 20 puede tener un impacto en el rendimiento. La ejecución de una activación de archivos por lotes mientras se ejecuta una prueba de rendimiento debería darle el nivel correcto al que debe ajustar el nivel de estadísticas.

Otra configuración de Dispatcher para optimizar al configurar statfilelevel es la configuración de período de gracia. Esto define el número de segundos que un recurso obsoleto e invalidado automáticamente puede seguir sirviéndose desde la caché después de la última activación. Los recursos invalidados automáticamente se invalidan con cualquier activación (cuando su ruta coincide con la sección dispatcher/invalidate y con el nivel especificado en la propiedad statfileslevel). Se puede utilizar la configuración de período de gracia en 2 segundos para evitar un escenario en el que se envíen continuamente varias solicitudes al editor, incluso mientras el editor esté aún en proceso de crear la nueva página.

>[!NOTE]
>
> Encontrará más información detallada sobre este tema en el repositorio [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) de GitHub.

## CIF - Almacenamiento en caché de GraphQL mediante componentes

Los componentes individuales dentro de AEM se pueden configurar para que se almacenen en caché, lo que significa que la solicitud de GraphQL al Adobe
El comercio se llama una vez y, a continuación, las solicitudes posteriores, hasta el límite de tiempo configurado, se recuperan de la caché de AEM y no colocarían más carga en Adobe Commerce. Algunos ejemplos serían la navegación del sitio basada en un árbol de categorías mostrado en cada página y las opciones dentro de una funcionalidad de búsqueda faceteada. Estas son solo dos áreas que requieren consultas intensivas en recursos sobre comercio de Adobe para compilar, pero es poco probable que cambien regularmente y, por lo tanto, serían buenas opciones para el almacenamiento en caché. De este modo, por ejemplo, incluso cuando el editor está reconstruyendo un PDP o PLP, la solicitud de GraphQL para la compilación de navegación que requiere muchos recursos no llegaría a Adobe Commerce y se podría recuperar de la caché de GraphQL en AEM CIF.

Un ejemplo a continuación es que el componente de navegación se almacene en caché porque envía la misma consulta de GraphQL a todas las páginas del sitio. La siguiente solicitud almacena en caché las últimas 100 entradas durante 10 minutos para la estructura de navegación:

```
venia/components/structure/navigation:true:100:600
```

El ejemplo siguiente almacena en caché las últimas 100 opciones de búsqueda faceteada en una página de búsqueda durante 1 hora:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

La solicitud, incluidos todos los encabezados y variables http personalizados, debe coincidir exactamente para que la caché se &quot;visite&quot; y para evitar una llamada repetida a Adobe Commerce. Debe tenerse en cuenta que una vez configurada, no hay una forma fácil de invalidar manualmente esta caché. Esto podría significar que, si se añade una nueva categoría en Adobe Commerce, no comenzaría a aparecer en la navegación hasta que la hora de caducidad establecida en la caché anterior haya caducado y se actualice la solicitud de GraphQL. Lo mismo para facetas de búsqueda. Sin embargo, dados los beneficios de rendimiento que se pueden lograr con este almacenamiento en caché, normalmente se trata de un compromiso aceptable.

Las opciones de almacenamiento en caché anteriores se pueden configurar usando la consola de configuración OSGi de AEM en el cliente de GraphQL
Fábrica de configuración&quot;. Cada entrada de configuración de caché se puede especificar con el siguiente formato:

```
• NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## Almacenamiento en caché híbrido: solicitudes de GraphQL del lado del cliente dentro de páginas de Dispatcher en caché

También es posible un enfoque híbrido para el almacenamiento en caché de páginas: es posible que una página de CIF contenga componentes que siempre soliciten la información más reciente de Adobe Commerce directamente desde el navegador del cliente. Esto puede resultar útil para áreas específicas de la página dentro de una plantilla que son importantes para mantenerse actualizado con información en tiempo real: Los precios de los productos dentro de un PDP, por ejemplo. Cuando los precios cambian con frecuencia debido a la coincidencia dinámica de precios, esa información se puede configurar para que no se almacene en caché en Dispatcher, sino que los precios se pueden recuperar del lado del cliente en el explorador del cliente desde Adobe Commerce directamente a través de las API de GraphQL con AEM componentes web del CIF.

Esto se puede configurar a través de la configuración de componentes de AEM : para obtener información sobre precios en páginas de listas de productos, esto se puede configurar en la plantilla de lista de productos, seleccionar el componente de lista de productos en la configuración de página y marcar la opción &quot;precios de carga&quot;. El mismo enfoque funcionaría para los niveles de existencias.

Los métodos anteriores solo deben utilizarse en caso de que sea necesario disponer de información actualizada y en tiempo real. En el ejemplo anterior con los precios, se podría acordar con las partes interesadas del negocio actualizar los precios solo diariamente en tiempos de poco tráfico y realizar entonces la operación de vaciado de la caché. Esto eliminaría la necesidad de las solicitudes de información de precios en tiempo real y la carga adicional subsiguiente en Adobe Commerce al crear cada página mostrando información de precios.

## Solicitudes de GraphQL no almacenables en caché

Los componentes de datos dinámicos específicos dentro de las páginas no deben almacenarse en caché y siempre requerirán una llamada de GraphQL a Adobe Commerce, como para el carro de compras y las llamadas a través de las páginas de cierre de compra. Esta información es específica para un usuario y cambia constantemente debido a la actividad del cliente en el sitio, por ejemplo, añadiendo productos al carro de compras.

Los resultados de la consulta de GraphQL no deben almacenarse en caché para los clientes que iniciaron sesión si el diseño del sitio ofrecía respuestas diferentes en función de la función del usuario. Por ejemplo, puede crear varios grupos de clientes y configurar diferentes precios de producto o distintas categorías de visibilidad de producto para cada grupo. Los resultados de almacenamiento en caché como estos pueden hacer que los clientes vean los precios de otro grupo de clientes o que se muestren categorías incorrectas.

## Ignorar parámetros de seguimiento en AEM caché de Dispatcher

Los sitios de comercio electrónico pueden dirigir el tráfico a su sitio mediante anuncios de búsqueda de PPC o campañas de medios sociales.

El uso de estos medios significará que se añade un ID de seguimiento al vínculo saliente desde esa plataforma. Por ejemplo, Facebook agregará un ID de clic de Facebook (fbclid) a la URL, Google Adverts agregará un ID de clic de Google (gclid), lo que hará que los vínculos entrantes a su front-end de AEM aparezcan como se muestra a continuación, como ejemplo:

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

El gclid y el fbclid cambiarán con cada usuario que haga clic en el anuncio; está pensado para fines de seguimiento, pero con su configuración predeterminada, AEM verían cada solicitud como una página única, lo que evitaría el despachante y generaría una carga adicional innecesaria en el editor y en el Adobe Commerce.

Durante un evento de sobrecarga, esto puede incluso provocar que los editores de AEM se sobrecarguen y no respondan. Cuando se configura que un parámetro se ignore para una página, la página se almacena en caché la primera vez que se solicita la página. Las solicitudes posteriores para la página se proporcionan en la página en caché, independientemente del valor del parámetro en la solicitud.

>[!NOTE]
>
>Encontrará más información sobre la importancia de configurar `ignoreUrlParams` en el repositorio [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) de GitHub.

Por lo tanto, debe configurarse para ignorar todos los parámetros de forma predeterminada en &quot;ignoreUrlParams&quot;, excepto cuando se utiliza un parámetro de GET que cambie la estructura HTML de una página. Un ejemplo de esto sería con una página de búsqueda donde el término de búsqueda está en la dirección URL como parámetro de GET: en este caso, debería configurar manualmente ignoreUrlParams para ignorar parámetros como gclid, fbclid y cualquier otro parámetro de seguimiento que estén utilizando los canales publicitarios, dejando sin afectar los parámetros de GET necesarios para las operaciones normales del sitio.

## Límites de los trabajadores de MPM en los despachantes

La configuración de trabajadores de MPM es una configuración avanzada del servidor HTTP de Apache que requeriría pruebas exhaustivas para optimizar según la CPU y la RAM disponibles de Dispatcher. Sin embargo, en el ámbito de este documento técnico sugeriríamos que ServerLimit y MaxRequestWorkers, deberían aumentarse a un nivel que admita la CPU y la RAM disponibles del servidor, y luego los MinSpareThreads y MaxSpareThreads deberían aumentarse a un nivel que coincida con MaxRequestWorkers.

Esta configuración dejaría a Apache HTTP en un &quot;ajuste de preparación completa&quot; que es una configuración de alto rendimiento para servidores con una RAM significativa y varios núcleos de CPU. Esta configuración genera los mejores tiempos de respuesta posibles de Apache HTTP al mantener las conexiones abiertas persistentes listas para servir solicitudes y eliminaría cualquier retraso en la generación de nuevos procesos en respuesta a repentinos aumentos del tráfico, como durante las ventas flash.
