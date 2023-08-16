---
title: Arquitectura de referencia
description: Revise los diagramas de la arquitectura de referencia recomendada para las implementaciones de Adobe Commerce y Magento Open Source.
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Arquitectura de referencia

En este tema se describe una configuración genérica recomendada para Adobe Commerce e instancias de Magento Open Source que utilizan servidores simples alojados físicamente en un centro de datos (no virtualizado) en el que los recursos no se comparten con otros usuarios. Su proveedor de alojamiento, especialmente si se especializa en alojamiento de alto rendimiento comercial, puede recomendarle una configuración diferente que sea igual o más eficaz para sus necesidades.

Para conocer Adobe Commerce sobre entornos de infraestructura en la nube, consulte [Arquitectura de inicio](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] Diagrama de arquitectura de referencia

El [!DNL Commerce] El diagrama de arquitectura de referencia representa el método de prácticas recomendadas para configurar un diseño escalable [!DNL Commerce] sitio.

El color de cada elemento del diagrama indica si el elemento forma parte de Magento Open Source o Adobe Commerce y si es necesario.

* Se requieren elementos naranjas para el Magento Open Source
* Los elementos grises son opcionales para Magento Open Source
* Los elementos azules son opcionales para Adobe Commerce

![Diagrama de arquitectura de referencia comercial](../assets/performance/images/ref-architecture-2.3.png)

Las secciones siguientes proporcionan recomendaciones y consideraciones para cada sección del diagrama de arquitectura de referencia comercial.

### [!DNL Varnish]

* A [!DNL Varnish] clúster puede escalarse al tráfico de un sitio
* Ajuste el tamaño de la instancia en función del número de páginas de caché necesarias
* En un sitio con mucho tráfico, utilice un [!DNL Varnish] Principal para garantizar el vaciado en caché de una solicitud (como máximo) por nivel web

### Web

* Habilitar la escala de nodos para el tráfico y la redundancia
* Un nodo es principal y ejecuta cron
* También puede utilizar un administrador dedicado y nodos de trabajo

### Caché

* Considere implementar una instancia de Redis independiente para las sesiones
* Puede tener una instancia de Redis por caché
* Cambie el tamaño de la instancia para que contenga el tamaño de caché esperado más grande

### Base de datos y colas

* Los sitios de alto tráfico pueden ajustar el rendimiento de la base de datos con bases de datos esclavas y bases de datos divididas para pedidos/carros (en Adobe Commerce)
* Considere utilizar una base de datos esclava para permitir una recuperación rápida y realizar copias de seguridad de los datos
* Los sitios de poco tráfico pueden almacenar imágenes en la base de datos

### Buscar {#search-heading}

* Ajuste el número de instancias en función del tráfico de búsqueda

### Almacenamiento

* Considere utilizar GFS o GlusterFS para el almacenamiento de medios/pubs
* Como alternativa, utilice el almacenamiento de BD para sitios de poco tráfico

### Recomendado [!DNL Varnish] arquitectura de referencia

Magento admite varios motores de almacenamiento en caché de página completa (File, Memcache, Redis, [!DNL Varnish]) de forma predeterminada, junto con una cobertura ampliada mediante extensiones. [!DNL Varnish] es el motor de caché de página completa recomendado.  [!DNL Commerce] admite muchas variables diferentes [!DNL Varnish] configuraciones.

Para los sitios que no requieren alta disponibilidad, recomendamos utilizar un [!DNL Varnish] configuración con terminación SSL Nginx.

![Sencilla [!DNL Varnish] Configuración con terminación SSL](../assets/performance/images/single-varnish-with-ssl-termination.png)

Para los sitios que requieren alta disponibilidad, recomendamos utilizar un nivel 2 [!DNL Varnish] con un equilibrador de carga con terminación SSL.

![Alta disponibilidad de dos niveles [!DNL Varnish] configuración con equilibrador de carga de terminación SSL](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
