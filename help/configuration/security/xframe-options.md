---
title: Encabezado X-Frame-Options
description: Utilice X-Frame-Options para controlar el procesamiento de las páginas.
source-git-commit: db696b8ca501d128db655c5ebb161c654c6378a7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Encabezado X-Frame-Options

Para ayudar a evitar [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) se ha agregado una opción para usar la variable [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) Encabezado de solicitud HTTP en solicitudes a su tienda.

La variable `X-Frame-Options` header le permite especificar si se debe permitir a un explorador procesar una página en un `<frame>`, `<iframe>`o `<object>` de la siguiente manera:

- `DENY`: La página no se puede mostrar en un marco.
- `SAMEORIGIN`: (predeterminado) La página solo se puede mostrar en un marco del mismo origen que la propia página.

>[!WARNING]
>
>La variable `ALLOW-FROM <uri>` se ha desaprobado porque los navegadores compatibles con Commerce ya no la admiten. Consulte [Compatibilidad del explorador](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Por motivos de seguridad, Adobe recomienda encarecidamente que no se ejecute la tienda Commerce en un marco.

## Implementación `X-Frame-Options`

Definir un valor para `X-Frame-Options` en `<project-root>/app/etc/env.php`. El valor predeterminado se establece de la siguiente manera:

```php
'x-frame-options' => 'SAMEORIGIN',
```

Reimplementar para cualquier cambio en la `env.php` para que surta efecto.

>[!TIP]
>
>Es más seguro editar la variable `env.php` que debe establecer un valor en el Administrador.

## Compruebe la configuración de `X-Frame-Options`

Para comprobar la configuración, vea los encabezados HTTP en cualquier página de tienda. Existen varias formas de hacerlo, incluido el uso de un inspector del explorador web.

El siguiente ejemplo utiliza curl, que puede ejecutar desde cualquier equipo que pueda conectarse al servidor de Commerce a través del protocolo HTTP.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Busque la variable `X-Frame-Options` en los encabezados.
