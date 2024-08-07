---
title: Desarrollo del compositor
description: Obtenga información sobre el desarrollo de módulos de Compositor in situ en el directorio "provider/".
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 7664ffb5-2e46-49c3-b2e6-c133c35d2f6b
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Desarrollo del compositor

En este tema se describe el método recomendado para desarrollar módulos Composer in situ (como repositorios Git en el directorio `vendor/`) y agregar esos módulos al proyecto Git principal.

>[!NOTE]
>
>Estas directrices se aplican principalmente a [proyectos de arquitectura de referencia global (GRA)](../overview.md).

## Preparación de una rama de desarrollo

1. Cree o retire la rama de desarrollo en su repositorio principal de Git.
1. Requerir versiones de desarrollo para cada módulo que mantenga.

   En este ejemplo, cada rama del repositorio principal de Git representa una versión del paquete Composer. La convención de nombres recomendada para las versiones de Compositor en este escenario es `dev-` seguida del nombre de la rama. Por ejemplo:

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. Si otro paquete Composer requiere una versión específica de un módulo (por ejemplo, `client/module-example 1.0.12`), instálelo con un alias:

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   Para la rama `qa`, reemplace `dev-develop` por `dev-qa`.

## Conversión de paquetes a repositorios Git

De manera predeterminada, los paquetes no contienen un directorio `.git/`. Composer puede extraer paquetes de Git en lugar de usar los paquetes predefinidos de Composer. La ventaja de este enfoque es que puede modificar fácilmente los paquetes durante el desarrollo.

1. Quite el módulo del directorio `vendor/`.

   ```bash
   rm -rf vendor/client/module-example
   ```

1. Vuelva a instalar el módulo con el origen Git [especificado](#prepare-a-development-branch).

   ```bash
   composer install --prefer-source
   ```

1. Compruebe que el paquete Composer sea ahora un repositorio Git:

   ```bash
   cd vendor/client/module-example
   git remote -v
   ```

1. Para convertir varios módulos en repositorios Git por lotes (por ejemplo, módulos &quot;cliente&quot;):

   ```bash
   rm -rf vendor/client
   composer install --prefer-source
   ```

## Iniciar desarrollo

1. Cree o extraiga una función o rama de trabajo. El siguiente ejemplo muestra una rama con el mismo nombre que un ticket Jira.

   ```bash
   cd vendor/client/module-example
   git checkout master
   git checkout -b JIRA-1200
   ```

1. Después de cambiar las ramas de un módulo, vea los cambios vaciando la caché de Adobe Commerce y el contenido estático.

   ```bash
   bin/magento cache:flush
   bin/magento module:enable --all --clear-static-content
   ```

## Actualizar el proyecto principal con el desarrollo

Actualice el repositorio principal de Git modificando el archivo `composer.lock`. Si el módulo es nuevo, actívelo.

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
