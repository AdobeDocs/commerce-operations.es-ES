---
title: Configuración de un trabajo cron personalizado y de un grupo cron (tutorial)
description: Utilice este tutorial paso a paso para crear un trabajo cron personalizado.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---


# Configuración de un trabajo cron personalizado

Este tutorial paso a paso muestra cómo crear un trabajo cron personalizado y, opcionalmente, un grupo cron en un módulo de muestra. Puede utilizar un módulo que ya tenga o puede utilizar un módulo de muestra de nuestra [`magento2-samples` repositorio][samples].

La ejecución del trabajo cron hace que se agregue una fila al `cron_schedule` tabla con el nombre del trabajo cron, `custom_cron`.

También le mostramos cómo crear opcionalmente un grupo cron, que puede utilizar para ejecutar trabajos cron personalizados con configuraciones que no sean las predeterminadas de la aplicación Commerce.

En este tutorial, se asume lo siguiente:

- La aplicación Commerce está instalada en `/var/www/html/magento2`
- El nombre de usuario y la contraseña de la base de datos de Commerce son los dos `magento`
- Todas las acciones se realizan como [propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)

## Paso 1: Obtener un módulo de muestra

Para configurar un trabajo cron personalizado, necesita un módulo de muestra. Sugerimos que `magento-module-minimal` módulo.

Si ya tiene un módulo de muestra, puede utilizarlo; omita este paso y el siguiente y continúe con el paso 3: Cree una clase para ejecutar cron.

**Para obtener un módulo de muestra**:

1. Inicie sesión en el servidor de Commerce como, o cambie a [propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Cambie a un directorio que no esté en la raíz de la aplicación Commerce (por ejemplo, su directorio principal).
1. Clonar el [`magento2-samples` repositorio][samples].

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   Si el comando falla con el error `Permission denied (publickey).`, debe [añada su clave pública SSH a GitHub.com][git-ssh].

1. Cree un directorio en el que copiar el código de ejemplo:

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. Copie el código del módulo de muestra:

   ```bash
   cp -r ~/magento2-samples/sample-module-minimal/* /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. Compruebe los archivos copiados correctamente:

   ```bash
   ls -al /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

   Debería ver el siguiente resultado:

   ```terminal
   drwxrwsr-x.   4 magento_user apache  4096 Oct 30 13:19 .
   drwxrwsr-x. 121 magento_user apache  4096 Oct 30 13:19 ..
   -rw-rw-r--.   1 magento_user apache   372 Oct 30 13:19 composer.json
   drwxrwsr-x.   2 magento_user apache  4096 Oct 30 13:19 etc
   -rw-rw-r--.   1 magento_user apache 10376 Oct 30 13:19 LICENSE_AFL.txt
   -rw-rw-r--.   1 magento_user apache 10364 Oct 30 13:19 LICENSE.txt
   -rw-rw-r--.   1 magento_user apache  1157 Oct 30 13:19 README.md
   -rw-rw-r--.   1 magento_user apache   270 Oct 30 13:19 registration.php
   drwxrwsr-x.   3 magento_user apache  4096 Oct 30 13:19 Test
   ```

1. Actualice la base de datos y el esquema de Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpie la caché:

   ```bash
   bin/magento cache:clean
   ```

## Paso 2: Compruebe el módulo de muestra

Antes de continuar, compruebe que el módulo de muestra esté registrado y habilitado.

1. Ejecute el siguiente comando:

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. Asegúrese de que el módulo esté habilitado.

   ```terminal
   Module is enabled
   ```

>[!TIP]
>
>Si la salida indica que la variable `Module does not exist`, revisar [Paso 1](#step-1-get-a-sample-module) cuidadosamente. Asegúrese de que el código se encuentra en el directorio correcto. La ortografía y el caso son importantes; si algo es diferente, el módulo no se cargará. Además, no olvide ejecutar `magento setup:upgrade`.

## Paso 3: Crear una clase para ejecutar cron

Este paso muestra una clase simple para crear un trabajo cron. La clase solo escribe una fila en la variable `cron_schedule` que confirma que se ha configurado correctamente.

Para crear una clase:

1. Cree un directorio para la clase y cambie a ese directorio:

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. Creación de un archivo con el nombre `Test.php` en ese directorio con el siguiente contenido:

   ```php
   <?php
   namespace Magento\SampleMinimal\Cron;
   
   use Psr\Log\LoggerInterface;
   
   class Test {
       protected $logger;
   
       public function __construct(LoggerInterface $logger) {
           $this->logger = $logger;
       }
   
      /**
       * Write to system.log
       *
       * @return void
       */
       public function execute() {
           $this->logger->info('Cron Works');
       }
   }
   ```

## Paso 4: Crear `crontab.xml`

La variable `crontab.xml` establece una programación para ejecutar el código cron personalizado.

Crear `crontab.xml` de la siguiente manera en la sección `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` directorio:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

El anterior `crontab.xml` ejecuta el `Magento/SampleMinimal/Cron/Test.php` una vez por minuto, lo que da como resultado que se añada una fila a la `cron_schedule` tabla.

Para que la programación cron se pueda configurar desde Admin, utilice la ruta de configuración del campo de configuración del sistema.

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <config_path>system/config/path</config_path>
        </job>
    </group>
</config>
```

Donde, `system/config/path` es una ruta de configuración del sistema definida en `etc/adminhtml/system.xml` de un módulo.

## Paso 5: Compilar y limpiar la caché

Compile el código con este comando:

```bash
bin/magento setup:di:compile
```

Y limpie la caché con este comando:

```bash
bin/magento cache:clean
```

## Paso 6: Verificar el trabajo cron

Este paso muestra cómo verificar correctamente el trabajo cron personalizado utilizando una consulta SQL en la variable `cron_schedule` tabla de base de datos.

Para verificar cron:

1. Ejecutar trabajos cron de Commerce:

   ```bash
   bin/magento cron:run
   ```

1. Introduzca la variable `magento cron:run` dos o tres veces.

   La primera vez que introduzca el comando, pondrá en cola los trabajos; posteriormente, se ejecutan los trabajos cron. Debe introducir el comando _al menos_ dos veces.

1. Ejecutar la consulta SQL `SELECT * from cron_schedule WHERE job_code like '%custom%'` de la siguiente manera:

   1. Entrar `mysql -u magento -p`
   1. En el `mysql>` solicitud, introduzca `use magento;`
   1. Entrar `SELECT * from cron_schedule WHERE job_code like '%custom%';`

      El resultado debe ser similar al siguiente:

      ```terminal
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. (Opcional) Compruebe que los mensajes están escritos en el registro del sistema de Commerce:

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   Debería ver una o más entradas como las siguientes:

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   Estos mensajes provienen de la variable `execute` método en `Test.php`:

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

Si el comando SQL y el registro del sistema no contienen entradas, ejecute el `magento cron:run` un par de veces más y esperar. La base de datos puede tardar algún tiempo en actualizarse.

## Paso 7 (opcional): Configuración de un grupo cron personalizado

Este paso muestra cómo configurar opcionalmente un grupo cron personalizado. Debe configurar un grupo cron personalizado si desea que su trabajo cron personalizado se ejecute en una programación diferente a la de otros trabajos cron (normalmente, una vez por minuto) o si desea que varios trabajos cron personalizados se ejecuten con una configuración diferente.

Para configurar un grupo cron personalizado:

1. Apertura `crontab.xml` en un editor de texto.
1. Cambiar `<group id="default">` a `<group id="custom_crongroup">`
1. Salga del editor de texto.
1. Crear `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` con el siguiente contenido:

   ```xml
   <?xml version="1.0"?>
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
       <group id="custom_crongroup">
           <schedule_generate_every>1</schedule_generate_every>
           <schedule_ahead_for>4</schedule_ahead_for>
           <schedule_lifetime>2</schedule_lifetime>
           <history_cleanup_every>10</history_cleanup_every>
           <history_success_lifetime>60</history_success_lifetime>
           <history_failure_lifetime>600</history_failure_lifetime>
           <use_separate_process>1</use_separate_process>
       </group>
   </config>
   ```

Para obtener una descripción del significado de las opciones, consulte [Personalización de la referencia de crons](custom-cron-reference.md).

## Paso 8: Verificar el grupo cron personalizado

Esta _opcional_ muestra cómo verificar el grupo cron personalizado mediante el administrador.

Para verificar el grupo de cron personalizado:

1. Ejecute trabajos de Commerce cron para su grupo personalizado:

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   Ejecute el comando al menos dos veces.

1. Limpie la caché:

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. Inicie sesión en Admin como administrador.
1. Haga clic en **Almacenes** > **Configuración** > **Configuración** > **Avanzadas** > **Sistema**.
1. En el panel derecho, expanda **Cron**.

   El grupo cron se muestra de la siguiente manera:

   ![Su grupo de cron personalizado](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
