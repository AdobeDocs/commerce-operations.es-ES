---
title: Prueba comparativa de rendimiento
description: Revise los resultados de los análisis de rendimiento para implementaciones de Adobe Commerce alojadas en la infraestructura de nube de Adobe.
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
source-git-commit: 09a42dc68836b34eab2c9d90879b897729cd1b09
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Resumen de referencia

Los resultados de referencia de rendimiento de Adobe Commerce 2.4.5 reflejan el rendimiento medido en una instancia de Adobe Commerce implementada con la siguiente infraestructura y componentes adicionales.
- [Entorno de nube Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) con [arquitectura escalada](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [B2B para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe Commerce Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

No hay personalizaciones adicionales.

La siguiente información resume los resultados de referencia y proporciona información sobre el entorno y los datos utilizados durante las pruebas.

## Métricas clave de rendimiento

La siguiente figura muestra la configuración del almacén de comercio para la referencia de rendimiento y las métricas clave de rendimiento de los resultados de la prueba.

![Medidor de referencia de rendimiento JMeter e infraestructura de producción](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

Basándose en criterios de prueba que imitan una organización empresarial B2C, el sistema puede gestionar el tráfico solicitado y los números de pedido durante las horas de mayor actividad, con un flujo de carga estándar.

### Aspectos destacados del rendimiento

- **Pedidos**: se procesaron 3.481 pedidos por minuto y se mantuvieron tiempos de respuesta inferiores a 2 segundos para el percentil 99 (el 99% de las solicitudes se atendieron con un tiempo de respuesta inferior a 2 segundos).
- **Vistas de página**: se han gestionado más de 2 millones de vistas de página por hora manteniendo tiempos de respuesta inferiores a 2 segundos para el percentil 99.
- **SKU efectivos**—El perfil del cliente incluía 242 millones de variaciones de precios diferentes (<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKU</a>) para 250.000 productos.
- **Solicitudes de GraphQL**: el sistema se escaló a 10.500 solicitudes de GraphQL no almacenadas en caché por minuto, mientras que se mantenían tiempos de respuesta inferiores a 2 segundos para el percentil 99.
- **Usuarios administradores simultáneos**: sistema escalado para admitir 500 usuarios administradores simultáneos mientras se mantienen tiempos de respuesta inferiores a 2 segundos para el percentil 99.

## Entorno de prueba

Los resultados de referencia de rendimiento se obtuvieron probando con una instancia de Adobe Commerce 2.4.5 implementada en un entorno de nube Pro con arquitectura escalada. La instancia también tenía instalados, configurados y habilitados los módulos Adobe Commerce B2B, Inventory management y Adobe Stock Integration .

Los datos de prueba de rendimiento para el perfil de prueba se generaron usando la variable <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Kit de herramientas de rendimiento</a>.

Las mediciones de rendimiento se basan en actividades diarias simuladas de tiendas para clientes y usuarios empresariales. Los valores reflejan un rendimiento casi máximo para cada caso, pero no reflejan modelos empresariales únicos, como ventas privadas o ventas flash.

- **Tienda LUMA**
   - 3000 usuarios simultáneos en tienda
   - Se establece en una tasa de aciertos de caché de CDN del 30%

      El uso efectivo de la capa de caché aumenta el número de vistas de página por hora.

- **API de GraphQL**
   - 250 subprocesos simultáneos
   - Establecer en una tasa de aciertos de caché de CDN del 0%

      Los tiempos de respuesta mejoran significativamente con una capa de almacenamiento en caché delante de GraphQL.

- **Web de administración**
   - 500 usuarios simultáneos
   - Establecer en una tasa de aciertos de caché de CDN del 0%

## Probar especificaciones del entorno

La prueba de carga se completó con perfiles de carga de JMeter ejecutados con la instancia de Adobe Commerce. Durante la prueba se utilizaron tres nodos web y tres nodos de servicio. La siguiente imagen detalla el punto de entrada de JMeter y la infraestructura de producción.

![Medidor de referencia de rendimiento JMeter e infraestructura de producción](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### Aplicación

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> implementada en infraestructura de nube con arquitectura Pro.

### Infraestructura

Para la referencia de rendimiento, Adobe Commerce 2.4.5 se implementó en un [infraestructura escalable](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) con la siguiente capacidad.

- **Especificaciones del nodo web**
   - vCPU 216 (72 x 3 nodos)
   - Memoria 432 GiB (144 x 3 nodos)
   - Ancho de banda de red de 768 Gbps (256 x 3 nodos)
   - Almacenamiento aprovisionado de 100 GB

- **Especificaciones del nodo de servicio**
   - vCPU 192 (64 x 3 nodos)
   - Memoria 768 GiB (256 x 3 nodos)
   - Ancho de banda de red de 60 Gbps (20 x 3 nodos)
   - Ancho de banda EBS 40800 Mbps (13600 x 3 nodos)
   - Almacenamiento aprovisionado de 1100 GB
