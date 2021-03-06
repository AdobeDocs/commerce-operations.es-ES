---
title: Consejos de pruebas de rendimiento
description: Obtenga información sobre cómo configurar los KPI para iniciar la solución de Adobe Commerce y Adobe Experience Manager.
exl-id: 4b0d9c4f-e611-452d-a80f-27f82705935d
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---

# Sugerencias de pruebas de rendimiento

Para evaluar la eficacia de todos los cambios anteriores, se deben ejecutar pruebas de rendimiento exhaustivas antes del lanzamiento y antes de cualquier implementación importante futura en los entornos de producción. Al planificar las pruebas de carga, es importante simular el tráfico de consumidores en la vida real en la medida de lo posible.

Las áreas con mayor consumo de recursos del sitio AEM/CIF/Adobe Commerce son aquellas que no se pueden almacenar en caché, como el proceso de cierre de compra y la búsqueda en el sitio. La exploración de páginas estática y, por lo tanto, almacenable en caché, como las páginas de detalles de producción (PDP) y las páginas de listas de productos (PLP) constituyen la mayoría del tráfico hacia un sitio de comercio electrónico en general, por lo que las secuencias de comandos y los escenarios de la prueba deben reflejarlo para medir los límites de la plataforma.

Tener un solo script ejecutándose para la prueba de carga que navega por el sitio sin tiempo de espera entre pasos y también completa siempre el proceso de cierre de compra cada vez no daría una indicación fiable de los límites de la plataforma, ya que no es lo que sería un escenario en la vida real.

La definición de los KPI debe ser el primer paso en el plan de prueba de rendimiento: defina las métricas que puede probar durante la prueba inicial, pero luego mida de nuevo en el futuro y de forma recurrente después de que el sitio esté activo. Esto le permite realizar un seguimiento del rendimiento del sitio a lo largo del tiempo, antes y después del inicio. Los KPI de ejemplo que se deben definir podrían ser:

- Tiempo de respuesta promedio: tiempo hasta el primer byte o el último byte
- Latencia
- Bytes/s (producción)
- Tasa de error
- Pedidos por hora
- Vistas de página por hora
- Usuarios únicos por hora (compradores simultáneos)

## Directrices de Jmeter

Al desarrollar las pruebas de carga de AEM/CIF/Adobe Commerce, se deben tener en cuenta las siguientes directrices de alto nivel de Jmetro:

- Divida el script en escenarios configurables, que deberían cubrir, por ejemplo:
   - Abrir la página principal
   - Abrir página de categoría (PLP)
   - Ver productos simples (PDP): 2 bucles dentro de cada iteración
   - Ver productos configurables: 2 bucles dentro de cada iteración
      - Por ejemplo, establezca los pasos anteriores en el 60 % del tráfico
   - Búsqueda de productos
      - Por ejemplo, configure la búsqueda en el catálogo en 37% del tráfico
   - Carro de compras y cierre de compra
      - Por ejemplo, un usuario que complete la parte del carro de compras y cierre de compra del script debería establecer de forma predeterminada una tasa de conversión del sitio de comercio electrónico estándar del sector de alrededor del 3%
      - Como el flujo de cierre de compra no se almacena en caché y normalmente es una operación que consume muchos recursos, configurar una cifra muy alta para la cantidad de personas que completan pedidos en comparación con la cantidad de exploradores del sitio daría un resultado poco fiable sobre el volumen de tráfico que su sitio podría gestionar.
- Limpie todas las cachés antes de cada ejecución de prueba:
   - La caché de Dispatcher AEM debe limpiarse completamente
   - La caché interna y la de Adobe Commerce deben limpiarse y vaciarse completamente: esto se puede hacer a través del control de caché en la administración de Adobe Commerce.
- Incluya un periodo de rampa en la prueba de Jmetro: No tener establecido un periodo de rampa significa que no hay una aceleración gradual del tráfico y que no hay posibilidad de que el sitio almacene en caché ninguna de las páginas y componentes más visitados de la página. En la vida real, sería inusual que todo el tráfico máximo llegara a un sitio completamente sin caché exactamente al mismo tiempo, por lo que debería incluirse un periodo de rampa en los scripts de prueba de Jmetro para permitir que la caché se acumulara tal y como sucedería en un sitio de comercio electrónico real.
- Se debería utilizar un &quot;tiempo de espera&quot; entre cada paso dentro de una iteración (en realidad, un usuario no saltaría inmediatamente a la siguiente página del sitio durante su recorrido), habría un tiempo de espera mientras que el usuario leía la página y decidía su siguiente acción.
- Si se establecen los grupos de subprocesos para que se reproduzcan infinitamente, pero durante un tiempo determinado de x (por ejemplo, 60 minutos), se obtendrá una prueba repetible, con tiempos de respuesta medios comparables a los de las ejecuciones de pruebas anteriores. Esto significa que después del periodo de ampliación establecido, habrá el número de usuarios virtuales que se ejecutarán simultáneamente y esto continuará durante el tiempo de bucle establecido.
- La mediana de tiempo debe utilizarse para mejorar/disminuir el tiempo de respuesta promedio, no el tiempo promedio. Si hay varios resultados puntuales que tardan mucho más que los otros resultados, esto distorsionaría este resultado promedio, pero lo que nos interesa es el tiempo de respuesta del usuario final para la mayoría de los usuarios, que es más adecuado para la medición media.
- Los recursos incrustados no se recopilan de forma predeterminada en jmetro (por ejemplo, JS, CSS y otros recursos descargados cuando un usuario visita la página). Esto se puede habilitar, pero solo para el dominio que está probando: las llamadas a recursos externos se deben seguir excluyendo (por ejemplo, no queremos incluir tiempos de respuesta de servicios alojados externamente, por ejemplo. código de google analytics, ya que no tenemos control sobre ellos).
- El Administrador de caché HTTP debe estar habilitado, lo que permite a Jmetro almacenar en caché los elementos de página durante un recorrido como lo haría el recorrido de un usuario real durante su navegación por el sitio web en su propio navegador. Durante su recorrido a través del sitio, el navegador del usuario descargaba el recurso incrustado relacionado solo una vez y luego el navegador del usuario los almacenaba en caché. Además, si el mismo usuario regresa al sitio algún tiempo después de su visita original, podría seguir siendo la caché en la que se almacenan esos recursos.
- Los oyentes deben mantenerse dentro de las ejecuciones de prueba de carga real (por ejemplo, &quot;Ver árbol de resultados&quot; y &quot;Agregar informe&quot;). Incluirlo en la ejecución de pruebas de carga real que no son de GUI puede afectar a los resultados de rendimiento que informa Jmetro, ya que los recursos se utilizan durante la ejecución de pruebas real para generar los informes. Estos oyentes se eliminaron de la secuencia de comandos de prueba para reemplazarlos con un archivo de resultados JTL, que luego se puede procesar usando la funcionalidad del panel de informes de Jmetro.
- Un tiempo de respuesta objetivo para evaluado, de modo que la &quot;puntuación Apdex&quot; del informe del panel pueda utilizarse como una forma rápida de medir el efecto de los cambios en el rendimiento entre ejecuciones de prueba. La puntuación de Apdex se basa en una cierta cantidad de personas que pueden acceder al sitio en un tiempo tolerable . Si el tiempo de respuesta supera una cierta cantidad &quot;frustrante&quot;, se reduce la puntuación. Los tiempos se pueden configurar utilizando los parámetros &quot;apdex_happy_ threshold&quot; y &quot;apdex_tolated_threshold&quot;.
- Establezca una métrica objetivo &quot;Pedidos por hora&quot; para presentarla a los usuarios empresariales, no a un recuento de usuarios virtuales. Los &quot;usuarios virtuales&quot; pueden ser un tema complejo para comprender qué mide la prueba en la vida real. Al calcular la tasa de conversión del sitio, los pedidos por hora, el tiempo promedio que un usuario emplea en el sitio y pensar en el tiempo entre cada carga de página, se pueden utilizar cálculos estándar del sector para presentar diferentes escenarios de prueba de carga basados en los pedidos por hora que se van a lograr.
- Por último, el servidor de prueba de Jmetro debe ejecutarse en un servidor geográficamente cercano al lugar de donde proviene la mayoría del tráfico del usuario y en el que se aloja la infraestructura de la nube. Es de esperar que estos sean los mismos.
