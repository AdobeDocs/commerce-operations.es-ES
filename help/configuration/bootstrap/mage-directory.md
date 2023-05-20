---
title: Personalizar rutas de directorio base
description: Utilice la variable MAGE_DIRS para establecer una matriz de rutas absolutas.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Rutas de directorio base

El `MAGE_DIRS` La variable de entorno permite especificar rutas de directorio base personalizadas y fragmentos de direcciones URL base que utiliza la aplicación Commerce para crear rutas absolutas a varios archivos o para generar direcciones URL.

## Establecer MAGE_DIRS

Especifique una matriz asociativa de la que las claves sean constantes [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] y son rutas absolutas de directorios o sus rutas URL, respectivamente.

Puede establecer `MAGE_DIRS` de cualquiera de las siguientes maneras:

- [Establecer el valor de los parámetros de arranque](../bootstrap/set-parameters.md)
- Utilice un script de punto de entrada personalizado como el siguiente:

   ```php
   <?php
   /**
    * Copyright © Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\App\Bootstrap;
   use Magento\Framework\App\Filesystem\DirectoryList;
   use Magento\Framework\App\Http;
   
   require __DIR__ . '/app/bootstrap.php';
   $params = $_SERVER;
   $params[Bootstrap::INIT_PARAM_FILESYSTEM_DIR_PATHS] = [
        DirectoryList::PUB => [DirectoryList::URL_PATH => ''],
        DirectoryList::MEDIA => [DirectoryList::PATH => '/mnt/nfs/media', DirectoryList::URL_PATH => ''],
        DirectoryList::STATIC_VIEW => [DirectoryList::URL_PATH => 'static'],
        DirectoryList::UPLOAD => [DirectoryList::URL_PATH => '/mnt/nfs/media/upload'],
        DirectoryList::CACHE => [DirectoryList::PATH => '/mnt/nfs/cache'],
   ];
   $bootstrap = Bootstrap::create(BP, $params);
   /** @var Http $app */
   $app = $bootstrap->createApplication(Http::class);
   $bootstrap->run($app);
   ```

En el ejemplo anterior se establecen las rutas de `[cache]` y `[media]` directorios para `/mnt/nfs/cache` y `/mnt/nfs/media`, respectivamente.

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
