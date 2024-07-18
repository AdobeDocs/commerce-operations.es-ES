---
title: Establecer el valor de los parámetros de arranque
description: Obtenga información sobre cómo establecer parámetros de bootstrap para la aplicación de Commerce.
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 1%

---

# Parámetros de Bootstrap

En este tema se muestra cómo establecer los valores de los parámetros de arranque de la aplicación Commerce. Consulte [Información general sobre inicialización y arranque de la aplicación](initialization.md).

En la tabla siguiente se describen los parámetros de bootstrap que puede establecer:

| Parámetro de Bootstrap | Descripción |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | Especifica rutas de directorio y URL personalizadas |
| MAGE_PROFILER | Habilita los gráficos de dependencias y la creación de perfiles de HTML |

>[!INFO]
>
>- No todos los parámetros de arranque están documentados.
>- Ahora puede establecer el modo de aplicación (desarrollador, predeterminado, producción) mediante el comando [`magento deploy:mode:set {mode}`](../cli/set-mode.md).

## Definición de parámetros mediante una variable de entorno

En esta sección se explica cómo establecer los valores de los parámetros de bootstrap usando variables de entorno.

### Establecer el modo de aplicación

Puede especificar variables de bootstrap como variables de entorno de todo el sistema, lo que permite que todos los procesos las utilicen.

Por ejemplo, puede usar la variable de entorno del sistema `MAGE_PROFILER` para especificar un modo de la siguiente manera:

```
MAGE_PROFILER={firebug|csv|<custom value>}
```

Configure la variable mediante un comando específico del shell. Como los shells tienen sintaxis diferente, consulte una referencia como [unix.stackexchange.com][unix-stackx].

Ejemplo de shell de Bash para CentOS:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Si aparece `PHP Fatal error` en el explorador después de establecer un valor de generador de perfiles, reinicie el servidor web. La razón podría estar relacionada con el almacenamiento en caché de código de bytes PHP, que almacena en caché códigos de bytes y rutas de clases PHP.

## Definir parámetros para Apache o Nginx

En esta sección se explica cómo especificar el modo para Apache o Nginx.

### Configuración de Nginx

Ver la [configuración de muestra de Nginx] en _GitHub_.

### Configuración de Apache .htaccess

Una forma de establecer el modo de aplicación es editar `.htaccess`. De este modo, no tiene que cambiar la configuración de Apache.

Puede modificar `.htaccess` en cualquiera de las siguientes ubicaciones, según el punto de entrada a la aplicación de Commerce:

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**Para establecer una variable**:

1. Abra cualquiera de los archivos anteriores en un editor de texto y agregue o quite los comentarios de la configuración deseada.

   Por ejemplo, para especificar un [modo](application-modes.md), quite el comentario de lo siguiente:

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Establezca el valor de `MAGE_PROFILER` en cualquiera de las siguientes opciones:

   ```
   firebug
   csvfile
   <custom value>
   ```

1. Guarde los cambios en `.htaccess`; no es necesario reiniciar Apache para que el cambio surta efecto.

### Configuración de Apache

El servidor web Apache admite la configuración del modo de aplicación mediante directivas `mod_env`.

La directiva Apache `mod_env` es ligeramente diferente en [Apache versión 2.2] y [Apache versión 2.4].

Los procedimientos siguientes muestran cómo establecer el modo de aplicación en un host virtual Apache. Esta no es la única manera de usar directivas de `mod_env`; consulte la documentación de Apache para obtener detalles.

>[!TIP]
>
>En la siguiente sección se da por hecho que ya ha configurado el host virtual. Si no, consulte un recurso como [este tutorial de DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Para especificar una variable de arranque para Apache en Ubuntu**:

1. Como usuario con privilegios de `root`, abra el archivo de configuración de host virtual en un editor de texto.

   Por ejemplo, si el host virtual se llama `my.magento`,

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. En cualquier lugar de la configuración del host virtual, agregue la siguiente línea:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Por ejemplo,

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Guarde los cambios y salga del editor de texto.
1. Habilite el host virtual si aún no lo ha hecho:

   ```bash
   a2ensite <virtual host config file name>
   ```

   Por ejemplo,

   ```bash
   a2ensite my.magento.conf
   ```

1. Después de configurar el modo, reinicie el servidor web:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>En esta sección se da por hecho que ya ha configurado el host virtual. Si no, consulte un recurso como [este tutorial de DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**Para especificar una variable de bootstrap para Apache en CentOS**:

1. Como usuario con privilegios de `root`, abra `/etc/httpd/conf/httpd.conf` en un editor de texto.

1. En cualquier lugar de la configuración del host virtual, agregue la siguiente línea:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Por ejemplo,

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Guarde los cambios y salga del editor de texto.

1. Después de configurar el modo, reinicie el servidor web:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache versión 2.2]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache versión 2.4]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Configuración de muestra de Nginx]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
