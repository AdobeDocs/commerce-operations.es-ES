---
title: Configuración de la tienda
description: Siga estos pasos para configurar la tienda de Adobe Commerce o Magento Open Source.
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# Configuración de la tienda

Antes de ejecutar este comando, debe hacer lo siguiente *o* debe [instalar la aplicación](../advanced.md):

* [Crear o actualizar la configuración de implementación](deployment.md)
* [Crear el esquema de la base de datos](database.md)

## Instalación segura

{{$include /help/_includes/secure-install.md}}

## Configuración de la tienda

Uso de comandos:

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

Donde la tabla siguiente define parámetros y valores:

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--base-url` | Dirección URL básica que se utilizará para acceder a su administrador y tienda en cualquiera de los formatos siguientes:<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**Nota:** El régimen (`http://` o `https://`) y una barra diagonal son obligatorios. `<your install dir>` es la ruta relativa a docroot en la que se instala la aplicación. Según la configuración del servidor web y los hosts virtuales, la ruta puede ser magento2 o estar en blanco.<br><br>Para acceder a la aplicación en localhost, puede utilizar `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` que representa una URL base definida por una configuración de host virtual o por un entorno de virtualización como Docker. Por ejemplo, si configura un host virtual con el nombre de host commerce.example.com, puede instalar la aplicación con `--base-url={{base_url}}` y acceda al administrador con una URL como `http://commerce.example.com/admin`. | No |
| `--language` | Código de idioma para usar en Admin y tienda.<br><br>(Si aún no lo ha hecho, puede ver la lista de códigos de idioma introduciendo `magento info:language:list` de la variable `bin` ). | No |
| `--currency` | Moneda predeterminada para usar en la tienda. <br><br>(Si aún no lo ha hecho, puede ver la lista de monedas introduciendo `magento info:currency:list` de la variable `bin` ). | No |
| `--timezone` | Zona horaria predeterminada para usar en Admin y tienda. (Si aún no lo ha hecho, puede ver la lista de zonas horarias introduciendo `magento info:timezone:list` de la variable `bin` ). | No |
| `--use-rewrites` | `1` significa que utiliza las reescrituras del servidor web para los vínculos generados en la tienda y en el administrador.<br><br>`0` deshabilita el uso de las reescrituras del servidor web. Este es el valor predeterminado. | No |
| `--use-secure` | `1` habilita el uso de Secure Sockets Layer (SSL) en las URL de tienda. Asegúrese de que el servidor web admita SSL antes de seleccionar esta opción.<br><br>`0` deshabilita el uso de SSL. En este caso, se supone que todas las demás opciones de URL seguras también son 0. Este es el valor predeterminado. | No |
| `--base-url-secure` | URL base segura que se utilizará para acceder a su administrador y tienda en el siguiente formato: `http[s]://<host or ip>/<your install dir>/` | No |
| `--use-secure-admin` | `1` significa que utiliza SSL para acceder al administrador. Asegúrese de que el servidor web admita SSL antes de seleccionar esta opción.<br><br>`0` significa que no utiliza SSL con el administrador. Este es el valor predeterminado. | No |
| `--admin-use-security-key` | `1` hace que la aplicación utilice un valor clave generado aleatoriamente para acceder a las páginas en el administrador y en los formularios. Estos valores clave ayudan a evitar ataques de falsificación de scripts en sitios múltiples. Este es el valor predeterminado.<br/><br/>`0` desactiva el uso de la clave. | No |
| `--magento-init-params` | Agregar a cualquier comando para personalizar los parámetros de inicialización de la aplicación<br/><br/>Por ejemplo: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | No |
