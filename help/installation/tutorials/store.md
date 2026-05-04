---
title: Configuración de la tienda
description: Obtenga información sobre cómo configurar el almacén de Adobe Commerce desde la línea de comandos después de la configuración de la implementación y la configuración del esquema de la base de datos, incluidas las opciones de instalación segura.
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: 41b8d77793f1c24f08ff7e6a2d35826a62477534
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Configuración de la tienda

Antes de ejecutar este comando, debe hacer lo siguiente *o* y debe [instalar la aplicación](../advanced.md):

* [Crear o actualizar la configuración de implementación](deployment.md)
* [Creación del esquema de base de datos](database.md)

## Instalación segura

{{$include /help/_includes/secure-install.md}}

## Configuración de la tienda

Uso de comandos:

```shell
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

Donde la siguiente tabla define parámetros y valores:

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--base-url` | Dirección URL base que se utilizará para obtener acceso al administrador y a la tienda en cualquiera de los formatos siguientes: <br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**Nota:** El esquema (`http://` o `https://`) y una barra diagonal son obligatorios. `<your install dir>` es la ruta de acceso relativa a docroot en la que se instala la aplicación. Según la configuración del servidor web y los hosts virtuales, la ruta puede ser magento2 o estar en blanco.<br><br>Para tener acceso a la aplicación en localhost, puede usar `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}`, que representa una dirección URL base definida por una configuración de host virtual o por un entorno de virtualización como Docker. Por ejemplo, si configura un host virtual con el nombre de host commerce.example.com, puede instalar la aplicación con `--base-url={{base_url}}` y acceder al administrador con una dirección URL como `http://commerce.example.com/admin`. | No |
| `--language` | Código de idioma que se va a usar en la administración y tienda.<br><br>(Si aún no lo ha hecho, puede ver la lista de códigos de idioma al escribir `magento info:language:list` desde el directorio `bin`.) | No |
| `--currency` | Moneda predeterminada que se utilizará en la tienda. <br><br>(si aún no lo ha hecho, puede ver la lista de monedas al escribir `magento info:currency:list` desde el directorio `bin`.) | No |
| `--timezone` | Zona horaria predeterminada que se utilizará en la administración y en la tienda. (Si aún no lo ha hecho, puede ver la lista de zonas horarias escribiendo `magento info:timezone:list` desde el directorio `bin`.) | No |
| `--use-rewrites` | `1` significa que usa reescrituras de servidor web para los vínculos generados en la tienda y el administrador.<br><br>`0` deshabilita el uso de reescrituras de servidores web. Esta es la opción predeterminada. | No |
| `--use-secure` | `1` habilita el uso de Capa de sockets seguros (SSL) en las direcciones URL de las tiendas. Asegúrese de que el servidor web admita SSL antes de seleccionar esta opción.<br><br>`0` deshabilita el uso de SSL. En este caso, todas las demás opciones de URL segura se suponen que también son 0. Esta es la opción predeterminada. | No |
| `--base-url-secure` | URL base segura que se usará para tener acceso a su administración y tienda en el siguiente formato: `http[s]://<host or ip>/<your install dir>/` | No |
| `--use-secure-admin` | `1` significa que utiliza SSL para acceder al administrador. Asegúrese de que el servidor web admita SSL antes de seleccionar esta opción.<br><br>`0` significa que no utiliza SSL con el administrador. Esta es la opción predeterminada. | No |
| `--admin-use-security-key` | `1` hace que la aplicación use un valor clave generado aleatoriamente para acceder a páginas del administrador y de formularios. Estos valores clave ayudan a evitar ataques de falsificación de scripts entre sitios. Éste es el valor predeterminado.<br/><br/>`0` deshabilita el uso de la clave. | No |
| `--magento-init-params` | Agregue a cualquier comando para personalizar los parámetros de inicialización de la aplicación<br/><br/>Por ejemplo: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | No |

<!-- Last updated from includes: 2022-09-08 11:33:05 -->
