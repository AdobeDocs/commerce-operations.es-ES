---
title: Evitar ataques de clickjacking
description: Evite las vulnerabilidades de secuestro de clics utilizando el encabezado "X-Frame-Options" para controlar las representaciones de páginas.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Evitar ataques de clickjacking

Impedir [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) exploits al incluir el [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) Encabezado de solicitud HTTP en solicitudes a su tienda.

El `X-Frame-Options` permite especificar si un explorador puede procesar una página en un `<frame>`, `<iframe>`, o `<object>` como sigue:

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
