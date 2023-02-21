---
title: Arquitectura de referencia
description: Revise los diagramas de la arquitectura de referencia recomendada para implementaciones de Adobe Commerce y Magento Open Source.
source-git-commit: 065c56f20ba5b1eef8c331c5c2f5649902f1442b
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---


# Arquitectura de referencia

En este tema se describe una configuración genérica recomendada para instancias de Adobe Commerce y Magento Open Source que utilizan servidores simples alojados físicamente en un centro de datos (no virtualizados) en el que los recursos no se comparten con otros usuarios. Su proveedor de alojamiento, especialmente si se especializa en hosting de alto rendimiento de Commerce, puede recomendar una configuración diferente que sea igual o más efectiva para sus necesidades.

Para Adobe Commerce en entornos de infraestructura en la nube, consulte [Arquitectura inicial](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] Diagrama de arquitectura de referencia

La variable [!DNL Commerce] El diagrama de arquitectura de referencia representa el método recomendado para configurar una variable escalable [!DNL Commerce] sitio.

El color de cada elemento del diagrama indica si el elemento forma parte de Magento Open Source o Adobe Commerce y si es necesario.

* Se requieren elementos naranja para el Magento Open Source
* Los elementos grises son opcionales para el Magento Open Source
* Los elementos azules son opcionales para Adobe Commerce

![Diagrama de arquitectura de referencia comercial](../assets/performance/images/ref-architecture-2.3.png)

En las secciones siguientes se proporcionan recomendaciones y consideraciones para cada sección del diagrama de Arquitectura de referencia del comercio.

### [!DNL Varnish]

* A [!DNL Varnish] el clúster puede escalar al tráfico de un sitio
* Ajuste el tamaño de la instancia en función del número de páginas de caché necesarias
* En un sitio de alto tráfico, utilice un [!DNL Varnish] Master para garantizar que el vaciado en caché de una solicitud (como máximo) por nivel web

### Web

* Habilitar la escala de nodos para el tráfico y la redundancia
* Un nodo es maestro y ejecuta cron
* También puede utilizar un nodo de administrador y de trabajo dedicado

### Caché

* Considere la posibilidad de implementar una instancia de Redis independiente para las sesiones
* Puede tener una instancia de Redis por caché
* Ajuste el tamaño de la instancia para que contenga el mayor tamaño de caché esperado

### Bases de datos y colas

* Los sitios de alto tráfico pueden ajustar el rendimiento de la base de datos con bases de datos esclavas y bases de datos divididas para pedidos/carros de compras (en Adobe Commerce)
* Considere utilizar una base de datos esclava para permitir una recuperación rápida y para backups de datos
* Los sitios de poco tráfico pueden almacenar imágenes en la base de datos

### Buscar {#search-heading}

* Ajustar el número de instancias en función del tráfico de búsqueda

### Almacenamiento

* Considere la posibilidad de utilizar GFS o GlusterFS para el almacenamiento de medios/pub
* También puede usar el almacenamiento de bases de datos para sitios de poco tráfico

### Recomendado [!DNL Varnish] arquitectura de referencia

Magento admite varios motores de almacenamiento en caché de página completa (File, Memcache, Redis, [!DNL Varnish]) de forma predeterminada, junto con una cobertura ampliada a través de extensiones. [!DNL Varnish] es el motor de caché de página completa recomendado.  [!DNL Commerce] admite muchos [!DNL Varnish] configuraciones.

Para los sitios que no requieren alta disponibilidad, recomendamos utilizar una [!DNL Varnish] configuración con terminación SSL de Nginx.

![Sencilla [!DNL Varnish] Configuración con terminación SSL](../assets/performance/images/single-varnish-with-ssl-termination.png)

Para los sitios que requieren alta disponibilidad, se recomienda utilizar un [!DNL Varnish] con un equilibrador de carga de terminación SSL.

![Dos niveles de alta disponibilidad [!DNL Varnish] configuración con equilibrador de carga con terminación SSL](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
