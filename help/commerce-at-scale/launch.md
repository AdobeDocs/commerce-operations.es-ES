---
title: Consejos de prueba de rendimiento
description: Obtenga información sobre cómo establecer KPI para lanzar su solución de Adobe Commerce y Adobe Experience Manager.
exl-id: 4b0d9c4f-e611-452d-a80f-27f82705935d
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---

# Sugerencias de pruebas de rendimiento

Para evaluar la eficacia de todos los cambios anteriores, se deben ejecutar pruebas de rendimiento exhaustivas antes del lanzamiento y antes de cualquier implementación importante futura en los entornos de producción. Al planificar las pruebas de carga, es importante simular el tráfico de los consumidores en la vida real en la medida de lo posible.

AEM Las áreas con mayor consumo de recursos del sitio del CIF/Adobe Commerce, del sitio de la comunidad de datos son las que no se pueden almacenar en caché, como el proceso de cierre de compra y la búsqueda en el sitio. La exploración de páginas estática y, por lo tanto, almacenable en caché, como para las páginas de detalles de productos (PDP) y las páginas de listas de productos (PLP), constituyen la mayor parte del tráfico de un sitio de comercio electrónico en general, por lo que los scripts y escenarios de la prueba deben reflejar eso para medir los límites de la plataforma.

Tener una sola secuencia de comandos en ejecución para la prueba de carga que navega por el sitio sin tiempo de espera entre pasos, y también siempre completa el proceso de cierre de compra cada vez no daría una indicación fiable de los límites de la plataforma, ya que eso no es lo que sería un escenario en la vida real.

La definición de los indicadores clave de rendimiento (KPI) debe ser el primer paso del plan de prueba de rendimiento: defina las métricas que puede probar durante la prueba inicial, pero luego volver a medir en el futuro y de forma recurrente después de que el sitio esté activo. Esto le permite realizar un seguimiento del rendimiento del sitio a lo largo del tiempo, tanto antes como después del lanzamiento. Ejemplo de KPI que definir podrían ser:

- Tiempo medio de respuesta: tiempo hasta el primer o último byte
- Latencia
- Bytes/s (rendimiento)
- Tasa de error
- Pedidos por hora
- Vistas de página por hora
- Usuarios únicos por hora (compradores simultáneos)

## Directrices de Jmeter

AEM Las siguientes directrices de alto nivel de Jmeter deben tenerse en cuenta al desarrollar las pruebas de carga de su/CIF/Adobe Commerce:

- Divida el script en escenarios configurables, que deberían cubrir, por ejemplo:
   - Abrir página principal
   - Abrir página de categoría (PLP)
   - Ver productos simples (PDP): 2 bucles dentro de cada iteración
   - Ver productos configurables: 2 bucles dentro de cada iteración
      - Por ejemplo, establezca los pasos anteriores en 60 % del tráfico
   - Búsqueda de productos
      - Por ejemplo, defina la búsqueda en el catálogo en el 37 % del tráfico
   - Carro y cierre de compra
      - Por ejemplo: un usuario que completa la parte del script de carro de compras y cierre de compra debe tener de forma predeterminada una tasa de conversión del sitio de comercio electrónico estándar del sector de alrededor del 3 %
      - Dado que el flujo de cierre de compra no se almacena en caché y suele ser una operación que consume muchos recursos, establecer una cifra demasiado alta para el número de personas que completan pedidos en comparación con el número de exploradores del sitio daría un resultado poco fiable para el volumen de tráfico que podría gestionar el sitio.
- Limpie todas las cachés antes de cada ejecución de prueba:
   - AEM La caché de Dispatcher debe limpiarse por completo
   - La caché interna y de Fastly de Adobe Commerce debe vaciarse y limpiarse por completo, esto se puede hacer a través del control de caché en el administrador de Adobe Commerce.
- Incluir un período de rampa en la prueba Jmeter: No tener un período de rampa establecido significa que no hay una rampa gradual del tráfico y no hay oportunidad para que el sitio almacene en caché ninguna de las páginas y los componentes de la página más visitados. En la vida real, sería inusual que todo el tráfico pico llegara a un sitio completamente sin caché exactamente al mismo tiempo, por lo tanto, se debe incluir un período de rampa en los scripts de prueba Jmeter para permitir que la caché se acumule como ocurriría en un sitio de comercio electrónico real.
- Se debe utilizar un &quot;Tiempo de espera&quot; entre cada paso de una iteración: en realidad, un usuario no pasaría inmediatamente a la siguiente página del sitio durante su recorrido; habría un tiempo de espera mientras leía la página y decidía su siguiente acción.
- Configurar los grupos de hilos para que se reproduzcan infinitamente, pero durante un tiempo establecido de x (p. ej., 60 minutos), dará una prueba repetible, con tiempos de respuesta medios comparables con ejecuciones de pruebas anteriores. Esto significa que después del período de ampliación establecido, habrá el número de destino de usuarios virtuales ejecutándose simultáneamente y esto continuará durante el tiempo de bucle establecido.
- La mediana de tiempo debe utilizarse para proporcionar una mejora/disminución del tiempo medio de respuesta, no del promedio. Si hay varios resultados Edge que tardan mucho más que los otros resultados, esto distorsionaría este resultado promedio, pero lo que nos interesa en el tiempo de respuesta del usuario final para la mayoría de los usuarios, que es más adecuado para la mediana de la medición.
- Los recursos incrustados no se recopilan de forma predeterminada en jmeter (por ejemplo, JS, CSS y otros recursos descargados cuando un usuario real visita la página). Esto se puede habilitar, pero solo para el dominio que está probando: las llamadas de recursos externos deben excluirse (por ejemplo, no queremos incluir los tiempos de respuesta de servicios alojados externamente, por ejemplo, código de google analytics, ya que no tenemos control sobre ellos).
- El Administrador de caché HTTP debe estar habilitado, lo que permite a Jmeter almacenar en caché los elementos de página durante un recorrido, como lo haría el recorrido de un usuario real durante su navegación por el sitio web en su propio navegador. Durante su recorrido por el sitio, el explorador del usuario descargaría el recurso incrustado relacionado solo una vez y, a continuación, el explorador del usuario lo almacenaría en caché. Además, si el mismo usuario regresa al sitio algún tiempo después de su visita original, podría seguir siendo la caché en la que se almacenan esos recursos.
- Los oyentes deben mantenerse dentro de las ejecuciones de prueba de carga reales (por ejemplo, &quot;Ver árbol de resultados&quot; e &quot;Informe agregado&quot;). Incluirlo en la ejecución de pruebas de carga real no GUI puede afectar a los resultados de rendimiento que Jmeter informa, ya que los recursos se utilizan durante la ejecución de pruebas reales para generar los informes. Estos oyentes se eliminaron del script de prueba para reemplazarlos con un archivo de resultados JTL, que luego se puede procesar con la funcionalidad Report Dashboard de Jmeter.
- Un tiempo de respuesta objetivo para evaluado de modo que la &quot;puntuación Apdex&quot; del informe del panel se pueda utilizar como una forma rápida de medir el efecto de los cambios en el rendimiento entre ejecuciones de prueba. La puntuación Apdex se basa en una cierta cantidad de personas que pueden acceder al sitio en un tiempo tolerable . Si el tiempo de respuesta es superior a una determinada cantidad &quot;frustrante&quot;, esto reduce la puntuación. Los tiempos se pueden establecer usando los parámetros &quot;apdex_completed_threshold&quot; y &quot;apdex_tolerated_threshold&quot;.
- Establezca como objetivo una métrica &quot;Pedidos por hora&quot; para presentarla a los usuarios empresariales, no un recuento de usuarios virtuales. &quot;Usuarios virtuales&quot; puede ser un tema complejo para comprender qué mide la prueba en la vida real. Al calcular la tasa de conversión del sitio, los pedidos por hora, el tiempo promedio que un usuario pasa en el sitio y el tiempo de reflexión entre cada carga de página, se pueden utilizar cálculos estándar del sector para presentar diferentes escenarios de prueba de carga basados en los pedidos por hora que se van a lograr.
- Por último, el servidor de prueba Jmeter debe ejecutarse en un servidor geográficamente cerca de donde proviene la mayor parte del tráfico de usuario y donde está alojada su infraestructura en la nube. Esperamos que estos sean los mismos.
