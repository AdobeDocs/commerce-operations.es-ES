---
title: Encabezado X-Frame-Options
description: Utilice X-Frame-Options para controlar el procesamiento de las páginas.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Encabezado X-Frame-Options

Para ayudar a evitar [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) se ha agregado una opción para usar la variable [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) Encabezado de solicitud HTTP en solicitudes a su tienda.

La variable `X-Frame-Options` el encabezado le permite especificar si se debe permitir o no que un explorador renderice una página en un `<frame>`, `<iframe>`o `<object>` de la siguiente manera:

- `DENY`: La página no se puede mostrar en un marco.
- `SAMEORIGIN`: (predeterminado) La página solo se puede mostrar en un marco del mismo origen que la propia página.

>[!WARNING]
>
>La variable `ALLOW-FROM <uri>` se ha desaprobado porque los navegadores compatibles con Commerce ya no la admiten. Consulte [Compatibilidad del explorador](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Por motivos de seguridad, Adobe recomienda encarecidamente que no se ejecute la tienda Commerce en un marco.

## Implementación `X-Frame-Options`

Definir un valor para `X-Frame-Options` en `<magento_root>/app/etc/env.php`. A continuación se muestra el valor predeterminado:

```php
'x-frame-options' => 'SAMEORIGIN',
```

>[!TIP]
>
>Es más seguro editar la variable `env.php` que debe establecer un valor en el Administrador.

## Compruebe la configuración de `X-Frame-Options`

Para comprobar la configuración, vea los encabezados HTTP en cualquier página de tienda. Existen varias formas de hacerlo, incluido el uso de un inspector del explorador web.

El siguiente ejemplo utiliza curl, que puede ejecutar desde cualquier equipo que pueda conectarse al servidor de Commerce a través del protocolo HTTP.

Utilice el siguiente comando:

```bash
curl -I -v --location-trusted '<your storefront URL>'
```

Busque la variable `X-Frame-Options` en los encabezados.
