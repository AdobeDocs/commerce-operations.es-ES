---
title: Tecnologías de infraestructura de nube
description: Obtenga una vista más detallada de la recopilación de tecnología que utilizamos para Adobe Commerce en la infraestructura de la nube.
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Tecnologías

Como hemos mencionado, Adobe Commerce aprovecha varias soluciones de software para admitir la plataforma. Específicamente, en lo que se refiere a la producción, hemos desglosado algunas de las soluciones y características técnicas incluidas en Adobe Commerce en la infraestructura de la nube que ayudan a aprovechar al máximo su entorno de producción.

![Diagrama de la tecnología de infraestructura en la nube de Adobe Commerce](../../../assets/playbooks/infrastructure-technology.svg)

## Soluciones de software

- **Nginx**—Servidor web que utiliza PHP-FPM. Hay una instancia con varios trabajadores.

- **GlusterFS**—Servidor de archivos para administrar todas las implementaciones de archivos estáticos y la sincronización con cuatro montajes de directorios:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis**: un servidor por VM con solo uno activo y los otros dos como réplicas.

- **Elasticsearch**: busque Adobe Commerce versión 2.2.x y posteriores.

- **Galera**: cluster de base de datos con una base de datos MySQL MariaDB por nodo con una configuración de incremento automático de tres para ID únicos en cada base de datos.

## Características y ventajas

- Con tres instancias dedicadas en un VPC, hay un equilibrador de carga elástico en tres zonas de disponibilidad o centros de datos independientes.

- Se proporciona una mayor resiliencia frente a eventos que pueden provocar que una sola instancia falle. Por ejemplo, una interrupción de toda una zona de disponibilidad de AWS o de un centro de datos.

- Sin escalamiento de tiempo de inactividad en toda la pila, incluida la web, el almacenamiento en caché, la búsqueda y la base de datos, en menos de 15 minutos.
