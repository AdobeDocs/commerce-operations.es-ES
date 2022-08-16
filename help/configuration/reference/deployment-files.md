---
title: Archivos de configuración para la implementación
description: Obtenga información sobre cómo funcionan los archivos de configuración para instalar la aplicación Commerce.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---


# Archivos de configuración para la implementación

Adobe Commerce proporciona archivos de configuración que permiten personalizar fácilmente un componente y crear tipos de configuración para ampliar la funcionalidad predeterminada. El proceso de configuración de la implementación consiste en la configuración compartida y específica del sistema para la instalación. La configuración de implementación de Commerce se divide entre [`app/etc/config.php`](../reference/config-reference-configphp.md) y [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` es la variable _shared_ archivo de configuración.
Este archivo contiene la lista de módulos, temas y paquetes de idioma instalados; y los ajustes de configuración compartidos.

   Compruebe este archivo para controlar el código fuente y utilícelo en los sistemas de desarrollo, ensayo y producción.

   A partir de la versión 2.2, la variable `app/etc/config.php` El archivo ya no es una entrada en la variable `.gitignore` archivo.
Esto se hizo para facilitar [implementación de canalización](../deployment/technical-details.md).

- `app/etc/env.php` contiene configuraciones específicas del entorno de instalación.

Juntos, `config.php` y `env.php` se denominan comercio _configuración de implementación_ porque los archivos se crean durante la instalación y son necesarios para iniciar la aplicación Commerce.

>[!INFO]
>
>La variable [!DNL Commerce 2] la configuración de implementación reemplaza a `local.xml` en [!DNL Magento 1.x].

A diferencia de otros [archivos de configuración del módulo](../reference/module-files.md), la configuración de la implementación de comercio se carga en la memoria durante la inicialización, no se combina con ningún otro archivo y no se puede ampliar. (`config.php` y `env.php` sin embargo, se combinan entre sí).

## Detalles sobre la configuración de implementación

`config.php` y `env.php` son archivos PHP que devuelven un [matriz asociativa multidimensional](https://www.w3schools.com:443/php/php_arrays.asp), que es básicamente una organización jerárquica de parámetros y valores de configuración.

En el nivel superior de esta matriz se encuentran _segmentos de configuración_. Un segmento tiene contenido arbitrario (un valor escalar o una matriz anidada) que se distingue por una clave arbitraria, donde tanto la clave como el par de valor están definidos por el marco de comercio.

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) solo proporciona acceso a estas secciones, pero no permite ampliarlas.

En el siguiente nivel de jerarquía, los elementos de cada segmento se ordenan según la variable [módulo](https://glossary.magento.com/module) definición de secuencia, que se obtiene combinando los archivos de configuración de todos los módulos, excepto los módulos desactivados.

Las siguientes secciones tratan sobre la estructura y el contenido de la configuración de implementación:

- Administrar módulos instalados
- Configuración específica del sistema

## Administrar módulos instalados

La variable `config.php` contiene una lista de módulos instalados. Adobe Commerce proporciona utilidades basadas en la línea de comandos y en la web para administrar módulos (instalar, desinstalar, habilitar, deshabilitar o actualizar).

Ejemplos:

- Desinstalar componentes: [`bin/magento setup:uninstall`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall.html)
- Comprobar el estado de los componentes: [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
- Habilitar o deshabilitar componentes: [`bin/magento module:disable`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-enable.html#instgde-cli-subcommands-enable-disable), [`bin/magento module:enable`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-enable.html#instgde-cli-subcommands-enable-disable).

> _config.php_

```php
return array (
  'modules' =>
  array (
    'Magento_Core' => 1,
    'Magento_Store' => 1,
    'Magento_Theme' => 1,
    'Magento_Authorization' => 1,
    'Magento_Directory' => 1,
    'Magento_Backend' => 1,
    'Magento_Backup' => 1,
    'Magento_Eav' => 1,
    'Magento_Customer' => 1,
...
  ),
);
```

El valor `1` o `0` indica si un módulo está habilitado o deshabilitado.

La aplicación Commerce no reconoce los módulos deshabilitados. en otras palabras, no participan en la configuración de combinación, en la inyección de dependencias, eventos, complementos, etc. Los módulos desactivados no modifican el [storefront](https://glossary.magento.com/storefront) o [Administrador](https://glossary.magento.com/admin) y no afectan al enrutamiento.

La única diferencia práctica de un módulo deshabilitado y un módulo ausente en la base de código es que el cargador automático encuentra un módulo deshabilitado, y sus clases y constantes están disponibles para su reutilización en otro código.