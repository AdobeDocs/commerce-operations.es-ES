---
title: Prácticas recomendadas para configurar los archivos robots.txt y sitemap.xml
description: Aprenda a pasar instrucciones sobre el sitio de Adobe Commerce a rastreadores web.
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Prácticas recomendadas para configurar `robots.txt` y `sitemap.xml` archivos

Este artículo contiene prácticas recomendadas para usar `robots.txt` y `sitemap.xml` archivos en Adobe Commerce, incluida la configuración y la seguridad. Estos archivos indican a los robots web (generalmente robots de motores de búsqueda) cómo rastrear páginas en un sitio web. La configuración de estos archivos puede mejorar el rendimiento del sitio y la optimización de los motores de búsqueda.

>[!NOTE]
>
>Estas prácticas recomendadas se aplican únicamente a los proyectos que utilizan la tienda nativa de Adobe Commerce. No se aplican a proyectos de Adobe Commerce que utilizan otras soluciones de tienda (por ejemplo, Adobe Experience Manager, sin encabezado).

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Adobe Commerce en la infraestructura en la nube

Un proyecto de Adobe Commerce predeterminado contiene una jerarquía que incluye un solo sitio web, tienda y vista de tienda. Para implementaciones más complejas, puede crear sitios web, tiendas y vistas de tiendas adicionales para un _de varios sitios_ tienda.

### Tiendas de un solo sitio

Siga estas prácticas recomendadas al configurar el `robots.txt` y `sitemap.xml` archivos para tiendas de un solo sitio:

- Asegúrese de que el proyecto esté utilizando [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) versión 2002.0.12 o posterior.
- Utilice la aplicación de administración para añadir contenido a `robots.txt` archivo.

   >[!TIP]
   >
   >Ver el archivo generado automáticamente `robots.txt` archivo para su tienda en `<domain.your.project>/robots.txt`.

- Utilice la aplicación de administración para generar un `sitemap.xml` archivo.

   >[!IMPORTANT]
   >
   >Debido al sistema de archivos de solo lectura de Adobe Commerce en los proyectos de infraestructura en la nube, debe especificar la variable `pub/media` ruta antes de generar el archivo.

- Utilice un fragmento personalizado de VCL de Fastly para redirigir desde la raíz del sitio a `pub/media/` ubicación de ambos archivos:

   ```vcl
   {
     "name": "sitemaprobots_rewrite",
     "dynamic": "0",
     "type": "recv",
     "priority": "90",
     "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
   }
   ```

- Pruebe el redireccionamiento viendo los archivos en un explorador web. Por ejemplo, `<domain.your.project>/robots.txt` y `<domain.your.project>/sitemap.xml`. Asegúrese de utilizar la ruta raíz para la que configuró el redireccionamiento y no una ruta diferente.

>[!INFO]
>
>Consulte [Añadir robots de mapa del sitio y de motor de búsqueda](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) para obtener instrucciones detalladas.


### Tiendas de varios sitios

Puede configurar y ejecutar varias tiendas con una sola implementación de Adobe Commerce en la infraestructura en la nube. Consulte [Configurar varios sitios web o tiendas](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

Las mismas prácticas recomendadas para configurar el `robots.txt` y `sitemap.xml` archivos para [tiendas de un solo sitio](#single-site-storefronts) se aplica a tiendas de varios sitios con dos diferencias importantes:

- Asegúrese de que la variable `robots.txt` y `sitemap.xml` los nombres de archivo contienen los nombres de los sitios correspondientes. Por ejemplo:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Utilice un fragmento de VCL personalizado ligeramente modificado de Fastly para redirigir desde la raíz de sus sitios al `pub/media` ubicación de ambos archivos en los sitios:

   ```vcl
   {
     "name": "sitemaprobots_rewrite",
     "dynamic": "0",
     "type": "recv",
     "priority": "90",
     "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
   }
   ```

## Adobe Commerce local

Utilice la aplicación Admin para configurar `robots.txt` y `sitemap.xml` para evitar que los bots analicen e indexen contenido innecesario (consulte [Robots del motor de búsqueda](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>En implementaciones locales, la forma de escribir los archivos depende de cómo haya instalado Adobe Commerce. Escribir los archivos en `/path/to/commerce/pub/media/` o `/path/to/commerce/media`, el que sea adecuado para la instalación.

## Seguridad

No exponga la ruta de administración en su `robots.txt` archivo. Exponer la ruta del administrador es una vulnerabilidad para el pirateo del sitio y la posible pérdida de datos. Elimine la ruta de administración de `robots.txt` archivo.

Para ver los pasos para editar la variable `robots.txt` y elimine todas las entradas de la ruta de administración, consulte [Guía del usuario de marketing > SEO y búsqueda > Robots de motores de búsqueda](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Si necesita ayuda, [enviar un ticket de asistencia de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Información adicional

- [Explicación de sitios web, tiendas y vistas de tiendas](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Adición de sitios web](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Use Fastly para bloquear el tráfico malicioso para sus sitios de Adobe Commerce](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt genera un error 404 en Adobe Commerce en la infraestructura en la nube 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
