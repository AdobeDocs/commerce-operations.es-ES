---
title: Tecnologías de infraestructura en nube
description: Eche un vistazo más de cerca a la colección de tecnología que utilizamos para Adobe Commerce en la infraestructura en la nube.
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Tecnologías

Como hemos mencionado, Adobe Commerce aprovecha una serie de soluciones de software para admitir la plataforma. En concreto, en lo que respecta a la producción, hemos desglosado algunas de las soluciones y funciones técnicas incluidas en Adobe Commerce en infraestructuras en la nube que ayudan a sacar el máximo partido a su entorno de producción.

![Diagrama que muestra Adobe Commerce sobre la tecnología de la infraestructura en la nube](../../../assets/playbooks/infrastructure-technology.svg)

## Soluciones de software

- **Nginx**: servidor web que utiliza PHP-FPM. Hay una instancia con varios trabajadores.

- **GlusterFS**: servidor de ficheros para gestionar todas las implementaciones y sincronización de ficheros estáticos con cuatro montajes de directorios:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis**: un servidor por VM con un solo servidor activo y los otros dos como réplicas.

- **Elasticsearch**: permite buscar Adobe Commerce versión 2.2.x y posterior.

- **OpenSearch**: permite buscar Adobe Commerce versión 2.4.6 y posterior.

- **Galera**: cluster de base de datos con una base de datos MariaDB MySQL por nodo con una configuración de incremento automático de tres para ID únicos en cada base de datos.

## Características y ventajas

- Con tres instancias dedicadas en un VPC, hay un equilibrador de carga elástico en tres zonas de disponibilidad o centros de datos separados.

- Se proporciona una mayor resistencia frente a eventos que pueden provocar el fallo de una sola instancia. Por ejemplo, una interrupción de toda una zona de disponibilidad de AWS o de un centro de datos.

- Escalado sin tiempo de inactividad en toda la pila, incluida la web, el almacenamiento en caché, la búsqueda y la base de datos, en menos de 15 minutos.
