---
title: Prácticas recomendadas de configuración
description: Obtenga información acerca de las prácticas recomendadas de configuración para optimizar el rendimiento de Adobe Commerce. Descubra la configuración y las herramientas para mejorar el tiempo de respuesta y el rendimiento.
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1424'
ht-degree: 0%

---

# Prácticas recomendadas de configuración

Commerce proporciona muchos ajustes y herramientas que puede utilizar para mejorar el tiempo de respuesta en las páginas y proporcionar un mayor rendimiento.

## Cron Jobs

Todas las operaciones asincrónicas de [!DNL Commerce] se realizan con el comando Linux `cron`. Consulte [Configurar y ejecutar cron](../configuration/cli/configure-cron-jobs.md) para configurarlo correctamente.

## Indexadores

Un indizador se puede ejecutar en modo **[!UICONTROL Update on Save]** o **[!UICONTROL Update on Schedule]**. El modo **[!UICONTROL Update on Save]** indiza inmediatamente cada vez que cambia el catálogo u otros datos. Este modo asume una baja intensidad de las operaciones de actualización y navegación en su tienda. Esto puede provocar retrasos significativos y la falta de disponibilidad de los datos durante cargas altas. Se recomienda usar **Actualización programada** con fines de rendimiento, ya que almacena información sobre actualizaciones de datos y realiza la indexación por partes en segundo plano a través de un trabajo cron específico. Puede cambiar el modo de cada indizador [!DNL Commerce] por separado en la página de configuración **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]**. El índice [!UICONTROL Customer Grid] siempre debe establecerse en el modo **[!UICONTROL Update on Save]**.

>[!TIP]
>
>La reindexación en MariaDB 10.4 y 10.6 tarda más tiempo en comparación con otras versiones de MariaDB o [!DNL MySQL]. Se recomienda modificar la configuración predeterminada de MariaDB, que se describe en los [requisitos previos de instalación](../installation/prerequisites/database/mysql.md).

## Cachés

Cuando inicie su tienda en producción, active todas las cachés de la página **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]**. Se recomienda encarecidamente usar [!DNL Varnish], ya que es una solución eficiente de caché de páginas de producción.

## Notificaciones de correo electrónico asincrónicas

Al habilitar la configuración &quot;Notificaciones por correo electrónico asincrónicas&quot; se mueven al segundo plano los procesos que administran las notificaciones por correo electrónico de cierre de compra y procesamiento de pedidos. Para habilitar esta característica, vaya a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Consulte [Correos electrónicos de ventas](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales-emails) en la _Guía del usuario de administración_ para obtener más información.

## Procesamiento asincrónico de datos de pedidos

Puede haber momentos en que se produzcan ventas intensivas en una tienda al mismo tiempo que [!DNL Commerce] está realizando un procesamiento intensivo de pedidos. Puede configurar [!DNL Commerce] para distinguir estos dos patrones de tráfico en el nivel de base de datos a fin de evitar conflictos entre las operaciones de lectura y escritura en las tablas correspondientes. Puede almacenar e indexar datos de pedido de forma asíncrona. Los pedidos se almacenan temporalmente y se mueven de forma masiva a la cuadrícula de Order Management sin que se produzcan conflictos. Puede activar esta opción desde **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Consulte [Actualizaciones programadas de cuadrícula](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations#enable-scheduled-grid-updates-and-reindexing) en la _Guía del usuario de administración_ para obtener más información.

>[!WARNING]
>
>La ficha **[!UICONTROL Developer]** y las opciones solo están disponibles en [modo de desarrollador](../configuration/cli/set-mode.md). [Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) no admite el modo `Developer`.

## Guardado de configuración asíncrona

Para los proyectos con un gran número de configuraciones en el nivel de almacén, guardar una configuración de almacén puede llevar una cantidad excesiva de tiempo o provocar un tiempo de espera. El módulo _Async Config_ habilita los guardados de configuración asincrónica ejecutando un trabajo cron que usa un consumidor para procesar el guardado en una cola de mensajes. AsyncConfig está **deshabilitado** de manera predeterminada.

Puede habilitar AsyncConfig mediante la interfaz de la línea de comandos:

```bash
bin/magento setup:config:set --config-async 1
```

El comando `set` escribe lo siguiente en el archivo `app/etc/env.php`:

```conf
...
   'config' => [
       'async' => 1
   ]
```

Inicie el siguiente Consumidor para comenzar a procesar los mensajes en cola en el orden de entrada y salida:

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## Actualización de stock diferida

En tiempos de ventas intensas, [!DNL Commerce] puede aplazar las actualizaciones de existencias relacionadas con los pedidos. Esto minimiza el número de operaciones y acelera el proceso de colocación de pedidos. Sin embargo, esta opción es arriesgada y solo se puede utilizar cuando los pedidos no satisfechos se activan en la tienda, ya que esta opción puede dar lugar a cantidades de stock negativas. Esta opción puede proporcionar una mejora significativa del rendimiento en los flujos de cierre de compra para tiendas que pueden rellenar fácilmente sus existencias bajo demanda. Para activar las actualizaciones de existencias diferidas en el sitio, vaya a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Consulte [Administración de inventario](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud) en la _Guía del usuario de Adobe Commerce_ para obtener más información.

>[!INFO]
>
>Esta opción solo está disponible si **[!UICONTROL Backorder with any mode]** está activado.

>[!INFO]
>
>Esta opción también funciona con [ubicación asincrónica de pedidos](high-throughput-order-processing.md#asynchronous-order-placement) en combinación con [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).

## Configuración de optimización del lado del cliente

Para mejorar la capacidad de respuesta de la tienda de su instancia de [!DNL Commerce], vaya al modo de administrador predeterminado o de desarrollador y cambie la siguiente configuración:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Grupo de configuración | Configuración | Valor |
| ------------------- | -------------------------- | ------ |
| Configuración de cuadrícula | Indexación asincrónica | Activar |
| Configuración de CSS | Minimizar archivos CSS | Sí |
| Configuración de [!DNL JavaScript] | Minificar [!DNL JavaScript] archivos | Sí |
| Configuración de [!DNL JavaScript] | Habilitar agrupación [!DNL JavaScript] | Sí |
| Configuración de plantilla | Minificar HTML | Sí |

>[!INFO]
>
>La ficha **[!UICONTROL Developer]** y las opciones solo están disponibles en [modo de desarrollador](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] en la infraestructura en la nube](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) no admite el modo `Developer`.

Al activar la opción **[!UICONTROL Enable [!DNL JavaScript] Bundling]**, permite que Commerce combine todos los recursos JS en uno o un conjunto de paquetes que se cargan en páginas de tienda. Agrupar JS resulta en menos solicitudes al servidor, lo que mejora el rendimiento de la página. También ayuda al explorador a almacenar en caché los recursos JS en la primera llamada y a reutilizarlos en todas las exploraciones posteriores. Esta opción también ofrece una evaluación diferida, ya que todos los JS se cargan como texto. Inicia el análisis y la evaluación del código solo después de activar acciones específicas en la página. Sin embargo, esta configuración no se recomienda en tiendas donde el primer tiempo de carga de página es extremadamente crítico, ya que todo el contenido JS se cargará en la primera llamada.

>[!INFO]
>
>Consulte [Optimización de archivos CSS y Javascript en Adobe Commerce en la infraestructura en la nube y Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) en el Centro de ayuda de Adobe Commerce_ para obtener más información sobre la optimización de CSS y Javascript.

### Paquetes de sugerencias

* Le recomendamos que utilice herramientas de terceros para la minificación y el agrupamiento (como [r.js](https://requirejs.org/)). Los mecanismos integrados de [!DNL Commerce] no son óptimos y se envían como alternativas de reserva.
* La activación del protocolo HTTP/2 puede ser una buena alternativa al uso del agrupamiento JS. El protocolo ofrece muchas de las mismas ventajas. Está habilitado de forma predeterminada en Adobe Commerce en proyectos de infraestructura en la nube.
* No se recomienda utilizar la configuración obsoleta como la combinación de archivos JS y CSS, ya que fueron diseñados solo para JS cargados sincrónicamente en la sección HEAD de la página. El uso de esta técnica puede hacer que el agrupamiento y la lógica requireJS funcionen incorrectamente.

## Validación de segmentos del cliente

Los comerciantes que tienen un gran número de [segmentos de clientes](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments) pueden experimentar una degradación significativa del rendimiento con las acciones de los clientes, como el inicio de sesión de clientes y la adición de productos al carro de compras.

Déclencheur Las acciones del cliente configuran un proceso de validación para los segmentos del cliente, que es lo que puede causar una degradación del rendimiento. De forma predeterminada, Adobe Commerce valida cada segmento en tiempo real para definir qué segmentos del cliente coinciden y cuáles no.

Para evitar la degradación del rendimiento, puede establecer la opción de configuración del sistema **[!UICONTROL Real-time Check if Customer is Matched by Segment]** en **No** para validar segmentos de clientes mediante una única consulta SQL de condición combinada.

Para habilitar esta optimización, vaya a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

Esta configuración mejora el rendimiento de la validación de segmentos del cliente si hay muchos segmentos de cliente en el sistema. Sin embargo, no funciona con implementaciones de [split database](../configuration/storage/multi-master.md) o cuando no hay clientes registrados.

## Programación de mantenimiento de base de datos {#database}

Se recomienda realizar copias de seguridad periódicas de la base de datos para las instancias de ensayo y producción. Debido a la naturaleza intensiva de E/S de las operaciones de copia de seguridad, puede encontrar copias de seguridad más lentas y posibles problemas. La ejecución de procesos de base de datos para varios entornos al mismo tiempo puede resultar potencialmente más lenta debido a la contención por los recursos disponibles.

Para obtener un mejor rendimiento, programe las copias de seguridad para que se ejecuten sucesivamente, de una en una, en las horas de menor actividad. Este método evita la contención de E/S y reduce el tiempo de finalización, especialmente para instancias más pequeñas, bases de datos más grandes, etc.

Por ejemplo, se recomienda programar una copia de seguridad de la base de datos de producción seguida de la base de datos de ensayo cuando las tiendas reciban menos visitas.

## Limitar el número de productos en la cuadrícula

Para mejorar el rendimiento de la cuadrícula de productos en catálogos grandes, se recomienda limitar el número de productos en la cuadrícula con la configuración del sistema **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]**.

Esta opción de configuración del sistema está deshabilitada de forma predeterminada. Si lo habilita, puede limitar el número de productos en la cuadrícula a un valor específico. **[!UICONTROL Records Limit]** es una configuración personalizable que tiene un valor mínimo predeterminado de `20000`.
Cuando la configuración **[!UICONTROL Limit Number of Products in Grid]** está habilitada y el número de productos en la cuadrícula es mayor que el límite de registros, se devuelve la colección limitada de registros. Cuando se alcanza el límite, el total de registros encontrados, el número de registros seleccionados y los elementos de paginación se ocultan del encabezado de la cuadrícula.

Cuando el número total de productos en la cuadrícula es limitado, no afecta a las acciones de masa de la cuadrícula de productos. Solo afecta a la capa de presentación de la cuadrícula de productos. Por ejemplo, hay un número limitado de `20000` productos en la cuadrícula, el usuario hace clic en **[!UICONTROL Select All]**, selecciona la acción masiva **[!UICONTROL Update attributes]** y actualiza algunos atributos. Como resultado, se actualizarán todos los productos, no la colección limitada de `20000` registros.

La limitación de la cuadrícula de productos solo afecta a las colecciones de productos que utilizan los componentes de la interfaz de usuario. Como resultado, esta limitación no afecta a todas las cuadrículas de productos. Solamente los que están usando `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
Puede limitar las colecciones de cuadrículas de productos solo en las páginas siguientes:

* Cuadrícula de producto de catálogo
* Agregar cuadrícula de productos relacionados/de ampliación de venta/de venta cruzada
* Añadir productos al paquete de productos
* Añadir productos al grupo de productos
* Página Administrador: Crear Pedido

Si no desea que la cuadrícula de productos esté limitada, le recomendamos que utilice filtros más precisos para que la colección de resultados tenga menos elementos que **[!UICONTROL Records Limit]**.
