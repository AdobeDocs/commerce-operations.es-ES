---
title: Parámetros de rendimiento
description: Revise los resultados de las pruebas de rendimiento de las implementaciones de Adobe Commerce alojadas en la infraestructura de la nube de Adobe.
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Resumen de referencia

Los resultados del análisis de rendimiento de Adobe Commerce 2.4.5 reflejan el rendimiento medido en una instancia de Adobe Commerce implementada con la siguiente infraestructura y componentes adicionales.
- [Entorno de nube profesional](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) con [arquitectura escalada](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [B2B para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe Commerce Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

No hay personalizaciones adicionales.

La siguiente información resume los resultados del análisis de rendimiento y proporciona información sobre el entorno y los datos utilizados durante las pruebas.

## Métricas clave de rendimiento

La siguiente figura muestra la configuración de la tienda de Commerce para el análisis de rendimiento y las métricas de rendimiento clave de los resultados de la prueba.

![Infraestructura de producción y JMeter de referencia de rendimiento](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

Según los criterios de prueba que imitan a una organización B2C empresarial, el sistema puede gestionar el tráfico solicitado y los números de pedido durante las horas de mayor actividad, con un flujo de carga estándar.

### Aspectos destacados del rendimiento

- **Pedidos**: procesó 3.481 pedidos por minuto mientras mantenía tiempos de respuesta de menos de 2 segundos para el percentil 99 (el 99% de las solicitudes se atendieron con un tiempo de respuesta de menos de 2 segundos).
- **Vistas de página**: se administraron más de 2 millones de vistas de página por hora mientras se mantenían tiempos de respuesta de menos de 2 segundos para el percentil 99.
- **SKU efectivas**: el perfil del cliente incluyó 242 millones de variaciones de precio diferentes (<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKU</a>) para 250 000 productos.
- **solicitudes de GraphQL**: el sistema se amplió a 10.500 solicitudes de GraphQL sin caché por minuto mientras se mantenían tiempos de respuesta de menos de 2 segundos para el percentil 99.
- **Usuarios administradores simultáneos**: el sistema se amplió para admitir 500 usuarios administradores simultáneos y se mantuvieron los tiempos de respuesta de menos de 2 segundos para el percentil 99.

## Entorno de prueba

Los resultados de las pruebas de rendimiento se obtuvieron comparándolos con una instancia de Adobe Commerce 2.4.5 implementada en un entorno de nube Pro con arquitectura escalada. La instancia también tenía instalados, configurados y habilitados los módulos de integración de Adobe Commerce B2B, Inventory management y Adobe Stock.

Los datos de las pruebas de rendimiento del perfil de prueba se generaron usando <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Performance Toolkit</a>.

Las mediciones de rendimiento se basan en actividades simuladas de tiendas diarias para clientes y usuarios empresariales. Los valores reflejan un rendimiento cercano al máximo para cada caso, pero no reflejan modelos empresariales únicos, como ventas privadas o ventas flash.

- **Tienda LUMA**
   - 3000 usuarios simultáneos en la tienda
   - Establezca en Tasa de aciertos de caché de CDN del 30 %

     El uso efectivo de la capa de caché aumenta el número de vistas de página por hora.

- **API de GraphQL**
   - 250 hilos simultáneos
   - Establezca en Tasa de aciertos de caché de CDN al 0%

     Los tiempos de respuesta mejoran significativamente con una capa de almacenamiento en caché delante de GraphQL.

- **Web de administración**
   - 500 usuarios simultáneos
   - Establezca en Tasa de aciertos de caché de CDN al 0%

## Especificaciones del entorno de prueba

La prueba de carga se completó con los perfiles de carga de JMeter ejecutados en la instancia de Adobe Commerce. Durante la prueba se utilizaron tres nodos web y tres nodos de servicio. La siguiente imagen detalla el punto de entrada de la infraestructura de JMeter y Producción.

![Infraestructura de producción y JMeter de referencia de rendimiento](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### Aplicación

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> implementado en infraestructura en la nube con arquitectura Pro.

### Infraestructura

Para la referencia de rendimiento, Adobe Commerce 2.4.5 se implementó en una [infraestructura escalable](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) con la siguiente capacidad.

- **Especificaciones del nodo web**
   - vCPU 216 (72 x 3 nodos)
   - Memoria 432 GiB (144 x 3 nodos)
   - Ancho de banda de red 768 Gb/s (256 x 3 nodos)
   - Ancho de banda EBS 57000 Mbps (19000 x 3 nodos)
   - Almacenamiento aprovisionado de 100 GB

- **Especificaciones del nodo de servicio**
   - vCPU 192 (64 x 3 nodos)
   - Memoria 768 GiB (256 x 3 nodos)
   - Ancho de banda de red 60 Gb/s (20 x 3 nodos)
   - Ancho de banda EBS 40800 Mbps (13600 x 3 nodos)
   - Almacenamiento aprovisionado de 1100 GB
