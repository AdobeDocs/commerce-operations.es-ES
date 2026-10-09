---
title: Exportar ajustes de configuración
description: Obtenga información sobre cómo exportar los ajustes de configuración de Adobe Commerce a archivos mediante el volcado de configuración. Descubra la implementación y administración de la configuración de la canalización.
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%
---
# Exportar ajustes de configuración

En Commerce 2.2 y versiones posteriores de [modelo de implementación de canalización](../deployment/technical-details.md), puede mantener una configuración coherente en todos los sistemas. Después de configurar las opciones en el Administrador del sistema de desarrollo, exporte dichas opciones a los archivos de configuración mediante el siguiente comando:

```shell
bin/magento app:config:dump {config-types}
```

_config_ types_ es una lista de tipos de configuración que se van a volcar separados por espacios. Los tipos disponibles incluyen `scopes`, `system`, `themes` y `i18n`. Si no se especifica ningún tipo de configuración, el comando elimina toda la información de configuración del sistema.

El siguiente ejemplo volca ámbitos y temas únicamente:

```shell
bin/magento app:config:dump scopes themes
```

Como resultado de la ejecución del comando, se actualizan los siguientes archivos de configuración:

- `app/etc/config.php`

  Este es el archivo de configuración compartida para todas las instancias de Commerce.
  Incluya esto en el control de código fuente para que se pueda compartir entre los sistemas de desarrollo, compilación y producción.

  Ver [config.php reference](../reference/config-reference-configphp.md).

- `app/etc/env.php`

  Este es el archivo de configuración específico del entorno.
  Contiene configuraciones sensibles y específicas del sistema para entornos individuales.

  _no_ incluye este archivo en el control de código fuente.

  Ver [referencia env.php](../reference/config-reference-envphp.md).

## Configuración confidencial o específica del sistema

Para establecer la configuración confidencial escrita en `env.php`, use el comando [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values).

Los valores de configuración se especifican como confidenciales o específicos del sistema haciendo referencia a [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) en el archivo [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings#how-to-specify-values-as-sensitive-or-system-specific) del módulo.

Para exportar la configuración adicional del sistema al usar `config_types`, considere la posibilidad de usar el comando [`bin/magento config:set`](set-configuration-values.md#set-values).
