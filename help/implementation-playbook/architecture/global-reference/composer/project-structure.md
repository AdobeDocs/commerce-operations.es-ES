---
title: Estructura del proyecto del Compositor
description: Aprenda a configurar y mantener la opción de paquetes independientes descrita en los ejemplos de arquitectura de referencia global.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 8757d5b8-8309-452f-bfb3-1188a816d14f
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Estructura del proyecto del Compositor

Esta guía describe cómo configurar y mantener la opción [paquetes separados](../examples.md#option-1-separate-packages) descrita en los ejemplos de arquitectura de referencia global (GRA).

## Requisitos previos

Antes de empezar, compruebe lo siguiente:

- Tiene un repositorio de Git
- Tiene un repositorio de Compositor (en este tema se resalta Private Packagist)
- Ha configurado su repositorio Composer para reflejar los repositorios `repo.magento.com` y `packagist.org`

## Repositorio de proyectos de Git principal

El repositorio del proyecto Git principal solo debe contener un proyecto Composer. Puede administrar todo lo demás con los paquetes de Composer. El proyecto principal no debe contener nada que no sea la siguiente estructura de archivos porque Composer instala todos los demás paquetes mediante dependencias:

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

Agregue el siguiente contenido al archivo `.gitignore`:

```tree
/*
!/composer.json
!/composer.lock
```

## Inicializar el proyecto principal

1. Cree un repositorio Git llamado `project-<region/country/brand>`.

1. Crear `composer.json` y `composer.lock` archivos:

   ```bash
   composer create-project --no-install --repository-url=https://repo.magento.com/ magento/project-enterprise-edition project-<region/country/brand>
   cd <install-directory-name>
   printf '/*\n!/composer.json\n!/composer.lock\n!/.gitignore' > .gitignore
   composer config --unset version
   composer config name '<client>/project-<region/country/brand>'
   composer config description '<client> <region/country/brand> main composer project'
   composer config repositories.private-packagist composer https://repo.packagist.com/<client>/
   composer config repositories.packagist.org false
   composer config --unset repositories.0
   composer install
   git init
   git add --all
   git commit -m 'initialize project'
   git remote add origin git@bitbucket.org:<client>/project-<region/country/brand>.git
   git push -u origin master
   ```

## Guardar archivos que no son de módulo

1. Agregue el archivo `app/etc/config.xml` al repositorio Git.

   Puede utilizar el módulo que va a crear para instalar otros archivos de región o específicos de marca, como `.htaccess`, archivos de texto de autenticación de Google o Bing, ejecutables u otros archivos estáticos que no administren los módulos de Adobe Commerce.

   Use `magento2-component` paquetes de tipo para crear una asignación de archivos y copiar los archivos en el repositorio principal de Git durante `composer install` y `composer update` operaciones.

1. Cree un repositorio Git que siga la convención de nomenclatura `component-environment-<region/country/brand>`:

   ```bash
   bin/magento module:enable --all
   cd ../
   mkdir component-environment-<region/country/brand>
   cd component-environment-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/component-environment-<region/country/brand>' \
    --description='<client> <region/country/brand> environment files' \
    --type=magento2-component \
    --require="magento/magento-composer-installer:*"
   mkdir -p app/etc
   cp ../project-<region/country/brand>/app/etc/config.php app/etc/
   composer config -e
   ```

1. Agregue el archivo `app/etc/config.php` como una asignación en el atributo `extra.map` de su archivo `composer.json`:

   ```json
   {
       "name": "example-client/component-environment-emea",
       "description": "Example client EMEA environment files",
       "type": "magento2-component",
       "require": {
           "magento/magento-composer-installer": "*"
       },
       "extra": {
           "map": [
               [
                   "app/etc/config.php",
                   "app/etc/config.php"
               ]
           ]
       }
   }
   ```

1. Valide el archivo `composer.json` y configúrelo en el repositorio Git:

   ```bash
   composer validate
   git init
   git add --all
   git commit -m 'initialize component'
   git remote add origin git@bitbucket.org:<client>/component-environment-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

## Configuración de metapaquetes

1. Cree los siguientes repositorios Git:

   - `meta-gra`
   - `meta-<region/country/brand>`

1. Configure el siguiente árbol de dependencias:

   ```tree
   client/project-<region/country/brand>
   └─ requires -> client/meta-<region/country/brand>
                  ├─ requires -> client/component-environment-<region/country/brand>
                  └─ requires -> client/meta-gra
                                 └─ requires -> magento/product-enterprise-edition
   ```

1. Cree el metapaquete GRA:

   ```bash
   cd ..
   mkdir meta-gra
   cd meta-gra
   composer init --no-interaction \
    --name='<client>/meta-gra' \
    --description='<client> GRA meta package' \
    --type=metapackage \
    --require="magento/product-enterprise-edition:<exact.required.version>"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-gra.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Cree el metapaquete de marca:

   ```bash
   cd ..
   mkdir meta-<region/country/brand>
   cd meta-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/meta-<region/country/brand>' \
    --description='<client> <region/country/brand> meta package' \
    --type=metapackage \
    --require="<client>/component-environment-<region/country/brand>:~0.1" \
    --require="<client>/meta-gra:~0.1"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Requiere la recopilación mediante la administración de dependencias en el proyecto principal:

   ```bash
   cd ../project-<region/country/brand>
   rm app/etc/config.php
   composer remove --no-update magento/product-enterprise-edition
   composer require --no-update "<client>/meta-<region/country/brand>:~0.1"
   composer config minimum-stability alpha
   composer config prefer-stable true
   composer update
   git add --all
   git commit -m 'set up GRA dependency tree'
   git push origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Compruebe que Composer copió el archivo `app/etc/config.php` de `<client>/component-environment-<region/country/brand>`.

## Implementación de código

En el servidor web, puede implementar código mediante Composer, pero no puede actualizar el proyecto principal. Vuelva a instalar el proyecto mediante Composer con cada nueva implementación, lo que elimina el requisito de que los servidores de producción y prueba tengan acceso a Git.

## Añadir otras instancias y paquetes

Cada instancia (región, marca o instalación única de Adobe Commerce) debe obtener su propia instancia de **proyecto principal**, **metapaquete específico** y **paquete de componentes de entorno**. El **metapaquete GRA** debe **compartirse** en todas las instancias.

Los paquetes funcionales (como módulos, temáticas, paquetes de idiomas y bibliotecas de Adobe Commerce) y los paquetes de terceros deben ser requeridos por:

- **Metapackage de GRA**: para la instalación en _todas_ las instancias
- **metapackage específico de instancia**: para su instalación en una sola marca o región

>[!IMPORTANT]
>
>No requiere paquetes en el archivo `composer.json` del proyecto principal en las ramas `main` o `release`.

## Preparación para el desarrollo

Para desarrollo, instale `develop` versiones de todos los módulos que mantenga.

Según su estrategia de ramificación, podría tener `develop`, `qa`, `uat` y `main` ramas. Cada rama existe en el Compositor con un prefijo `dev-`. Por lo tanto, la rama `develop` se puede requerir a través del Compositor como la versión `dev-develop`.

1. Cree `develop` ramas en todos los módulos y repositorios de proyectos.

   ```bash
   cd ../component-environment-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../meta-<region/country/brand>
   git checkout master
   git checkout -b develop
   
   git push -u origin develop
   
   
   cd ../meta-gra
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../project-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   composer require \
   "magento-services/meta-fantasy-corp:dev-develop as 0.999" \
   "magento-services/meta-gra:dev-develop as 0.999" \
   "magento-services/component-environment-fantasy-corp:dev-develop as 0.999"
   ```

   El paso anterior genera las líneas siguientes en el archivo `composer.json`:

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**No combine** estos `composer.json` cambios de archivo en la rama de producción. Instalar solo versiones estables de paquetes en las ramas `release` y `main`. Puede definir estas dependencias para `qa` ramas y otras ramas que no sean principales.
