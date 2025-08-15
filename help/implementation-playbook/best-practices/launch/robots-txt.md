---
title: Prácticas recomendadas para configurar rastreadores web
description: Aprenda a pasar instrucciones sobre el sitio de Adobe Commerce a rastreadores web mediante archivos robots.txt y sitemap.xml.
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# Prácticas recomendadas para configurar rastreadores web

Este artículo proporciona prácticas recomendadas para usar archivos de `robots.txt` y `sitemap.xml` en Adobe Commerce, incluida la configuración y la seguridad. Estos archivos indican a los rastreadores web (generalmente robots de motores de búsqueda) cómo rastrear páginas en un sitio web. La configuración de estos archivos puede mejorar el rendimiento del sitio y la optimización de los motores de búsqueda.

>[!NOTE]
>
>Estas prácticas recomendadas se aplican únicamente a los proyectos que utilizan la tienda nativa de Adobe Commerce. No se aplican a proyectos de Adobe Commerce que utilizan otras soluciones de tienda (por ejemplo, Adobe Experience Manager, sin encabezado).

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Adobe Commerce en la infraestructura en la nube

Un proyecto de Adobe Commerce predeterminado contiene una jerarquía que incluye un solo sitio web, tienda y vista de tienda. Para implementaciones más complejas, puedes crear sitios web, tiendas y vistas de tiendas adicionales para una tienda de _varios sitios_.

### Tiendas de un solo sitio

Siga estas prácticas recomendadas al configurar los archivos de `robots.txt` y `sitemap.xml` para tiendas de un solo sitio:

- Asegúrese de que el proyecto esté usando [`ece-tools`](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) versión 2002.0.12 o posterior.
- Utilice la aplicación Admin para agregar contenido al archivo `robots.txt`.

  >[!TIP]
  >
  >Vea el archivo `robots.txt` generado automáticamente para su tienda en `<domain.your.project>/robots.txt`.

- Use la aplicación Admin para generar un archivo de `sitemap.xml`.

  >[!IMPORTANT]
  >
  >Debido al sistema de archivos de solo lectura de Adobe Commerce en los proyectos de infraestructura en la nube, debe especificar la ruta de acceso `pub/media` antes de generar el archivo.

- Utilice un fragmento personalizado de VCL de Fastly para redirigir desde la raíz del sitio a la ubicación `pub/media/` para ambos archivos:

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
>Consulte [Agregar robots de mapa del sitio y de motor de búsqueda](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) para obtener instrucciones detalladas.


### Tiendas de varios sitios

Puede configurar y ejecutar varias tiendas con una sola implementación de Adobe Commerce en la infraestructura en la nube. Ver [Configurar varios sitios web o tiendas](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites).

Las mismas prácticas recomendadas para configurar los archivos de `robots.txt` y `sitemap.xml` para [tiendas de un solo sitio](#single-site-storefronts) se aplican a tiendas de varios sitios con dos diferencias importantes:

- Asegúrese de que los nombres de archivo `robots.txt` y `sitemap.xml` contengan los nombres de los sitios correspondientes. Por ejemplo:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Utilice un fragmento de VCL personalizado ligeramente modificado para redirigir desde la raíz de sus sitios a la ubicación `pub/media` para ambos archivos en los sitios:

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

Use la aplicación Admin para configurar los archivos de `robots.txt` y `sitemap.xml` a fin de evitar que los bots analicen e indexen contenido innecesario (consulte [Robots de motores de búsqueda](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>En implementaciones locales, la forma de escribir los archivos depende de cómo haya instalado Adobe Commerce. Escriba los archivos en `/path/to/commerce/pub/media/` o `/path/to/commerce/media`, lo que sea adecuado para la instalación.

## Seguridad

No exponga la ruta de acceso de administrador en el archivo `robots.txt`. Exponer la ruta del administrador es una vulnerabilidad para el pirateo del sitio y la posible pérdida de datos. Quitar la ruta de acceso de administración del archivo `robots.txt`.

Para ver los pasos para editar el archivo `robots.txt` y eliminar todas las entradas de la ruta de administración, consulte [Guía del usuario de marketing > SEO y búsqueda > Robots del motor de búsqueda](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Si necesita ayuda, [envíe un ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Más información

- [Explicación de sitios web, tiendas y vistas de tiendas](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [Agregando sitios web](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [Use Fastly para bloquear el tráfico malintencionado para sus sitios de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking)
- [robots.txt genera un error 404 en Adobe Commerce en la infraestructura en la nube 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
