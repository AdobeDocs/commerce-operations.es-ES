---
title: Prácticas recomendadas de configuración
description: Optimizar el tiempo de respuesta de la implementación de Adobe Commerce o Magento Open Source mediante estas prácticas recomendadas.
source-git-commit: 5b455cb1285ce764a0517008fb8b692f3899066d
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 0%

---


# Prácticas recomendadas de configuración

Commerce proporciona muchos ajustes y herramientas que puede utilizar para mejorar el tiempo de respuesta en las páginas y proporcionar un mayor rendimiento.

## Cron Jobs

Todas las operaciones asincrónicas de [!DNL Commerce] se realizan utilizando Linux `cron` comando. Consulte [Configurar y ejecutar cron](../configuration/cli/configure-cron-jobs.md) para configurarlo correctamente.

## Indexadores

Un indexador puede ejecutarse en **[!UICONTROL Update on Save]** o **[!UICONTROL Update on Schedule]** modo. El **[!UICONTROL Update on Save]** El modo de inmediatamente indexa cada vez que cambian el catálogo u otros datos. Este modo asume una baja intensidad de las operaciones de actualización y navegación en su tienda. Esto puede provocar retrasos significativos y la falta de disponibilidad de los datos durante cargas altas. Se recomienda utilizar **Actualización según lo programado** en producción, porque almacena información sobre las actualizaciones de datos y realiza la indexación por partes en segundo plano a través de un trabajo cron específico. Puede cambiar el modo de cada [!DNL Commerce] indexador por separado en la  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** página de configuración de.

>[!TIP]
>
>La reindexación en MariaDB 10.4 y 10.6 lleva más tiempo en comparación con otras MariaDB o [!DNL MySQL] versiones. Sugerimos modificar la configuración predeterminada de MariaDB, que se describe en la sección [requisitos previos de instalación](../installation/prerequisites/database/mysql.md).

## Cachés

Cuando inicie la tienda en producción, active todas las cachés del **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** página. Recomendamos encarecidamente utilizar [!DNL Varnish], ya que es una solución eficaz de caché de páginas de producción.

## Notificaciones de correo electrónico asincrónicas

Al habilitar la configuración &quot;Notificaciones por correo electrónico asincrónicas&quot; se mueven al segundo plano los procesos que administran las notificaciones por correo electrónico de cierre de compra y procesamiento de pedidos. Para habilitar esta función, vaya a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Consulte [Correos electrónicos de ventas](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) en el _Guía del usuario de Magento Open Source_ para obtener más información.

## Procesamiento asincrónico de datos de pedidos

Puede haber momentos en que las ventas intensivas en una tienda ocurren al mismo tiempo que [!DNL Commerce] está realizando un procesamiento intensivo de pedidos. Puede configurar [!DNL Commerce] para distinguir estos dos patrones de tráfico en el nivel de base de datos a fin de evitar conflictos entre las operaciones de lectura y escritura en las tablas correspondientes. Puede almacenar e indexar datos de pedido de forma asíncrona. Los pedidos se almacenan temporalmente y se mueven de forma masiva a la cuadrícula de Order Management sin que se produzcan conflictos. Puede activar esta opción desde **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Consulte [Actualizaciones programadas de cuadrícula](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) en el _Guía del usuario de Magento Open Source_ para obtener más información.

>[!WARNING]
>
>El **[!UICONTROL Developer]** Las pestañas y opciones de solo están disponibles en [Modo de desarrollador](../configuration/cli/set-mode.md). [Adobe Commerce en la infraestructura en la nube](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) no admite `Developer` modo.

## Actualización de stock diferida

En tiempos de ventas intensivas, [!DNL Commerce] puede retrasar las actualizaciones de existencias relacionadas con los pedidos. Esto minimiza el número de operaciones y acelera el proceso de colocación de pedidos. Sin embargo, esta opción es arriesgada y solo se puede utilizar cuando los pedidos no satisfechos se activan en la tienda, ya que esta opción puede dar lugar a cantidades de stock negativas. Esta opción puede proporcionar una mejora significativa del rendimiento en los flujos de cierre de compra para tiendas que pueden rellenar fácilmente sus existencias bajo demanda. Para activar las actualizaciones de stock diferidas en el sitio, vaya a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Consulte [Administración del inventario](https://docs.magento.com/user-guide/catalog/inventory.html) en el _Guía del usuario de Adobe Commerce_ para obtener más información.

>[!INFO]
>
>Esta opción solo está disponible si **[!UICONTROL Backorder with any mode]** está activada.

>[!INFO]
>
>Esta opción también funciona con [Colocación de pedido asincrónica](high-throughput-order-processing.md#asynchronous-order-placement) en combinación con [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).

## Configuración de optimización del lado del cliente

Para mejorar la capacidad de respuesta de la tienda [!DNL Commerce] En este caso, vaya a Admin en modo predeterminado o de desarrollador y cambie la siguiente configuración:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Grupo de configuración | Configuración | Valor |
| ------------------- | -------------------------- | ------ |
| Configuración de cuadrícula | Indexación asincrónica | Activar |
| Configuración de CSS | Minimizar archivos CSS | Sí |
| [!DNL JavaScript] Configuración | Minificar [!DNL JavaScript] Archivos | Sí |
| [!DNL JavaScript] Configuración | Activar [!DNL JavaScript] Agrupación | Sí |
| Configuración de plantilla | Minificar HTML | Sí |

>[!INFO]
>
>El **[!UICONTROL Developer]** Las pestañas y opciones de solo están disponibles en [Modo de desarrollador](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] en la infraestructura en la nube](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) no admite `Developer` modo.

Cuando activa el **[!UICONTROL Enable [!DNL JavaScript] Bundling]** , permite a Commerce combinar todos los recursos JS en uno o un conjunto de paquetes cargados en páginas de tienda. Agrupar JS resulta en menos solicitudes al servidor, lo que mejora el rendimiento de la página. También ayuda al explorador a almacenar en caché los recursos JS en la primera llamada y a reutilizarlos en todas las exploraciones posteriores. Esta opción también ofrece una evaluación diferida, ya que todos los JS se cargan como texto. Inicia el análisis y la evaluación del código solo después de activar acciones específicas en la página. Sin embargo, esta configuración no se recomienda en tiendas donde el primer tiempo de carga de página es extremadamente crítico, ya que todo el contenido JS se cargará en la primera llamada.

>[!INFO]
>
>Consulte [Optimización de archivos CSS y Javascript en Adobe Commerce en la infraestructura en la nube y Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) en el Centro de ayuda de Adobe Commerce para obtener más información sobre la optimización de CSS y Javascript.

### Paquetes de sugerencias

* Le recomendamos que utilice herramientas de terceros para la minificación y el agrupamiento (como [r.js](https://requirejs.org/)). [!DNL Commerce] los mecanismos integrados no son óptimos y se envían como alternativas de reserva.
* La activación del protocolo HTTP2 puede ser una buena alternativa al uso del agrupamiento JS. El protocolo ofrece prácticamente los mismos beneficios.
* No se recomienda utilizar la configuración obsoleta como la combinación de archivos JS y CSS, ya que fueron diseñados solo para JS cargados sincrónicamente en la sección HEAD de la página. El uso de esta técnica puede hacer que el agrupamiento y la lógica requireJS funcionen incorrectamente.

## Validación de segmentos del cliente

Comerciantes que tienen un gran número de [segmentos del cliente](https://docs.magento.com/user-guide/marketing/customer-segments.html) puede experimentar una degradación significativa del rendimiento con las acciones del cliente, como iniciar sesión y agregar productos al carro de compras.

Déclencheur Las acciones del cliente configuran un proceso de validación para los segmentos del cliente, que es lo que puede causar una degradación del rendimiento. De forma predeterminada, Adobe Commerce valida cada segmento en tiempo real para definir qué segmentos del cliente coinciden y cuáles no.

Para evitar la degradación del rendimiento, puede establecer el **[!UICONTROL Real-time Check if Customer is Matched by Segment]** opción de configuración del sistema a **No** para validar segmentos de clientes mediante una única consulta SQL de condición combinada.

Para habilitar esta optimización, vaya a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

Esta configuración mejora el rendimiento de la validación de segmentos del cliente si hay muchos segmentos de cliente en el sistema. Sin embargo, no funciona con [base de datos dividida](../configuration/storage/multi-master.md) implementaciones o cuando no hay clientes registrados.

## Programación de mantenimiento de base de datos {#database}

Se recomienda realizar copias de seguridad periódicas de la base de datos para las instancias de ensayo y producción. Debido a la naturaleza intensiva de E/S de las operaciones de copia de seguridad, puede encontrar copias de seguridad más lentas y posibles problemas. La ejecución de procesos de base de datos para varios entornos al mismo tiempo puede resultar potencialmente más lenta debido a la contención por los recursos disponibles.

Para obtener un mejor rendimiento, programe las copias de seguridad para que se ejecuten sucesivamente, de una en una, en las horas de menor actividad. Este método evita la contención de E/S y reduce el tiempo de finalización, especialmente para instancias más pequeñas, bases de datos más grandes, etc.

Por ejemplo, se recomienda programar una copia de seguridad de la base de datos de producción seguida de la base de datos de ensayo cuando las tiendas reciban menos visitas.

## Limitar el número de productos en la cuadrícula

Para mejorar el rendimiento de la cuadrícula de productos en los catálogos grandes, se recomienda limitar el número de productos en la cuadrícula con el **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** configuración del sistema.

Esta opción de configuración del sistema está deshabilitada de forma predeterminada. Si lo habilita, puede limitar el número de productos en la cuadrícula a un valor específico. **[!UICONTROL Records Limit]** es una configuración personalizable que tiene un valor mínimo predeterminado de `20000`.
Si la variable **[!UICONTROL Limit Number of Products in Grid]** la configuración está habilitada y el número de productos en la cuadrícula es bueno que el límite de registros, por lo que se devuelve la colección limitada de registros. Cuando se alcanza el límite, el total de registros encontrados, el número de registros seleccionados y los elementos de paginación se ocultan del encabezado de la cuadrícula.

Cuando el número total de productos en la cuadrícula es limitado, no afecta a las acciones de masa de la cuadrícula de productos. Solo afecta a la capa de presentación de la cuadrícula de productos. Por ejemplo, hay un número limitado de `20000` productos en la cuadrícula, el usuario hace clic en **[!UICONTROL Select All]**, selecciona el **[!UICONTROL Update attributes]** acción masiva y actualiza algunos atributos. Como resultado, se actualizan todos los productos, no la colección limitada de `20000` registros.

La limitación de la cuadrícula de productos solo afecta a las colecciones de productos que utilizan los componentes de la interfaz de usuario. Como resultado, esta limitación no afecta a todas las cuadrículas de productos. Solo los que utilizan `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
Puede limitar las colecciones de cuadrículas de productos solo en las páginas siguientes:

* Cuadrícula de producto de catálogo
* Agregar cuadrícula de productos relacionados/de ampliación de venta/de venta cruzada
* Añadir productos al paquete de productos
* Añadir productos al grupo de productos
* Página Administrador: Crear Pedido

Si no desea que la cuadrícula de productos esté limitada, le recomendamos que utilice filtros de forma más precisa para que la colección de resultados tenga menos elementos que **[!UICONTROL Records Limit]**.

