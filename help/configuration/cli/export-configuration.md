---
title: Exportar ajustes de configuración
description: Exporte los ajustes de configuración de Adobe Commerce a los archivos de configuración, también conocidos como volcado de configuración.
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Exportar ajustes de configuración

En Commerce 2.2 y versiones posteriores de [modelo de implementación de canalización](../deployment/technical-details.md), puede mantener una configuración coherente en todos los sistemas. Después de configurar las opciones en el Administrador del sistema de desarrollo, exporte dichas opciones a los archivos de configuración mediante el siguiente comando:

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ es una lista de tipos de configuración que se van a volcar separados por espacios. Los tipos disponibles incluyen `scopes`, `system`, `themes` y `i18n`. Si no se especifica ningún tipo de configuración, el comando elimina toda la información de configuración del sistema.

El siguiente ejemplo volca ámbitos y temas únicamente:

```bash
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

Los valores de configuración se especifican como confidenciales o específicos del sistema haciendo referencia a [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) en el archivo [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) del módulo.

Para exportar la configuración adicional del sistema al usar `config_types`, considere la posibilidad de usar el comando [`bin/magento config:set`](set-configuration-values.md#set-values).
