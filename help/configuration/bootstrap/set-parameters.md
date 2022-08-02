---
title: Establezca el valor de los parámetros de arranque
description: Aprenda a configurar los parámetros de arranque para la aplicación Commerce.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 1%

---


# parámetros de Bootstrap

En este tema se explica cómo configurar los valores de los parámetros de arranque de la aplicación Commerce. Consulte [Descripción general de la inicialización y arranque de la aplicación](initialization.md).

La siguiente tabla describe los parámetros de arranque que puede establecer:

| parámetro de Bootstrap | Descripción |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | Especifica rutas de URL y directorios personalizados |
| MAGE_PROFILER | Permite la creación de perfiles de HTML y gráficos de dependencias |

>[!INFO]
>
>- No todos los parámetros de arranque están documentados.
>- Ahora, establece el modo de aplicación (desarrollador, predeterminado, producción) utilizando la variable [`magento deploy:mode:set {mode}`](../cli/set-mode.md) comando.


## Configuración de parámetros mediante una variable de entorno

En esta sección se explica cómo configurar los valores de los parámetros de arranque mediante variables de entorno.

### Definir el modo de aplicación

Puede especificar variables de arranque como variables de entorno de todo el sistema, lo que permite que todos los procesos las utilicen.

Por ejemplo, puede usar la variable `MAGE_PROFILER` variable de entorno del sistema para especificar un modo como se indica a continuación:

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

Configure la variable utilizando un comando específico del shell. Dado que los contenedores tienen una sintaxis diferente, consulte una referencia como [unix.stackexchange.com][unix-stackx].

Ejemplo de shell de Bash para CentOS:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Si `PHP Fatal error` se muestra en el explorador después de establecer un valor de perfil, reinicie el servidor web. La razón puede estar relacionada con el almacenamiento en caché de bytecode de PHP, que almacena en caché bytecodes y rutas de clases de PHP.

## Configuración de parámetros para Apache o Nginx

En esta sección se explica cómo especificar el modo para Apache o Nginx.

### Configuración de Nginx

Consulte la [Configuración de muestra de Nginx] en _GitHub_.

### Configuración de Apache .htaccess

Una forma de establecer el modo de aplicación es editando `.htaccess`. De este modo, no es necesario cambiar la configuración de Apache.

Puede modificar `.htaccess` en cualquiera de las ubicaciones siguientes, según el punto de entrada a la aplicación Commerce:

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**Para configurar una variable**:

1. Abra cualquiera de los archivos anteriores en un editor de texto y añada o quite el comentario de la configuración deseada.

   Por ejemplo, para especificar un [mode](application-modes.md), quite la marca de comentario siguiente:

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Establezca el valor de `MAGE_PROFILER` a cualquiera de los siguientes:

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. Guarde los cambios en `.htaccess`; no es necesario reiniciar Apache para que el cambio surta efecto.

### Configuración de Apache

El servidor web Apache admite la configuración del modo de aplicación mediante `mod_env` directivas.

El Apache `mod_env` directiva es ligeramente diferente en [Apache versión 2.2] y [Apache versión 2.4].

Los siguientes procedimientos muestran cómo configurar el modo de aplicación en un host virtual Apache. Esta no es la única manera de usar `mod_env` directivas; consulte la documentación de Apache para obtener más información.

>[!TIP]
>
>La siguiente sección supone que ya ha configurado su host virtual. Si no lo ha hecho, consulte un recurso como [este tutorial de DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Para especificar una variable de arranque para Apache en Ubuntu**:

1. Como usuario con `root` privilegios, abra el archivo de configuración de host virtual en un editor de texto.

   Por ejemplo, si el host virtual tiene el nombre `my.magento`,

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. En cualquier parte de la configuración del host virtual, agregue la línea siguiente:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Por ejemplo,

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Guarde los cambios y salga del editor de texto.
1. Habilite su host virtual si aún no lo ha hecho:

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
>Esta sección supone que ya ha configurado el host virtual. Si no lo ha hecho, consulte un recurso como [este tutorial de DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**Para especificar una variable de arranque para Apache en CentOS**:

1. Como usuario con `root` privilegios, abrir `/etc/httpd/conf/httpd.conf` en un editor de texto.

1. En cualquier parte de la configuración del host virtual, agregue la línea siguiente:

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

[Apache versión 2.2]: http://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache versión 2.4]: http://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Configuración de muestra de Nginx]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: http://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
