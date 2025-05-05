---
title: Archivos de configuración para implementación
description: Comprender cómo funcionan los archivos de configuración para instalar la aplicación de Commerce.
feature: Configuration, Deploy
exl-id: 772a6814-6b18-4f8f-b31e-72faf790ff37
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Archivos de configuración para implementación

Adobe Commerce proporciona archivos de configuración que permiten personalizar fácilmente un componente y crear tipos de configuración para ampliar la funcionalidad predeterminada. El proceso de configuración de la implementación consiste en la configuración compartida y específica del sistema para la instalación. La configuración de implementación de Commerce se divide entre [`app/etc/config.php`](../reference/config-reference-configphp.md) y [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` es el archivo de configuración _compartido_.
Este archivo contiene la lista de módulos, temáticas y paquetes de idiomas instalados, así como las opciones de configuración compartidas.

  Proteja este archivo para controlar el código fuente y utilícelo en los sistemas de desarrollo, ensayo y producción.

- `app/etc/env.php` contiene configuraciones específicas del entorno de instalación.

En conjunto, `config.php` y `env.php` se denominan la _configuración de implementación_ de Commerce porque los archivos se crean durante la instalación y son necesarios para iniciar la aplicación de Commerce.

>[!INFO]
>
>La configuración de implementación [!DNL Commerce 2] reemplaza a `local.xml` en [!DNL Magento 1.x].

A diferencia de otros [archivos de configuración del módulo](../reference/module-files.md), la configuración de la implementación de Commerce se carga en la memoria durante la inicialización, no se combina con ningún otro archivo y no se puede ampliar. (`config.php` y `env.php` se combinan entre sí, sin embargo).

## Detalles sobre la configuración de implementación

`config.php` y `env.php` son archivos PHP que devuelven una [matriz asociativa multidimensional](https://www.w3schools.com:443/php/php_arrays.asp), que es básicamente una disposición jerárquica de parámetros y valores de configuración.

En el nivel superior de esta matriz se encuentran _segmentos de configuración_. Un segmento tiene contenido arbitrario (un valor escalar o una matriz anidada) que se distingue por una clave arbitraria (donde el marco de trabajo de Commerce define tanto el par clave como valor).

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) simplemente proporciona acceso a estas secciones, pero no le permite ampliarlas.

En el siguiente nivel de jerarquía, los elementos de cada segmento se ordenan según la definición de secuencia del módulo, que se obtiene combinando todos los archivos de configuración de los módulos, excepto los módulos desactivados.

Las secciones siguientes describen la estructura y el contenido de la configuración de la implementación:

- Administrar módulos instalados
- Configuración específica del sistema

## Administrar módulos instalados

El archivo `config.php` contiene una lista de módulos instalados. Adobe Commerce proporciona utilidades basadas en la línea de comandos y en la web para administrar módulos (instalar, desinstalar, habilitar, deshabilitar o actualizar).

Ejemplos:

- Desinstalar componentes: [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- Comprobar el estado de los componentes: [`bin/magento module:status`](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/cli-reference/commerce-on-premises#modulestatus)
- Habilitar o deshabilitar componentes: [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md), [`bin/magento module:enable`](../../installation/tutorials/manage-modules.md).

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

La aplicación de Commerce no reconoce los módulos desactivados; es decir, no participan en la combinación de configuraciones, en la inyección de dependencias, en eventos, complementos, etc. Los módulos desactivados no modifican la tienda ni el administrador y no afectan al enrutamiento.

La única diferencia práctica entre un módulo deshabilitado y un módulo ausente en la base de código es que el cargador automático encuentra un módulo deshabilitado y sus clases y constantes están disponibles para su reutilización en otro código.
