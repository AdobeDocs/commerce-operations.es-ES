---
title: Encabezado X-Frame-Options
description: Utilice X-Frame-Options para controlar las representaciones de páginas.
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Encabezado X-Frame-Options

Para ayudar a prevenir [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) exploits, hemos añadido una opción para utilizar el [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) Encabezado de solicitud HTTP en solicitudes a su tienda.

El `X-Frame-Options` permite especificar si se debe permitir a un explorador procesar una página en un `<frame>`, `<iframe>`, o `<object>` como sigue:

- `DENY`: la página no se puede mostrar en un marco.
- `SAMEORIGIN`: (predeterminado) La página solo se puede mostrar en un marco del mismo origen que la propia página.

>[!WARNING]
>
>El `ALLOW-FROM <uri>` Esta opción ha quedado obsoleta porque los exploradores compatibles con Commerce ya no la admiten. Consulte [Compatibilidad del explorador](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Por motivos de seguridad, Adobe recomienda encarecidamente no ejecutar la tienda de Commerce en un marco.

## Implementación `X-Frame-Options`

Establecer un valor para `X-Frame-Options` in `<project-root>/app/etc/env.php`. El valor predeterminado se establece de la siguiente manera:

```php
'x-frame-options' => 'SAMEORIGIN',
```

Volver a implementar para cualquier cambio en `env.php` para que surta efecto.

>[!TIP]
>
>Es más seguro editar el `env.php` de lo que es para establecer un valor en Admin.

## Compruebe la configuración de `X-Frame-Options`

Para comprobar la configuración, vea los encabezados HTTP en cualquier página de la tienda. Existen varias formas de hacerlo, incluido el uso de un inspector del explorador web.

El siguiente ejemplo utiliza curl, que puede ejecutar desde cualquier equipo que pueda conectarse al servidor de Commerce a través del protocolo HTTP.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Busque la variable `X-Frame-Options` en los encabezados.
