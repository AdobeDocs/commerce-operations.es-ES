---
title: Exportar ajustes de configuración
description: Exporte los ajustes de configuración de Adobe Commerce a archivos de configuración, también conocidos como volcado de configuración.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# Exportar ajustes de configuración

En Commerce 2.2 y posterior [modelo de implementación de canalización](../deployment/technical-details.md), puede mantener una configuración coherente en todos los sistemas. Después de configurar las opciones de Administración en el sistema de desarrollo, exporte esas opciones a los archivos de configuración mediante el siguiente comando:

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ es una lista de tipos de configuración separados por espacios que se van a volcar. Los tipos disponibles incluyen `scopes`, `system`, `themes`y `i18n`. Si no se especifica ningún tipo de configuración, el comando volcará toda la información de configuración del sistema.

En el siguiente ejemplo se muestran solo ámbitos y temas:

```bash
bin/magento app:config:dump scopes themes
```

Como resultado de la ejecución del comando, se actualizan los siguientes archivos de configuración:

- `app/etc/config.php`

   Este es el archivo de configuración compartido para todas las instancias de Commerce.
Incluya esto en el control de código fuente para que se pueda compartir entre los sistemas de desarrollo, compilación y producción.

   Consulte [Referencia config.php](../reference/config-reference-configphp.md).

- `app/etc/env.php`

   Este es el archivo de configuración específico del entorno.
Contiene configuraciones sensibles y específicas del sistema para entornos individuales.

   Do _not_ incluya este archivo en el control de código fuente.

   Consulte [referencia env.php](../reference/config-reference-envphp.md).

## Ajustes confidenciales o específicos del sistema

Para establecer la configuración confidencial escrita en `env.php`, use el [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) comando.

Los valores de configuración se especifican como confidenciales o específicos del sistema haciendo referencia a [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) en el [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) archivo.

Para exportar configuraciones del sistema adicionales al usar `config_types`, considere usar la variable [`bin/magento config:set`](set-configuration-values.md#set-values) comando.
