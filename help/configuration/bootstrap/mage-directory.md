---
title: Personalizar rutas de directorio base
description: Utilice la variable MAGE_DIRS para establecer una matriz de rutas absolutas.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 02c69e890b40643781ab8f48c3133527dd79386a
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# Rutas de directorio base

La variable de entorno `MAGE_DIRS` le permite especificar rutas de acceso de directorio base personalizadas y fragmentos de direcciones URL base que utiliza la aplicación Commerce para generar rutas de acceso absolutas a varios archivos o para generar direcciones URL.

## Establecer MAGE_DIRS

Especifique una matriz asociativa donde las claves son constantes de [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] y los valores son rutas absolutas de directorios o sus rutas de URL, respectivamente.

Puede establecer `MAGE_DIRS` de cualquiera de las siguientes maneras:

- [Establecer el valor de los parámetros de arranque](../bootstrap/set-parameters.md)
- Utilice un script de punto de entrada personalizado como el siguiente:

  ```php
  <?php
  /**
   * Copyright Adobe
   * All Rights Reserved.
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

El ejemplo anterior establece rutas de acceso para los directorios `[cache]` y `[media]` en `/mnt/nfs/cache` y `/mnt/nfs/media`, respectivamente.

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
