---
title: Arquitectura de referencia
description: Revise los diagramas de la arquitectura de referencia recomendada para las implementaciones de Adobe Commerce.
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Arquitectura de referencia

En este tema se describe una configuración recomendada genérica para instancias de Adobe Commerce que utilizan servidores simples alojados físicamente en un centro de datos (no virtualizado) en el que los recursos no se comparten con otros usuarios. Su proveedor de alojamiento, especialmente si se especializa en alojamiento de alto rendimiento de Commerce, puede recomendarle una configuración diferente que sea igual o más eficaz para sus necesidades.

Para Adobe Commerce sobre entornos de infraestructura en la nube, consulte [Arquitectura de inicio](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture).

## [!DNL Commerce] Diagrama de arquitectura de referencia

El diagrama de arquitectura de referencia [!DNL Commerce] representa la práctica recomendada para configurar un sitio [!DNL Commerce] escalable.

El color de cada elemento del diagrama indica si el elemento forma parte de Magento Open Source o Adobe Commerce y si es necesario.

* Se requieren elementos naranjas para Magento Open Source
* Los elementos grises son opcionales para Magento Open Source
* Los elementos azules son opcionales para Adobe Commerce

![diagrama de arquitectura de referencia de Commerce](../assets/performance/images/ref-architecture-2.3.png)

En las siguientes secciones se proporcionan recomendaciones y consideraciones para cada sección del diagrama de arquitectura de referencia de Commerce.

### [!DNL Varnish]

* Un clúster [!DNL Varnish] se puede escalar al tráfico de un sitio
* Ajuste el tamaño de la instancia en función del número de páginas de caché necesarias
* En un sitio con mucho tráfico, use un sitio principal de [!DNL Varnish] para asegurarse de que se vacía en la caché una solicitud (como máximo) por nivel web

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

### Arquitectura de referencia [!DNL Varnish] recomendada

Magento admite varios motores de almacenamiento en caché de páginas completas (File, Memcache, Redis, [!DNL Varnish]) de forma predeterminada, así como una cobertura ampliada mediante extensiones. [!DNL Varnish] es el motor de caché de página completa recomendado.  [!DNL Commerce] admite muchas configuraciones de [!DNL Varnish] diferentes.

Para los sitios que no requieren alta disponibilidad, se recomienda usar una configuración simple de [!DNL Varnish] con terminación SSL Nginx.

![Configuración simple de [!DNL Varnish] con terminación SSL](../assets/performance/images/single-varnish-with-ssl-termination.png)

Para los sitios que requieren alta disponibilidad, se recomienda utilizar una configuración de [!DNL Varnish] de 2 niveles con un equilibrador de carga con terminación SSL.

![Configuración de alta disponibilidad de dos niveles [!DNL Varnish] con equilibrador de carga con terminación SSL](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
