---
title: Parámetros de rendimiento
description: Revise los resultados de las pruebas de rendimiento de las implementaciones de Adobe Commerce alojadas en la infraestructura de la nube de Adobe.
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
source-git-commit: eeb7146a8051e8692ebf974d65db75a4999cf2e6
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# Resumen de referencia

Los resultados del análisis de rendimiento de Adobe Commerce 2.4.5 reflejan el rendimiento medido en una instancia de Adobe Commerce implementada con la siguiente infraestructura y componentes adicionales.
- [Entorno en la nube de Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) con [arquitectura a escala](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [B2B para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe Commerce Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

No hay personalizaciones adicionales.

La siguiente información resume los resultados del análisis de rendimiento y proporciona información sobre el entorno y los datos utilizados durante las pruebas.

## Métricas clave de rendimiento

La siguiente figura muestra la configuración de la tienda de Commerce para la referencia de rendimiento y las métricas de rendimiento clave de los resultados de la prueba.

![Referencia de rendimiento JMeter e infraestructura de producción](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

Según los criterios de prueba que imitan a una organización B2C empresarial, el sistema puede gestionar el tráfico solicitado y los números de pedido durante las horas de mayor actividad, con un flujo de carga estándar.

### Aspectos destacados del rendimiento

- **Pedidos**—Procesó 3.481 pedidos por minuto mientras mantuvo tiempos de respuesta de menos de 2 segundos para el percentil 99 (el 99 % de las solicitudes se atendieron con un tiempo de respuesta de menos de 2 segundos).
- **Page views**: se gestionaron más de 2 millones de vistas de página por hora mientras se mantuvieron los tiempos de respuesta de menos de 2 segundos para el percentil 99.
- **SKU efectivas**—El perfil del cliente incluyó 242 millones de variaciones de precios diferentes (<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKU</a>) para 250.000 productos.
- **Solicitudes de GraphQL**: el sistema se amplió a 10 500 solicitudes sin caché de GraphQL por minuto mientras se mantenían los tiempos de respuesta de menos de 2 segundos para el percentil 99.
- **Usuarios administradores simultáneos**: el sistema se ha escalado para admitir 500 usuarios administradores simultáneos y mantener los tiempos de respuesta de menos de 2 segundos para el percentil 99.

## Entorno de prueba

Los resultados de las pruebas de rendimiento se obtuvieron comparándolos con una instancia de Adobe Commerce 2.4.5 implementada en un entorno de nube Pro con arquitectura escalada. La instancia también tenía instalados, configurados y habilitados los módulos de integración de Adobe Commerce B2B, Inventory management y Adobe Stock.

Los datos de las pruebas de rendimiento del perfil de prueba se generaron utilizando <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Performance Toolkit</a>.

Las mediciones de rendimiento se basan en actividades simuladas de tiendas diarias para clientes y usuarios empresariales. Los valores reflejan un rendimiento cercano al máximo para cada caso, pero no reflejan modelos empresariales únicos, como ventas privadas o ventas flash.

- **Tienda de LUMA**
   - 3000 usuarios simultáneos en la tienda
   - Establezca en Tasa de aciertos de caché de CDN del 30 %

      El uso efectivo de la capa de caché aumenta el número de vistas de página por hora.

- **API de GraphQL**
   - 250 hilos simultáneos
   - Establezca en Tasa de aciertos de caché de CDN al 0%

      Los tiempos de respuesta mejoran significativamente con una capa de almacenamiento en caché delante de GraphQL.

- **Web del administrador**
   - 500 usuarios simultáneos
   - Establezca en Tasa de aciertos de caché de CDN al 0%

## Especificaciones del entorno de prueba

La prueba de carga se completó con los perfiles de carga de JMeter ejecutados en la instancia de Adobe Commerce. Durante la prueba se utilizaron tres nodos web y tres nodos de servicio. La siguiente imagen detalla el punto de entrada de la infraestructura de JMeter y Producción.

![Referencia de rendimiento JMeter e infraestructura de producción](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### Aplicación

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> implementado en la infraestructura en la nube con arquitectura Pro.

### Infraestructura

Para el análisis de rendimiento, Adobe Commerce 2.4.5 se implementó en un [infraestructura ampliable](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) con la siguiente capacidad.

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
