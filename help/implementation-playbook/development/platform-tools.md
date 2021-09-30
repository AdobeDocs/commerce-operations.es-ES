---
title: Herramientas de plataforma
description: Elija las herramientas de plataforma recomendadas para la implementación de Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# Herramientas de plataforma

No hay escasez de aspectos que deben ser bien pensados y rigurosamente probados para mantener un sitio de comercio electrónico funcionando sin interferencias. No solo debe identificar las soluciones adecuadas para abordar todos los aspectos del sitio (desde el almacenamiento de datos y la programación hasta el almacenamiento en caché y la seguridad), sino que también necesita el proceso adecuado para garantizar la entrega de una plataforma que se ejecute sin problemas y que se pueda crear y optimizar de forma eficiente.

Esta sección no solo ofrece un vistazo a las herramientas, soluciones, procesos y metodologías que se han probado y perfeccionado en una serie de implementaciones de comercio de Adobe, sino también a las recomendaciones para las que las soluciones se ajustan mejor a las necesidades y objetivos específicos del negocio.

La siguiente tabla incluye soluciones que recomendamos y que se pueden usar en Adobe Commerce para impulsar el rendimiento en la plataforma:

| Objetivo | Herramienta |
|------------------------------------------|-------------------------|
| Base de datos | MySQL, MariaDB, Percona |
| Lenguaje de programación | PHP, JS, HTML, LESS CSS |
| Entorno de desarrollo integrado (IDE) | Eclipse, PHPStorm |
| Servidor web | Nginx, Apache |
| Servicios de almacenamiento en caché | Redis, Varniz |
| Servicios de búsqueda | Elasticsearch |
| Servicios de cola de mensajes | RabbitMQ |
| Herramienta de análisis de seguridad | SonarQube, ZAP |

## Base de datos

Hay tres herramientas diferentes que utilizamos dependiendo de las necesidades de la marca. MySQL es una buena solución de línea de base como la base de datos de comercio de Adobe si no espera que su tienda gestione cargas extremas.

MariaDB se centra más en la comunidad y funciona mejor para los usuarios que se preocupan más por las características que por el rendimiento puro. MariaDB es compatible con una gran variedad de motores de base de datos, cifrado de discos, interconectividad horizontal compleja y funciones de escalado, lo que podría ser interesante para grandes tiendas de comercio de Adobe.

Percona es una ramificación de MySQL que se centra en el rendimiento y la gestión de carga máxima. Elija MariaDB si necesita más calidad de vida y características de DevOps. Vaya a Percona si su objetivo es obtener un rendimiento de alta carga en conjuntos de datos a gran escala.

## Lenguaje de programación

Adobe Commerce es una aplicación basada en PHP y las versiones más recientes son siempre compatibles con la última versión estable de PHP (por ejemplo, Adobe Commerce versión 2.4 recomienda utilizar PHP 7.4). Para obtener más seguridad y rendimiento, hay varios factores a tener en cuenta al configurar PHP para obtener la máxima velocidad y eficiencia en el procesamiento de solicitudes. La tienda web de Adobe Commerce está creada con HTML, JavaScript y el preprocesador LESS CSS.

## Servidores web

Adobe Commerce es totalmente compatible con los servidores web Nginx y Apache. Adobe Commerce proporciona archivos de configuración recomendados de ejemplo para ambos:

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

El ejemplo de Nginx contiene ajustes para un mejor rendimiento y está diseñado para que se requiera poca reconfiguración.

## Servicios de almacenamiento en caché

Adobe Commerce ofrece numerosas opciones para almacenar su caché y sus datos de sesión, como Redis, Memcache, filesystem y base de datos. Para una configuración con varios nodos web, Redis es la mejor opción.

Recomendamos encarecidamente usar Varnish como servidor de caché de página completa para su tienda. Adobe Commerce distribuye un archivo de configuración de muestra para Varnish que contiene todos los ajustes recomendados para el rendimiento.

## Servicios de búsqueda

Para Adobe Commerce versión 2.4 y posterior, todas las instalaciones deben configurarse para utilizar Elasticsearch como solución de búsqueda de catálogo. Elasticsearch proporciona búsquedas rápidas y avanzadas de los productos del catálogo. Elasticsearch es opcional para versiones anteriores a la 2.4, pero se recomienda.

## Servicios de cola de mensajes

Las colas de mensajes proporcionan un mecanismo de comunicación asincrónico en el que el remitente y el receptor de un mensaje no se comunican entre sí. RabbitMQ es un intermediario de mensajes de código abierto que ofrece un sistema de mensajería fiable, altamente disponible, escalable y portátil.

## Herramientas de seguridad

La [herramienta de análisis de seguridad del comercio de Adobe](https://docs.magento.com/user-guide/magento/security-scan.html) le permite supervisar con regularidad sus sitios web de tienda y recibir actualizaciones para detectar riesgos de seguridad conocidos, malware y software obsoleto. Normalmente, se empieza a utilizar esta herramienta cuando se comienza a probar la aceptación del usuario (UAT). Además de la herramienta Adobe Commerce Security Scan, que es gratuita y está disponible para todas las implementaciones y versiones de Adobe Commerce, hay otras opciones que se pueden utilizar durante el proceso CI/CD y antes de cada versión.

SonarQube es una plataforma de gestión de calidad de código abierto diseñada para analizar y medir la calidad técnica de su código. SonarQube no solo proporciona un informe completo de errores de código, errores de sintaxis y vulnerabilidades, sino que también ofrece sugerencias y ejemplos para corregir el código. SonarQube es perfecta para su uso en un entorno CI/CD como herramienta capaz de analizar el código antes de su implementación.

Zed Attack Proxy (ZAP) es una herramienta gratuita de pruebas de seguridad que utilizan miles de probadores de bolígrafos de todo el mundo. ZAP es desarrollado por OWASPy es una de las herramientas más preferidas para las pruebas de seguridad manuales.
