---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.77'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.77.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 98ccb5c357ebcb3bc2a7bb48e61b8557a65049f9
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.77

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.77.

QPT v1.1.77 incluye los siguientes parches:

1. **[ACSD-63687](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-63687.md)**: corrige un problema en el que se muestran precios incorrectos porque no es posible limpiar la caché de [!DNL Redis].
1. **[ACSD-68341](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68341.md)**: corrige un problema en el cual la cookie `X-Magento-Vary` se establece varias veces durante la carga de PDP, cuando se crean varios segmentos de clientes en la tienda.
1. **[ACSD-68537](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68537.md)**: corrige un problema en el cual el rendimiento del cierre de compra se degradaba a medida que aumentaba el número de segmentos del cliente.
1. **[ACSD-68664](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68664.md)**: corrige un problema en el que la vista previa de la actualización programada se interrumpe al intentar obtener una vista previa del contenido para tiendas con dominios personalizados.
1. **[ACSD-68759](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68759.md)**: se corrige un problema por el que al crear una cuenta de cliente se produce un error al usar la configuración regional árabe y el atributo Fecha de nacimiento (DOB) está establecido para mostrarse en la tienda.
1. **[ACSD-68892](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68892.md)**: corrige un problema en el cual las páginas almacenables en caché no se almacenan o proporcionan correctamente desde la caché [!DNL Fastly], lo que da como resultado un comportamiento de almacenamiento en caché incoherente y un rendimiento reducido.
1. **[ACSD-69016](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69016.md)**: corrige un problema por el que el precio especial no tiene efecto para los sitios web creados en diferentes zonas horarias.
1. **[ACSD-69020](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69020.md)**: corrige un problema en el cual un producto configurable se incluye automáticamente en [!DNL Page Builder] listados de carrusel de productos si alguno de sus productos secundarios cumple las condiciones de filtrado.
1. **[ACSD-69237](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69237.md)**: corrige un problema en el cual el número de entradas que se pueden procesar e insertar a través de los `sales_*_async_insert` trabajos cron está limitado a *100* por ejecución.
1. **[ACSD-69311](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69311.md)**: corrige un problema con el cálculo de impuestos incorrecto en las notas de abono al crear un reembolso parcial a partir de una factura, si se creó una nota de abono anterior desde la página de vista de pedidos.
1. **[ACSD-69351](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69351.md)**: corrige un problema por el que los saldos de las tarjetas regalo y las fechas de caducidad no se muestran de acuerdo con el ámbito del sitio web asignado.
1. **[ACSD-69494](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69494.md)**: corrige un problema con las operaciones de devolución asincrónicas en las que las solicitudes de devolución con el parámetro `is_online` no se procesan correctamente.

Utilice el menú de la izquierda para navegar a una página específica del parche.
