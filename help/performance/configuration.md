---
title: Prácticas recomendadas de configuración
description: Optimice el tiempo de respuesta de su implementación de Adobe Commerce o Magento Open Source mediante estas prácticas recomendadas.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---


# Prácticas recomendadas de configuración

Commerce proporciona muchos ajustes y herramientas que puede utilizar para mejorar el tiempo de respuesta en las páginas, así como para proporcionar un mayor rendimiento.

## Trabajos cron

Todas las operaciones asincrónicas en [!DNL Commerce] se realizan utilizando Linux `cron` comando. Consulte [Configuración y ejecución de cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) para configurarlo correctamente.

## Indexadores

Un indizador puede ejecutarse en **[!UICONTROL Update on Save]** o **[!UICONTROL Update on Schedule]** en el menú contextual. La variable **[!UICONTROL Update on Save]** se indexa inmediatamente cuando cambia el catálogo u otros datos. Este modo supone una baja intensidad de las operaciones de actualización y navegación en su tienda. Puede provocar retrasos importantes y la falta de disponibilidad de datos durante las cargas elevadas. Se recomienda usar **Actualización según lo programado** en producción, ya que almacena información sobre actualizaciones de datos y realiza la indexación por partes en segundo plano a través de un trabajo cron específico. Puede cambiar el modo de cada [!DNL Commerce] indexador por separado en el  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** página de configuración.

La reindexación en MariaDB 10.4 lleva más tiempo que otras MariaDB o [!DNL MySQL] versiones. Como solución alternativa, sugerimos modificar la configuración predeterminada de MariaDB y establecer los siguientes parámetros:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

## Cachés

Cuando inicie la tienda en producción, active todas las cachés desde la **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** página. Se recomienda encarecidamente utilizar [!DNL Varnish], ya que es una solución de caché de página de producción eficiente.

## Notificaciones de correo electrónico asincrónicas

Al habilitar la opción &quot;Notificaciones de correo electrónico asincrónicas&quot;, se mueven al fondo los procesos que administran las notificaciones de cierre de compra y procesamiento de solicitudes por correo electrónico. Para habilitar esta función, vaya a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Consulte [Correos electrónicos de ventas](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) en el _Guía del usuario del Magento Open Source_ para obtener más información.

## Procesamiento asincrónico de datos de pedidos

Puede haber momentos en que se producen ventas intensivas en una tienda al mismo tiempo que [!DNL Commerce] está realizando un procesamiento intensivo de pedidos. Puede configurar [!DNL Commerce] para distinguir estos dos patrones de tráfico en el nivel de base de datos para evitar conflictos entre las operaciones de lectura y escritura en las tablas correspondientes. Los datos de pedidos se pueden almacenar e indexar de forma asíncrona. Los pedidos se colocan en un almacenamiento temporal y se mueven de forma masiva a la cuadrícula Gestión de pedidos sin conflictos. Puede activar esta opción desde **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Consulte [Actualizaciones de cuadrícula programadas](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) en el _Guía del usuario del Magento Open Source_ para obtener más información.

>[!WARNING]
>
>La variable **[!UICONTROL Developer]** y las opciones solo están disponibles en [Modo de desarrollador](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-mode.html). [Adobe Commerce en infraestructura en la nube](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) no es compatible `Developer` en el menú contextual.

## Actualización de stock diferido

En tiempos de ventas intensivas, [!DNL Commerce] puede retrasar las actualizaciones de stock relacionadas con pedidos. Esto minimiza el número de operaciones y acelera el proceso de colocación de pedidos. Sin embargo, esta opción es riesgosa y solo se puede utilizar cuando se activan Backorders en la tienda, ya que esta opción puede generar cantidades de stock negativas. Esta opción puede proporcionar una mejora significativa en el rendimiento de los flujos de cierre de compra para las tiendas que pueden rellenar fácilmente sus existencias bajo demanda. Para activar las actualizaciones de stock diferidas en su sitio, vaya a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Consulte [Administración de inventario](https://docs.magento.com/user-guide/catalog/inventory.html) en el _Guía del usuario de Adobe Commerce_ para obtener más información.

>[!INFO]
>
>Esta opción solo está disponible si **[!UICONTROL Backorder with any mode]** está activada.

## Configuración de optimización del lado del cliente

Para mejorar la capacidad de respuesta de la tienda de su [!DNL Commerce] , vaya al modo Administrador en modo predeterminado o Desarrollador y cambie la siguiente configuración:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Grupo de configuración | Configuración | Valor |
| ------------------- | -------------------------- | ------ |
| Configuración de cuadrícula | Indexación asíncrona | Habilitar |
| Configuración de CSS | Minimizar archivos CSS | Sí |
| [!DNL JavaScript] Configuración | Minificar [!DNL JavaScript] Archivos | Sí |
| [!DNL JavaScript] Configuración | Habilitar [!DNL JavaScript] Agrupación | Sí |
| Configuración de plantilla | Minificar HTML | Sí |

>[!INFO]
>
>La variable **[!UICONTROL Developer]** y las opciones solo están disponibles en [Modo de desarrollador](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-mode.html). [Adobe [!DNL Commerce] en la infraestructura de nube](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) no es compatible `Developer` en el menú contextual.

Al activar el **[!UICONTROL Enable [!DNL JavaScript] Bundling]** , permite que Commerce combine todos los recursos JS en uno o un conjunto de paquetes que se cargan en páginas de tienda. Al empaquetar JS, se atenúan las solicitudes al servidor, lo que mejora el rendimiento de la página. También ayuda al explorador a almacenar en caché los recursos JS en la primera llamada y reutilizarlos para todas las exploraciones posteriores. Esta opción también ofrece una evaluación diferida, ya que todos los JS se cargan como texto. Inicia el análisis y la evaluación del código solo después de activar acciones específicas en la página. Sin embargo, no se recomienda esta configuración para las tiendas en las que el tiempo de carga de la primera página sea extremadamente crítico, ya que todo el contenido de JS se cargará en la primera llamada.

>[!INFO]
>
>Consulte [Optimización de archivos CSS y Javascript en Adobe Commerce en infraestructura en la nube y Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) en el Centro de ayuda de Adobe Commerce_ para obtener más información sobre la optimización de CSS y Javascript.

### Sugerencias de agrupamiento

* Le recomendamos que utilice herramientas de terceros para la minificación y el agrupamiento (como [r.js](https://requirejs.org/)). [!DNL Commerce] los mecanismos integrados no son óptimos y se envían como alternativas de reserva.
* La activación del protocolo HTTP2 puede ser una buena alternativa al uso del paquete JS. El protocolo ofrece casi las mismas ventajas.
* No se recomienda utilizar configuraciones obsoletas como la combinación de archivos JS y CSS, ya que solo se diseñaron para JS cargados sincrónicamente en la sección HEAD de la página. El uso de esta técnica puede hacer que el agrupamiento y la lógica de requiredJS funcionen incorrectamente.

## Calendario de mantenimiento de la base de datos {#database}

Se recomienda realizar copias de seguridad periódicas de la base de datos para las instancias de Ensayo y Producción. Debido a la naturaleza intensiva de I/O de las operaciones de backup, puede encontrar backups más lentos y posibles problemas. La ejecución de procesos de base de datos para varios entornos al mismo tiempo puede resultar más lenta debido a la contención de los recursos disponibles.

Para obtener un mejor rendimiento, programe los backups para que se ejecuten sucesivamente, uno a la vez, en las horas de menor actividad. Este método evita la contención de E/S y reduce el tiempo para completarse, especialmente en instancias más pequeñas, bases de datos más grandes, etc.

Por ejemplo, se recomienda programar una copia de seguridad de la base de datos de producción seguida de la base de datos de ensayo cuando las tiendas tengan menos visitas.
