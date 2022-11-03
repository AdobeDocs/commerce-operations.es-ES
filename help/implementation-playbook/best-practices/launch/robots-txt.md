---
title: Prácticas recomendadas para configurar archivos "robots.txt" y "sitemap.xml"
description: Aprenda a pasar instrucciones sobre su sitio de Adobe Commerce a rastreadores web.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---


# Prácticas recomendadas para la configuración `robots.txt` y `sitemap.xml` files

Este artículo proporciona prácticas recomendadas para usar `robots.txt` y `sitemap.xml` en Adobe Commerce, incluida la configuración y seguridad. Estos archivos indican a los robots web (normalmente robots de motores de búsqueda) cómo rastrear las páginas en un sitio web. La configuración de estos archivos puede mejorar el rendimiento del sitio y la optimización de los motores de búsqueda.

>[!NOTE]
>
>Estas prácticas recomendadas se aplican a proyectos que solo utilizan la tienda nativa de Adobe Commerce. No se aplican a proyectos de Adobe Commerce que utilizan otras soluciones de tienda (por ejemplo, Adobe Experience Manager, sin encabezado).

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Adobe Commerce en infraestructura en la nube

Un proyecto predeterminado de Adobe Commerce contiene una jerarquía que incluye un solo sitio web, tienda y vista de tienda. Para implementaciones más complejas, puede crear sitios web, tiendas y vistas de tienda adicionales para un _multisitio_ tienda.

### Tiendas de un solo sitio

Siga estas prácticas recomendadas al configurar la variable `robots.txt` y `sitemap.xml` archivos para tiendas de un solo sitio:

- Asegúrese de que el proyecto esté utilizando [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) versión 2002.0.12 o posterior.
- Utilice la aplicación de administración para añadir contenido al `robots.txt` archivo.

   >[!TIP]
   >
   >Ver el `robots.txt` para su tienda en `<domain.your.project>/robots.txt`.

- Utilice la aplicación de administración para generar un `sitemap.xml` archivo.

   >[!IMPORTANT]
   >
   >Debido al sistema de archivos de solo lectura de Adobe Commerce en proyectos de infraestructura en la nube, debe especificar la variable `pub/media` antes de generar el archivo.

- Utilice un fragmento personalizado de Fy VCL para redirigir desde la raíz del sitio al `pub/media/` ubicación para ambos archivos:

   ```vcl
   {
     "name": "sitemaprobots_rewrite",
     "dynamic": "0",
     "type": "recv",
     "priority": "90",
     "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
   }
   ```

- Pruebe la redirección consultando los archivos en un explorador web. Por ejemplo, `<domain.your.project>/robots.txt` y `<domain.your.project>/sitemap.xml`. Asegúrese de que está utilizando la ruta raíz para la que configuró la redirección y no una ruta diferente.

>[!INFO]
>
>Consulte [Agregar robots de mapa del sitio y de motor de búsqueda](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) para obtener instrucciones detalladas.


### Tiendas de varios sitios

Puede configurar y ejecutar varias tiendas con una sola implementación de Adobe Commerce en la infraestructura de la nube. Consulte [Configuración de varios sitios web o tiendas](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

Las mismas prácticas recomendadas para configurar la variable `robots.txt` y `sitemap.xml` archivos para [tiendas de un solo sitio](#single-site-storefronts) se aplica a tiendas de varios sitios con dos diferencias importantes:

- Asegúrese de que la variable `robots.txt` y `sitemap.xml` los nombres de archivo contienen los nombres de los sitios correspondientes. Por ejemplo:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Utilice un fragmento personalizado de Fy VCL ligeramente modificado para redirigir desde la raíz de sus sitios a la variable `pub/media` ubicación de ambos archivos en los sitios:

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

Utilice la aplicación de administración para configurar la variable `robots.txt` y `sitemap.xml` archivos para evitar que los bots analicen e indiquen contenido innecesario (consulte [Robots en motores de búsqueda](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>Para implementaciones locales, el lugar donde se escriben los archivos depende de cómo se haya instalado Adobe Commerce. Escriba los archivos en `/path/to/commerce/pub/media/` o `/path/to/commerce/media`, lo que sea adecuado para su instalación.

## Seguridad

No exponga la ruta de administración en su `robots.txt` archivo. La exposición de la ruta de administración es una vulnerabilidad para el hackeo del sitio y una posible pérdida de datos. Elimine la ruta de administración de la variable `robots.txt` archivo.

Para ver los pasos para editar la variable `robots.txt` y elimine todas las entradas de la ruta de administración, consulte [Guía del usuario de marketing > SEO y Search > Robots en los motores de búsqueda](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Si necesita ayuda, [enviar un ticket de asistencia de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.md#submit-ticket).

## Información adicional

- [Información sobre sitios web, tiendas y vistas de tiendas](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Adición de sitios web](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Use Finfinito para bloquear el tráfico malintencionado de sus sitios de Adobe Commerce](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt proporciona un error 404 en Adobe Commerce en la infraestructura de nube 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.md)
