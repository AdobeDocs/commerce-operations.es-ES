---
title: Ejemplos de arquitectura de referencia global
description: Consulte ejemplos de administración de código para proyectos de Adobe Commerce a gran escala.
role: Developer, Architect
level: Experienced
hide: true
hidefromtoc: true
exl-id: 2a85b9bf-e547-4a2a-9234-210865f55609
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# Ejemplos de arquitectura de referencia global

En este tema se describen formas comunes de organizar una base de código de [arquitectura de referencia global (GRA)](overview.md). Aunque se prefiere la opción [separar paquetes](#option-1-separate-packages), algunas situaciones requieren una de las otras opciones que se describen a continuación.

## Definiciones

{{$include /help/_includes/gra-definitions.md}}

## Opción 1: separar los paquetes

Consulte las prácticas recomendadas en la [estructura del proyecto Composer](composer/project-structure.md) para configurar este método.

![Diagrama que ilustra la opción de paquetes separados para la arquitectura de referencia global](../../../assets/playbooks/gra-separate-packages.png)

La forma más flexible de administrar los paquetes del Compositor de GRA es a través de metapaquetes. Los metapaquetes sólo contienen un archivo de `composer.json`, que define otras dependencias de paquetes. Cree metapaquetes usando [repositorios de Packagist privado](https://packagist.com/).

### Proyecto principal `composer.json`

```json
{
    "name": "example-client/region-1",
    "description": "Example Client Region 1",
    "type": "project",
    "require": {
        "magento/product-enterprise-edition": "2.3.5",
        "example-client/meta-region-1": "~1.0"
    },
    "minimum-stability": "dev",
    "prefer-stable": true,
    "repositories": [
        {"type": "composer", "url": "https://repo.packagist.com/example-client/"},
        {"packagist.org": false}
    ]
}
```

### `example-client/meta-region-1 composer.json`

```json
{
    "name": "example-client/meta-region-1",
    "description": "Region 1 meta package",
    "type": "metapackage",
    "require": {
        "example-client/meta-gra": "~1.0",
        "example-client/theme-frontend-region1",
        "example-client/language-es-es",
        "ingenico/ogone-client"
    }
}
```

### `example-client/meta-gra composer.json`

```json
{
    "name": "example-client/meta-gra",
    "description": "GRA meta package",
    "type": "metapackage",
    "require": {
        "geoip2/geoip2": "~2.0",
        "magento-services/module-stackify-logger": "~1.1",
        "example-client/sap-connector",
        "example-client/service-chat",
        "example-client/store-locator"
    }
}
```

Cada módulo, paquete de idioma, tema y biblioteca tiene su propio repositorio de Git. Cada repositorio de Git se sincroniza automáticamente con el repositorio de Private Packagist y genera un paquete allí siempre y cuando haya un archivo `composer.json` en la raíz del repositorio de Git.

## Opciones 2: Paquetes en bloque

A continuación se muestra un ejemplo de varios módulos dentro de un mismo paquete de Composer.

Un paquete masivo solo puede incluir paquetes del mismo tipo. Por ejemplo, si tiene varios paquetes para módulos, temáticas, paquetes de idiomas y bibliotecas de Adobe Commerce, debe crear paquetes por lotes independientes para cada tipo.

La estructura de archivos dentro del directorio del proveedor debe ser similar al siguiente ejemplo. Sin embargo, compruebe el proyecto para ver qué debe incluirse en el repositorio Git):

```tree
.
└── example-client/
    └── gra/
        └── src/
            ├── SapConnector/
            │   ├── etc/
            │   └── registration.php
            ├── ServiceChat/
            │   ├── etc/
            │   └── registration.php
            ├── StoreLocator/
            │   ├── etc/
            │   └── registration.php
            └── composer.json
```

El archivo de `composer.json` debe tener este aspecto:

```json
{
    "name": "example-client/gra",
    "description": "GRA Modules",
    "require": {
        "magento/magento-composer-installer": "*"
    },
    "type": "magento2-module",
    "autoload": {
        "files": [
            "src/SapConnector/registration.php",
            "src/ServiceChat/registration.php",
            "src/StoreLocator/registration.php"
        ],
        "psr-4": {
            "ExampleClient\\SapConnector\\": "src/SapConnector",
            "ExampleClient\\ServiceChat\\": "src/ServiceChat",
            "ExampleClient\\StoreLocator\\": "src/StoreLocator"
        }
    }
}
```

## Opción 3: Dividir Git

Esta arquitectura utiliza cuatro repositorios Git para almacenar código:

- `core`: contiene la instalación principal de Adobe Commerce. Se utiliza para actualizar las versiones de Adobe Commerce.
- `GRA`: contiene código GRA. Todos los módulos GRA, paquetes de idiomas, temas de etiquetas blancas y bibliotecas.
- `brand/region`: cada marca o región tiene su propio repositorio con solo código específico de marca o región.
- `release`: todo lo anterior se combina con este repositorio Git. Aquí solo se permiten confirmaciones de combinación.

![Diagrama que ilustra la opción de Git dividido para la arquitectura de referencia global](../../../assets/playbooks/gra-split-git.png)

Para configurar esta opción:

1. Cree los cuatro tipos de repositorio en Git. Crear los repositorios de `core` y `GRA` solo una vez. Crear un `brand/region` y un repositorio `release` para cada marca.

   Nombres de repositorios sugeridos:

   - `m2-core`
   - `m2-gra`
   - `m2-region-x`/`m2-brand-x` (por ejemplo, `m2-emea`/`m2-adobe`)
   - `m2-release-region-x`/`m2-release-brand-x` (por ejemplo, `m2-release-emea`/`m2-release-adobe`)

1. Cree un directorio `release/` y ejecute lo siguiente para crear un historial Git compartido para todos los repositorios.

   ```bash
   git init
   git remote add origin git@github.com:example-client/m2-release-brand-x.git
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   touch .gitkeep
   git add .gitkeep
   git commit -m 'initialize repository'
   git push -u origin master
   git push core master
   git push gra master
   git push region-x master
   ```

1. Clone cada repositorio, excepto `core`, en un directorio diferente del equipo.

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   git clone git@github.com:example-client/m2-region-x.git
   git clone git@github.com:example-client/m2-gra.git
   ```

1. [Instalar Adobe Commerce con Composer](../../../installation/composer.md). Elimine el archivo `.gitignore`, agregue el remoto `core`, agregue y confirme el código, y presione.

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition m2-core
   cd m2-core
   git init
   rm .gitignore
   git remote add origin git@github.com:example-client/m2-core.git
   git fetch
   git checkout .gitkeep
   git add --all
   git commit -m 'install Adobe Commerce'
   git push
   ```

1. En el repositorio `GRA`, cree los siguientes directorios:

   - `app/code/`
   - `app/design/`
   - `app/i18n/`
   - `lib/`

1. Agregue el código. Elimine el archivo `.gitignore`, agregue y confirme el código, agregue el remoto y presione.

1. En el repositorio `brand/region`. Haga lo mismo que en el repositorio `GRA` y tenga en cuenta que los archivos deben ser únicos. No puede incluir el mismo archivo en este repositorio y en el repositorio `GRA`.

1. En el repositorio `release`, aplique la combinación.

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   cd m2-release-brand-x
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

1. Quitar el archivo `.gitkeep`.

1. Implemente el repositorio `release` en los servidores de producción, prueba, control de calidad y desarrollo. Actualizar el código `core`, `GRA` y `brand` es tan fácil como ejecutar los siguientes comandos:

   ```bash
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

## Opción 4: Monorepo (recomendado)

Esta estrategia imita de cerca la forma en que funciona el repositorio Git de Magento Open Source.

Todo el código se desarrolla y prueba en un único repositorio. La automatización destila paquetes de este único repositorio, que se puede instalar en entornos UAT y de producción mediante Composer.

![Diagrama que ilustra la opción monorepo para la arquitectura de referencia global](../../../assets/playbooks/gra-monorepo1.png)

La opción monorepo le ofrece la facilidad de trabajar en un único repositorio, a la vez que proporciona la flexibilidad de componer instancias con paquetes.

Las versiones y la destilación de paquetes se realizan mediante automatización, con acciones de GitHub o acciones de GitLab.

![Diagrama que ilustra la opción monorepo para la arquitectura de referencia global](../../../assets/playbooks/gra-monorepo2.png)

Consulte los siguientes recursos para obtener más información sobre esta automatización:

- [https://github.com/symplify/monorepo-builder](https://github.com/symplify/monorepo-builder)
- [https://github.com/danharrin/monorepo-split-github-action](https://github.com/danharrin/monorepo-split-github-action)

>[!TIP]
>
>La configuración de un monorrepo es avanzada, pero ofrece la mayor flexibilidad con el menor costo de gastos generales.

## No mezclar estrategias

No se recomienda utilizar un método combinado con Composer para paquetes GRA y el directorio `app/` para paquetes de marca o región.

No solo obtienes todas las _ventajas_, sino también todas las _desventajas_ de ambos métodos. Debe elegir una o la otra (Git o Composer) para trabajar de forma óptima.

## Soluciones que se deben evitar

- **Convenciones de nomenclatura de módulos para indicar GRA o marca**

  Nombrar módulos para significar GRA o marca lleva a la falta de flexibilidad. En su lugar, utilice metapaquetes de Compositor para determinar a qué grupo pertenece un módulo. Por ejemplo, para el cliente VF, el paquete `vf/meta-gra` contiene referencias a todos los paquetes GRA y se puede instalar mediante el comando `composer require vf/meta-gra`. El paquete `vf/meta-kipling` contiene referencias a todos los paquetes específicos de Kipling y al paquete `vf/meta-gra`. Los módulos se denominan `vf/module-sales` y `vf/module-sap`, por ejemplo. Esta convención de nombres le permite mover paquetes entre la marca y el estado GRA, con bajo impacto.

- **Actualizaciones principales de Adobe Commerce por instancia**

  Programe actualizaciones principales de Adobe Commerce, incluidas las actualizaciones de parches, para diferentes marcas o regiones para que se ejecuten lo más cerca posible. El soporte de varias versiones de Adobe Commerce para módulos compartidos lleva a la ramificación de módulos debido a restricciones de compatibilidad y más del doble del esfuerzo de mantenimiento. Evite este mayor esfuerzo asegurándose de que todas las instancias se ejecuten en la misma versión de Adobe Commerce antes de continuar con el desarrollo regular.
