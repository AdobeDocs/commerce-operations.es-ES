---
title: Realización de una actualización
description: Siga estos pasos para actualizar las implementaciones locales de Adobe Commerce.
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---


# Realización de una actualización

Puede actualizar _implementaciones locales_ de la aplicación Adobe Commerce desde la línea de comandos si instaló el software mediante:

- Descargando el metapaquete Composer mediante el comando `composer create-project`.
- Instalación del archivo comprimido.

>[!NOTE]
>
>- Para Adobe Commerce sobre proyectos de infraestructura en la nube, consulte [Actualizar la versión de Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html) en la Guía de la nube.
>- No utilice este método para actualizar si ha clonado el repositorio de GitHub. Consulte [Actualizar una instalación basada en Git](../developer/git-installs.md).

Las siguientes instrucciones muestran cómo realizar la actualización mediante el Administrador de paquetes del Compositor. Adobe Commerce 2.4.2 ha introducido la compatibilidad con Composer 2. Si intenta actualizar desde &lt;2.4.1, primero debe actualizar a una versión compatible con Composer 2 (por ejemplo, 2.4.2) mediante Composer 1 _antes de_ actualizar a Composer 2 para actualizaciones >2.4.2. Además, debe ejecutar una [versión compatible](../../installation/system-requirements.md) de PHP.

>[!WARNING]
>
>El procedimiento para actualizar Adobe Commerce ha cambiado. Debe instalar una nueva versión del paquete `magento/composer-root-update-plugin` (consulte [requisitos previos](../prepare/prerequisites.md)). Además, los comandos para la actualización han cambiado de `composer require magento/<package_name>` a `composer require-commerce magento/<package_name>`.

## Antes de empezar

Debe completar los [requisitos previos de actualización](../prepare/prerequisites.md) para preparar su entorno antes de iniciar el proceso de actualización.

## Administración de paquetes

>[!NOTE]
>
>Consulte los ejemplos que aparecen al final de esta sección para obtener ayuda sobre cómo especificar diferentes niveles de versión. Por ejemplo, parches de calidad y parches de seguridad. Si no encuentra estos paquetes en Composer, póngase en contacto con el Soporte técnico de Adobe Commerce.

1. Cambie al modo de mantenimiento para evitar el acceso a su tienda durante el proceso de actualización.

   ```bash
   bin/magento maintenance:enable
   ```

   Consulte [Habilitar o deshabilitar el modo de mantenimiento](../../installation/tutorials/maintenance-mode.md) para ver opciones adicionales. Opcionalmente, puede crear una [página de modo de mantenimiento personalizado](../troubleshooting/maintenance-mode-options.md).

1. Iniciar el proceso de actualización mientras se ejecutan procesos asincrónicos, como los consumidores de cola de mensajes, puede dañar los datos. Para evitar que se dañen los datos, deshabilite todos los trabajos cron.

   _Adobe Commerce en la infraestructura en la nube:_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source:_

   ```bash
   bin/magento cron:remove
   ```

1. Iniciar todos los consumidores de colas de mensajes manualmente para asegurarse de que se consumen todos los mensajes.

   ```bash
   bin/magento cron:run --group=consumers
   ```

   Espere a que se complete el trabajo cron. Puede supervisar el estado del trabajo con un visor de procesos o ejecutando el comando `ps aux | grep 'bin/magento queue'` varias veces hasta que se completen todos los procesos.

1. Cree una copia de seguridad del archivo `composer.json`.

   ```bash
   cp composer.json composer.json.bak
   ```

1. Añada o elimine paquetes específicos según sus necesidades.

   Por ejemplo, si está actualizando de Magento Open Source a Adobe Commerce, elimine el paquete de Magento Open Source.

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   También puede actualizar los datos de ejemplo.

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _Adobe Commerce:_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
     ```

   - _Magento Open Source:_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
     ```

1. Actualice la instancia con la siguiente sintaxis de comando `composer require-commerce`:

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   Las opciones de comando incluyen:

   - `<product>` —(Obligatorio) El paquete para actualizar. Para instalaciones locales, este valor debe ser `product-community-edition` o `product-enterprise-edition`.

   - `<version>` —(Obligatorio) La versión de Adobe Commerce a la que está actualizando. Por ejemplo, `2.4.3`.

   - `--no-update` —(Obligatorio) Deshabilita la actualización automática de las dependencias.

   - `--interactive-root-conflicts` —(Opcional) Permite ver y actualizar de forma interactiva cualquier valor obsoleto de versiones anteriores o cualquier valor personalizado que no coincida con la versión a la que está actualizando.

   - `--force-root-updates` —(Opcional) Anula todos los valores personalizados en conflicto con los valores de Commerce esperados.

   - `--help` —(Opcional) Proporciona detalles de uso sobre el complemento.

   Si no se especifica ni `--interactive-root-conflicts` ni `--force-root-updates`, el comando mantiene los valores existentes en conflicto y muestra un mensaje de advertencia. Para obtener más información sobre el complemento, consulte el [LÉAME de uso del complemento](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. Actualice las dependencias.

   ```bash
   composer update
   ```

### Ejemplo: Enumerar versiones disponibles

Para ver la lista completa de versiones de 2.4.x disponibles:

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### Ejemplo: parche de calidad

Los parches de calidad contienen principalmente _y_ correcciones de seguridad funcionales. Sin embargo, a veces pueden contener nuevas funciones compatibles con versiones anteriores. Use Composer para descargar un parche de calidad.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6 --no-update
```

### Ejemplo: parche de seguridad

Los parches de seguridad solo contienen correcciones de seguridad. Están diseñadas para que el proceso de actualización sea más rápido y sencillo. Los parches de seguridad utilizan la convención de nombres del Compositor `2.4.x-px`.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6-p3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6-p3 --no-update
```

## Actualización de metadatos

1. Actualice los campos `"name"`, `"version"` y `"description"` en el archivo `composer.json` según sea necesario.

   >[!NOTE]
   >
   >La actualización de los metadatos del archivo `composer.json` es totalmente superficial, no funcional.

1. Aplicar actualizaciones.

   ```bash
   composer update
   ```

1. Borrar los subdirectorios `var/` y `generated/`:

   ```bash
   rm -rf var/cache/*
   ```

   ```bash
   rm -rf var/page_cache/*
   ```

   ```bash
   rm -rf generated/code/*
   ```

   >[!NOTE]
   >
   >Si utiliza un almacenamiento en caché que no sea el sistema de archivos, como Redis o Memcached, también deberá borrar manualmente la caché allí.

1. Actualizar el esquema y los datos de la base de datos.

   ```bash
   bin/magento setup:upgrade
   ```

1. Desactive el modo de mantenimiento.

   ```bash
   bin/magento maintenance:disable
   ```

1. _(Opcional)_ Reiniciar el barniz.

   Si utiliza Barnish para el almacenamiento en caché de páginas, reinícielo:

   ```bash
   service varnish restart
   ```

## Compruebe su trabajo

Para comprobar si la actualización se ha realizado correctamente, abra la dirección URL de la tienda en un explorador web. Si la actualización no se ha realizado correctamente, la tienda no se cargará correctamente.

Si la aplicación falla con un error `We're sorry, an error has occurred while generating this email.`:

1. Restablecer la propiedad y los permisos del sistema de archivos [como usuario con privilegios de `root`.](../../installation/prerequisites/file-system/configure-permissions.md)
1. Borre los siguientes directorios:
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Vuelva a comprobar la tienda en el explorador web.
