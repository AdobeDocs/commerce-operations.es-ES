---
title: Herramientas de plataforma
description: Elija las herramientas de plataforma recomendadas para su implementación de Adobe Commerce.
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
feature: Configuration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# Herramientas de Platform

No hay escasez de aspectos que deben ser bien pensados y rigurosamente probados para mantener un sitio de comercio electrónico funcionando sin interferencias. No solo debe identificar las soluciones adecuadas para abordar todos los aspectos del sitio, desde el almacenamiento y la programación de datos hasta el almacenamiento en caché y la seguridad, sino que también necesita el proceso adecuado para garantizar el envío de una plataforma que se ejecute sin problemas y que se pueda crear y optimizar de forma eficaz.

Esta sección ofrece no solo una visión de las herramientas, soluciones, procesos y metodologías que se han probado y perfeccionado en varias implementaciones de Adobe Commerce, sino también nuestras recomendaciones para qué soluciones se adaptan mejor a las necesidades y objetivos específicos de la empresa.

La siguiente tabla incluye soluciones que recomendamos y que pueden utilizarse en Adobe Commerce para impulsar el rendimiento en la plataforma:

| Finalidad | Herramienta |
|------------------------------------------|-------------------------|
| Base de datos | MySQL, MariaDB, Percona |
| Lenguaje de programación | PHP, JS, HTML, MENOS CSS |
| Entorno de desarrollo integrado (IDE) | Eclipse, PHPStorm |
| Servidor web | Nginx, Apache |
| Servicios de almacenamiento en caché | Redis, Barniz |
| Servicios de búsqueda | Elasticsearch |
| Servicios de cola de mensajes | [!DNL RabbitMQ] |
| Herramienta de exploración de seguridad | SonarQube, ZAP |

## Base de datos

Existen tres herramientas diferentes que utilizamos en función de las necesidades de la marca. MySQL es una buena solución de línea base como base de datos de Adobe Commerce si no espera que su tienda gestione cargas extremas.

MariaDB se centra más en la comunidad y funciona mejor para los usuarios que se preocupan más por las características que por el rendimiento puro. MariaDB admite una gran variedad de motores de base de datos, cifrado de disco, interconectividad horizontal compleja y características de escalado, que podrían ser interesantes para grandes tiendas Adobe Commerce.

Percona es una ramificación de MySQL que se centra en el rendimiento y la gestión de la carga máxima. Elija MariaDB si necesita más calidad de vida y características de DevOps. Elija Percona si su objetivo es obtener un rendimiento de alta carga en conjuntos de datos a gran escala.

## Lenguaje de programación

Adobe Commerce es una aplicación basada en PHP y las versiones más recientes siempre son compatibles con la última versión estable de PHP (por ejemplo, la versión 2.4 de Adobe Commerce recomienda usar PHP 7.4). Para obtener más seguridad y rendimiento, existen varios factores a tener en cuenta al configurar PHP para obtener la máxima velocidad y eficiencia en el procesamiento de solicitudes. La tienda web de Adobe Commerce está diseñada con HTML, JavaScript y el preprocesador LESS CSS.

## Servidores web

Adobe Commerce es totalmente compatible con los servidores web Nginx y Apache. Adobe Commerce proporciona archivos de configuración recomendados de ejemplo para ambos:

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

La muestra Nginx contiene ajustes para un mejor rendimiento y está diseñada para que se requiera poca reconfiguración.

## Servicios de almacenamiento en caché

Adobe Commerce proporciona numerosas opciones para almacenar la caché y los datos de sesión, incluidos Redis, Memcache, el sistema de archivos y la base de datos. Para una configuración con varios nodos web, Redis es la mejor opción.

Recomendamos encarecidamente usar Varnish como servidor de caché de página completa para su tienda. Adobe Commerce distribuye un archivo de configuración de ejemplo para Barniz que contiene todos los ajustes recomendados para el rendimiento.

## Servicios de búsqueda

En la versión 2.4 y posteriores de Adobe Commerce, todas las instalaciones deben configurarse para utilizar Elasticsearch o OpenSearch como solución de búsqueda en el catálogo. Elasticsearch realiza búsquedas rápidas y avanzadas en los productos del catálogo. Elasticsearch es opcional en las versiones anteriores a la 2.4, pero se recomienda.

## Servicios de cola de mensajes

Las colas de mensajes proporcionan un mecanismo de comunicación asincrónico en el que el remitente y el receptor de un mensaje no se ponen en contacto. [!DNL RabbitMQ] es un agente de mensajería de código abierto que ofrece un sistema de mensajería fiable, de alta disponibilidad, escalable y portátil.

## Herramientas de seguridad

El [Herramienta de análisis de seguridad de Adobe Commerce](https://docs.magento.com/user-guide/magento/security-scan.html) le permite supervisar regularmente los sitios web de su tienda y recibir actualizaciones para detectar riesgos de seguridad conocidos, malware y software obsoleto. Normalmente, empezará a utilizar esta herramienta cuando comience la prueba de aceptación del usuario (UAT). Además de la herramienta de análisis de seguridad de Adobe Commerce, que es gratuita y está disponible para todas las implementaciones y versiones de Adobe Commerce, hay otras opciones que se pueden utilizar durante el proceso de CI/CD y antes de cada versión.

SonarQube es una plataforma de gestión de calidad de código abierto, diseñada para analizar y medir la calidad técnica de su código. SonarQube no solo proporciona un informe completo de errores de código, errores de sintaxis y vulnerabilidades, sino que también ofrece sugerencias y ejemplos para corregir su código. SonarQube es perfecto para usarlo en un entorno de CI/CD como herramienta capaz de analizar el código antes de implementarlo.

Zed Attack Proxy (ZAP) es una herramienta gratuita de pruebas de seguridad utilizada por miles de probadores de pluma en todo el mundo. ZAP es desarrollado por OWASP y es una de las herramientas preferidas para las pruebas de seguridad manuales.
