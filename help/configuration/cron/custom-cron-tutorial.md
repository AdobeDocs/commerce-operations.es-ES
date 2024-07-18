---
title: Configuración de un trabajo cron personalizado y un grupo cron (tutorial)
description: Utilice este tutorial paso a paso para crear un trabajo cron personalizado.
exl-id: d8efcafc-3ae1-4c2d-a8ad-4a806fb48932
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 0%

---

# Configuración de un trabajo cron personalizado

Este tutorial paso a paso muestra cómo crear un trabajo cron personalizado y, opcionalmente, un grupo cron en un módulo de muestra. Puede usar un módulo que ya tiene o puede usar un módulo de ejemplo de nuestro repositorio [`magento2-samples`][samples].

La ejecución del trabajo cron hace que se agregue una fila a la tabla `cron_schedule` con el nombre del trabajo cron `custom_cron`.

También le mostramos cómo crear opcionalmente un grupo cron, que puede utilizar para ejecutar trabajos cron personalizados con configuraciones distintas a los valores predeterminados de la aplicación Commerce.

En este tutorial, suponemos lo siguiente:

- La aplicación Commerce está instalada en `/var/www/html/magento2`
- Su nombre de usuario y contraseña de la base de datos de Commerce son `magento`
- Realiza todas las acciones como [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md)

## Paso 1: Obtener un módulo de muestra

Para configurar un trabajo cron personalizado, necesita un módulo de ejemplo. Sugerimos el módulo `magento-module-minimal`.

Si ya tiene un módulo de ejemplo, puede utilizarlo; omita este paso y el siguiente y continúe con el Paso 3: Crear una clase para ejecutar cron.

**Para obtener un módulo de ejemplo**:

1. Inicie sesión en el servidor de Commerce como [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md) o cambie a él.
1. Cambie a un directorio que no esté en la raíz de la aplicación de Commerce (por ejemplo, el directorio principal).
1. Clonar el repositorio [`magento2-samples` ][samples].

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   Si el comando falla con el error `Permission denied (publickey).`, debe [agregar su clave pública SSH a GitHub.com][git-ssh].

1. Cree un directorio en el que copiar el código de ejemplo:

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. Copie el código del módulo de ejemplo:

   ```bash
   cp -r ~/magento2-samples/sample-module-minimal/* /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. Compruebe que los archivos se han copiado correctamente:

   ```bash
   ls -al /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

   Debería ver el siguiente resultado:

   ```
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

## Paso 2: Verificar el módulo de ejemplo

Antes de continuar, compruebe que el módulo de ejemplo esté registrado y habilitado.

1. Ejecute el siguiente comando:

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. Asegúrese de que el módulo esté activado.

   ```
   Module is enabled
   ```

>[!TIP]
>
>Si el resultado indica que `Module does not exist`, revise [el paso 1](#step-1-get-a-sample-module) con cuidado. Asegúrese de que el código esté en el directorio correcto. La ortografía y el caso son importantes; si algo es diferente, el módulo no se cargará. Además, no olvide ejecutar `magento setup:upgrade`.

## Paso 3: Crear una clase para ejecutar cron

Este paso muestra una clase simple para crear un trabajo cron. La clase solo escribe una fila en la tabla `cron_schedule` que confirma que se ha configurado correctamente.

Para crear una clase:

1. Cree un directorio para la clase y cambie a ese directorio:

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. Se creó un archivo con el nombre `Test.php` en ese directorio con el siguiente contenido:

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

El archivo `crontab.xml` establece una programación para ejecutar el código personalizado cron.

Cree `crontab.xml` como se indica a continuación en el directorio `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc`:

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

El `crontab.xml` anterior ejecuta la clase `Magento/SampleMinimal/Cron/Test.php` una vez por minuto, lo que da como resultado que se agregue una fila a la tabla `cron_schedule`.

Para que la programación de cron se pueda configurar desde el administrador, utilice la ruta de configuración del campo de configuración del sistema.

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

Donde, `system/config/path` es una ruta de acceso de configuración del sistema definida en `etc/adminhtml/system.xml` de un módulo.

## Paso 5: Compilar y limpiar la caché

Compile el código con este comando:

```bash
bin/magento setup:di:compile
```

Y limpie la caché con este comando:

```bash
bin/magento cache:clean
```

## Paso 6: Verificar el trabajo de cron

Este paso muestra cómo comprobar correctamente el trabajo cron personalizado mediante una consulta SQL en la tabla de base de datos `cron_schedule`.

Para verificar cron:

1. Ejecutar trabajos cron de Commerce:

   ```bash
   bin/magento cron:run
   ```

1. Escriba el comando `magento cron:run` dos o tres veces.

   La primera vez que se introduce el comando, se ponen en cola los trabajos; posteriormente, se ejecutan los trabajos cron. Debe escribir el comando _al menos_ dos veces.

1. Ejecute la consulta SQL `SELECT * from cron_schedule WHERE job_code like '%custom%'` de la siguiente manera:

   1. Ingresar `mysql -u magento -p`
   1. En el `mysql>`, escriba `use magento;`
   1. Ingresar `SELECT * from cron_schedule WHERE job_code like '%custom%';`

      El resultado debe ser similar al siguiente:

      ```
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. (Opcional) Compruebe que los mensajes se escriben en el registro del sistema de Commerce:

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   Debería ver una o más entradas como la siguiente:

   ```
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   Estos mensajes provienen del método `execute` en `Test.php`:

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

Si el comando SQL y el registro del sistema no contienen ninguna entrada, ejecute el comando `magento cron:run` varias veces más y espere. La base de datos puede tardar algún tiempo en actualizarse.

## Paso 7 (opcional): Configurar un grupo cron personalizado

Este paso muestra cómo configurar opcionalmente un grupo cron personalizado. Debe configurar un grupo cron personalizado si desea que el trabajo cron personalizado se ejecute en una programación diferente a otras tareas cron (normalmente, una vez por minuto) o si desea que varios trabajos cron personalizados se ejecuten con configuraciones diferentes.

Para configurar un grupo cron personalizado:

1. Abra `crontab.xml` en un editor de texto.
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

## Paso 8: Verificar su grupo personalizado de cron

Este paso _opcional_ muestra cómo comprobar el grupo cron personalizado mediante el administrador.

Para verificar su grupo cron personalizado:

1. Ejecute trabajos cron de Commerce para su grupo personalizado:

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   Ejecute el comando al menos dos veces.

1. Limpie la caché:

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. Inicie sesión en el administrador como administrador.
1. Haga clic en **Tiendas** > **Configuración** > **Configuración** > **Avanzado** > **Sistema**.
1. En el panel derecho, expanda **Cron**.

   El grupo de cron se muestra de la siguiente manera:

   ![Su grupo cron personalizado](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
