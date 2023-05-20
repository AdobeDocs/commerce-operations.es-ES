---
title: Secure cron PHP
description: Restrinja quién puede ejecutar el archivo cron.php en un explorador.
exl-id: c81fcab2-1ee3-4ec7-a300-0a416db98614
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 0%

---

# Secure cron PHP

En este tema se explica la seguridad `pub/cron.php` para evitar que se utilice en un ataque malicioso. Si no protege cron, cualquier usuario podría ejecutar cron potencialmente para atacar su aplicación de Commerce.

El trabajo cron ejecuta varias tareas programadas y es una parte vital de la configuración de Commerce. Las tareas programadas incluyen, entre otras:

- Reindexación
- Generación de correos electrónicos
- Generando boletines
- Generando mapas del sitio

>[!INFO]
>
>Consulte [Configurar y ejecutar cron](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) para obtener más información sobre los grupos cron.

Puede ejecutar un trabajo cron de las siguientes maneras:

- Uso del [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) comando desde la línea de comandos o en un crontab
- Acceso `pub/cron.php?[group=<name>]` en un explorador web

>[!INFO]
>
>No es necesario que haga nada si usa el [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) para ejecutar cron porque utiliza un proceso diferente que ya es seguro.

## CRON seguro con Apache

En esta sección se explica cómo proteger cron mediante la autenticación HTTP Basic con Apache. Estas instrucciones se basan en Apache 2.2 con CentOS 6. Para obtener más información, consulte uno de los siguientes recursos:

- [Tutorial de autenticación y autorización de Apache 2.2](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [Tutorial de autenticación y autorización de Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

### Crear un archivo de contraseña

Por motivos de seguridad, puede localizar el archivo de contraseña en cualquier lugar excepto en el servidor web docroot. En este ejemplo, almacenamos el archivo de contraseña en un nuevo directorio.

Introduzca los siguientes comandos como usuario con `root` privilegios:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

Donde `<username>` puede ser el usuario del servidor web u otro usuario. En este ejemplo, utilizamos el usuario del servidor web, pero la elección del usuario depende de usted.

Siga las indicaciones de la pantalla para crear una contraseña de usuario.

Para agregar otro usuario al archivo de contraseñas, escriba el siguiente comando como usuario con `root` privilegios:

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### Agregar usuarios para crear un grupo cron autorizado (opcional)

Puede permitir que más de un usuario ejecute cron agregando estos usuarios a su archivo de contraseñas, incluido un archivo de grupo.

Para agregar otro usuario al archivo de contraseñas:

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

Para crear un grupo autorizado, cree un archivo de grupo en cualquier lugar fuera del docroot del servidor web. El archivo de grupo especifica el nombre del grupo y los usuarios del grupo. En este ejemplo, el nombre del grupo es `MagentoCronGroup`.

```bash
vim /usr/local/apache/password/group
```

Contenido del archivo:

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### Asegurar cron en `.htaccess`

Para proteger cron en `.htaccess` archivo:

1. Inicie sesión en el servidor de Commerce como propietario del sistema de archivos o cambie a.
1. Abrir `<magento_root>/pub/.htaccess` en un editor de texto.

   (Porque `cron.php` se encuentra en la `pub` directorio, editar esto `.htaccess` sólo.)

1. _Acceso de Cron para uno o más usuarios._ Reemplazar el existente `<Files cron.php>` con lo siguiente:

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. _Acceso de Cron para un grupo._ Reemplazar el existente `<Files cron.php>` con lo siguiente:

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. Guardar los cambios en `.htaccess` y salga del editor de texto.
1. Continuar con [Verifique que cron sea seguro](#verify-cron-is-secure).

## CRON seguro con Nginx

En esta sección se explica cómo proteger cron mediante el servidor web Nginx. Debe realizar las siguientes tareas:

1. Configuración de un archivo de contraseña cifrado para Nginx
1. Modifique la configuración de nginx para hacer referencia al archivo de contraseña al acceder a `pub/cron.php`

### Crear un archivo de contraseña

Consulte uno de los siguientes recursos para crear un archivo de contraseña antes de continuar:

- [Cómo configurar la autenticación de contraseña con Nginx en Ubuntu 14.04 (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [Autenticación HTTP básica con Nginx (howtoforge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### Asegurar cron en `nginx.conf.sample`

Commerce proporciona un archivo de configuración de nginx de muestra optimizado de forma predeterminada. Se recomienda modificarla para proteger cron.

1. Añada lo siguiente a su [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) archivo:

   ```conf
   #Securing cron
   location ~ cron\.php$ {
      auth_basic "Cron Authentication";
      auth_basic_user_file /etc/nginx/.htpasswd;
   
      try_files $uri =404;
      fastcgi_pass   fastcgi_backend;
      fastcgi_buffers 1024 4k;
   
      fastcgi_read_timeout 600s;
      fastcgi_connect_timeout 600s;
   
      fastcgi_index  index.php;
      fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
      include        fastcgi_params;
   }
   ```

1.Restart nginx:

```bash
systemctl restart nginx
```

1. Continuar con [Verifique que cron sea seguro](#verify-cron-is-secure).

## Verifique que cron sea seguro

La forma más sencilla de comprobar que `pub/cron.php` es seguro para comprobar que está creando filas en el `cron_schedule` tabla de la base de datos después de configurar la autenticación por contraseña. Este ejemplo utiliza comandos SQL para comprobar la base de datos, pero puede utilizar la herramienta que desee.

>[!INFO]
>
>El `default` cron que está ejecutando en este ejemplo se ejecuta según la programación definida en `crontab.xml`. Algunos trabajos de cron se ejecutan solo una vez al día. La primera vez que ejecute cron desde el explorador, la variable `cron_schedule` se actualiza, pero la siguiente `pub/cron.php` Las solicitudes de se ejecutan según la programación configurada.

**Para comprobar que cron es seguro**:

1. Inicie sesión en la base de datos como usuario de la base de datos de Commerce o como `root`.

   Por ejemplo,

   ```bash
   mysql -u magento -p
   ```

1. Utilice la base de datos de Commerce:

   ```shell
   use <database-name>;
   ```

   Por ejemplo,

   ```shell
   use magento;
   ```

1. Elimine todas las filas del `cron_schedule` tabla de base de datos:

   ```shell
   TRUNCATE TABLE cron_schedule;
   ```

1. Ejecute cron desde un explorador:

   ```shell
   http[s]://<Commerce hostname or ip>/cron.php?group=default
   ```

   Por ejemplo:

   ```shell
   http://magento.example.com/cron.php?group=default
   ```

1. Cuando se le solicite, introduzca el nombre y la contraseña de un usuario autorizado. La siguiente figura muestra un ejemplo.

   ![Autorizar cron mediante HTTP Basic](../../assets/configuration/cron-auth.png)

1. Compruebe que se han agregado filas a la tabla:

   ```shell
   SELECT * from cron_schedule;
   
   mysql> SELECT * from cron_schedule;
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   | schedule_id | job_code                             | status  | messages | created_at        | scheduled_at      | executed_at | finished_at |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   |         1 | catalog_product_outdated_price_values_cleanup | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         2 | sales_grid_order_async_insert             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         3 | sales_grid_order_invoice_async_insert       | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         4 | sales_grid_order_shipment_async_insert      | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         5 | sales_grid_order_creditmemo_async_insert     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         6 | sales_send_order_emails                  | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         7 | sales_send_order_invoice_emails            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         8 | sales_send_order_shipment_emails           | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         9 | sales_send_order_creditmemo_emails         | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        10 | newsletter_send_all                     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:25:00 | NULL      | NULL      |
   |        11 | captcha_delete_old_attempts               | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        12 | captcha_delete_expired_images             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        13 | outdated_authentication_failures_cleanup     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        14 | magento_newrelicreporting_cron            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   14 rows in set (0.00 sec)
   ```

## Ejecute cron desde un explorador web

Puede ejecutar cron en cualquier momento, como durante el desarrollo, utilizando un explorador web.

>[!WARNING]
>
>Hacer _no_ ejecute cron en un explorador sin protegerlo primero.

Si utiliza un servidor web Apache, debe eliminar la restricción de `.htaccess` antes de ejecutar cron en un explorador:

1. Inicie sesión en el servidor de Commerce como un usuario con permisos para escribir en el sistema de archivos de Commerce.
1. Abra cualquiera de las siguientes opciones en un editor de texto (según el punto de entrada al Magento):

   ```text
   <magento_root>/pub/.htaccess
   <magento_root>/.htaccess
   ```

1. Elimine o comente lo siguiente:

   ```conf
   ## Deny access to cron.php
     <Files cron.php>
        order allow,deny
        deny from all
     </Files>
   ```

   Por ejemplo,

   ```conf
   ## Deny access to cron.php
      #<Files cron.php>
         # order allow,deny
         # deny from all
      #</Files>
   ```

1. Guarde los cambios y salga del editor de texto.

   A continuación, puede ejecutar cron en un explorador web de la siguiente manera:

   ```text
   <your hostname or IP>/<Commerce root>/pub/cron.php[?group=<group name>]
   ```

Donde:

- `<your hostname or IP>` es el nombre de host o la dirección IP de su instalación de Commerce
- `<Commerce root>` es el directorio docroot-relativo al servidor web en el que instaló el software Commerce

   La dirección URL exacta que utilice para ejecutar la aplicación Commerce depende de cómo haya configurado el servidor web y el host virtual.

- `<group name>` es cualquier nombre de grupo cron válido (opcional)

Por ejemplo,

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>Debe ejecutar cron dos veces: primero para descubrir tareas que ejecutar y de nuevo para ejecutar las tareas por sí mismas. Consulte [Configurar y ejecutar cron](../cli/configure-cron-jobs.md) para obtener más información sobre los grupos cron.
