---
title: Guía de instalación
description: Utilice esta guía para instalar [!DNL Site-Wide Analysis Tool] para su sitio web
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: 163d12b1f30a3098932c62e11f24784422002c67
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 0%

---

# Guía de instalación

El [!DNL Site-Wide Analysis Tool] proporciona monitorización del rendimiento, informes y recomendaciones en tiempo real las 24 horas del día, los 7 días de la semana, para garantizar la seguridad y la operabilidad de Adobe Commerce en las instalaciones de infraestructura en la nube. También proporciona información detallada sobre los parches disponibles e instalados, las extensiones de terceros y la instalación de Adobe Commerce.

>[!INFO]
>
>Aprender [cómo habilitar](../site-wide-analysis-tool/access.md) el [!DNL Site-Wide Analysis Tool] y generar informes.

Si tiene una instalación local de Adobe Commerce, instale un agente en su infraestructura para utilizar la herramienta. No es necesario instalar el agente en Adobe Commerce en proyectos de infraestructura en la nube.

## Agente

El [!DNL Site-Wide Analysis Tool] El agente le permite utilizar el [!DNL Site-Wide Analysis Tool] para instalaciones locales de Adobe Commerce.

El [!DNL Site-Wide Analysis Tool] El agente recopila datos empresariales y de aplicaciones, los analiza y proporciona información adicional sobre el estado de la instalación para que pueda mejorar la experiencia del cliente. Supervisa la aplicación y le ayuda a identificar problemas de rendimiento, seguridad, disponibilidad y aplicaciones.

La instalación del agente requiere los siguientes pasos:

1. Compruebe los requisitos del sistema.

1. Configure las claves API en [!UICONTROL Commerce Services Connector] extensión.

1. Instale el agente.

1. Ejecute el agente.

>[!INFO]
>
>El agente admite instalaciones de Adobe Commerce de varios nodos. Instale y configure el agente en cada nodo.

## Requisitos del sistema

Su infraestructura local debe cumplir los siguientes requisitos antes de instalar el agente:

- Sistemas operativos

   - [!DNL Linux x86-64] distribuciones, como [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian], y similares

  >[!IMPORTANT]
  >
  >Adobe Commerce no es compatible con [!DNL Microsoft Windows] o [!DNL macOS].

- Adobe Commerce 2.4.5-p1 o posterior (debido a la dependencia del conector de servicio)

- [!DNL Commerce Services Connector extension]

- CLI DE PHP

- Utilidades de Bash/Shell

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

El agente requiere lo siguiente [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) extensión que se va a instalar en el sistema y [configurado](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) con claves API. Para comprobar que la extensión está instalada, ejecute el siguiente comando:

```bash
bin/magento module:status Magento_ServicesId
```

Si ha instalado la extensión de y la ha configurado con una clave de API existente para un servicio diferente, debe **DEBE regenerar la clave de API** y actualícelo en el Administrador de Adobe Commerce para el agente.

1. Coloque el sitio web en [modo de mantenimiento](../../installation/tutorials/maintenance-mode.md).

1. Iniciar sesión en [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > Si tiene problemas para acceder a su cuenta, consulte [No se puede iniciar sesión en la asistencia de Adobe Commerce o en la cuenta de la nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) para obtener ayuda sobre solución de problemas.

1. Haga clic **[!UICONTROL API Portal]**.

1. Clic **[!UICONTROL Delete]** junto a la clave de API existente.

1. [Configurar](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) una nueva clave de API.

>[!IMPORTANT]
>
> Si genera claves nuevas en el portal de API, actualice inmediatamente las claves de API en la [!DNL Admin configuration]. Si genera claves nuevas y no las actualiza en el [!DNL Admin], sus extensiones SaaS dejarán de funcionar y perderá datos valiosos.

Si la extensión no está instalada, siga las siguientes instrucciones para instalarla:

1. Añada la extensión de a `composer.json` e instálelo.

   ```bash
   composer require magento/services-id
   ```

1. Active la extensión de.

   ```bash
   bin/magento module:enable Magento_ServicesId
   ```

1. Actualice el esquema de la base de datos.

   ```bash
   bin/magento setup:upgrade
   ```

1. Borre la caché.

   ```bash
   bin/magento cache:clean
   ```

1. [Configuración de claves API](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) para conectar la extensión al sistema.

## Instalación del agente

Hemos creado un [shell script](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) para simplificar la instalación. Se recomienda utilizar el script shell, pero puede seguir las [instalación manual](#manual) si es necesario.

>[!INFO]
>
>Una vez instalado el agente, se actualizará automáticamente cuando haya una nueva versión disponible.

### Con scripts

1. Descargue y ejecute el script shell.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >Se recomienda instalar el agente fuera del directorio raíz del proyecto de Adobe Commerce.

1. Compruebe la instalación.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Después de descargar e instalar el agente, [configúrelo para que se ejecute](#run-the-agent) mediante uno de los métodos siguientes:

   - [Servicio](#service) (preferido si tiene acceso raíz)

   - [Cron](#cron)

### Manual {#manual}

Si no desea utilizar nuestra [shell script](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) para instalar el agente, debe instalarlo manualmente siguiendo estos pasos:

1. Cree un directorio en el que quiera descargar el agente.

   >[!TIP]
   >
   >Se recomienda instalar el agente fuera del directorio raíz del proyecto de Adobe Commerce.

1. Descargue el archivo binario y desempaquete.

   >[!INFO]
   >
   >Para usar la variable [!DNL Site-Wide Analysis Tool], primero debe leer y aceptar las Condiciones de uso que se presentan al acceder al panel desde el Administrador de Adobe Commerce.

   Para el **AMD64** arquitectura:

   1. Descargue el archivo del lanzador.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Desempaquete el archivo del lanzador.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   Para el **ARM64** arquitectura:

   1. Descargue el archivo del lanzador.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. Desempaquete el archivo del lanzador.

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```

1. *(Opcional)* Compruebe la firma del archivo de suma de comprobación.

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *(Opcional)* Compruebe la suma de comprobación.

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. Cree el `config.yaml` archivo con el siguiente contenido.

   ```yaml
   project:
     appname: "Acme Inc" # Company or site name that you provided when installing the agent
   application:
     phppath: php # Path to your PHP CLI interpreter (usually /usr/bin/php)
     magentopath: /var/www/html/example.com # Root directory where your Adobe Commerce application is installed (usually /var/www/html)
     checkregistrypath: /path/to/swat-agent/tmp # Temporary directory for the agent (usually /usr/local/swat-agent/tmp)
     issandbox: false # Enabling sandbox mode to use the agent on staging environment (true or false)
     database:
       user: your-adobe-commerce-db-username # Database user for your Adobe Commerce installation
       password: your-password # Database password for the specified user for your Adobe Commerce installation
       host: 127.0.0.1 # Database host for your Adobe Commerce installation
       dbname: your-adobe-commerce-db-name # Database name for your Adobe Commerce installation
       port: 3306 # Database port for your Adobe Commerce installation (usually 3306)
       tableprefix: # Table Prefix for your Adobe Commerce installation (default value: empty)
    enableautoupgrade: true # Enables automatic upgrade (restart required after an upgrade; agent does not check for upgrades if the option is disabled; true or false)
    runchecksonstart: true # Collect data on the first run (Usually 1)
    loglevel: error # Determines what events are logged based on severity (usually error)
   ```

1. Compruebe la instalación.

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Después de descargar e instalar el agente, debe [configúrelo para que se ejecute](#run-the-agent) mediante uno de los métodos siguientes:

   - [Servicio](#service) (preferido si tiene acceso raíz)

   - [Cron](#cron)

## Ejecutar el agente {#run-the-agent}

Se recomienda configurar el agente para que se ejecute como servicio. Si tiene acceso limitado a su infraestructura y no tiene permisos de root, debe utilizar [cron](#cron) en su lugar.

### Servicio {#service}

1. Crear un archivo de unidad del sistema `(/etc/systemd/system/scheduler.service)` con la siguiente configuración (sustituya `<filesystemowner>` con el usuario de UNIX® que posee el directorio en el que están instalados el agente y el software de Adobe Commerce). Si ha descargado el agente como usuario raíz, cambie el propietario del directorio y de los archivos anidados.

   ```config
   [Unit]
   Wants=network.target
   After=network.target
   
   [Service]
   Type=simple
   User=<filesystemowner>
   ExecStart=/path/to/agent/scheduler
   Restart=always
   RestartSec=3
   
   [Install]
   WantedBy=multi-user.target
   ```

1. Inicie el servicio.

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. Compruebe que el servicio esté en funcionamiento.

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

Si no tiene permisos de raíz o no tiene permisos para configurar un servicio como raíz, puede utilizar cron en su lugar.

Actualice la programación de cron:

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## Desinstalar

Ejecute los siguientes comandos para desinstalar el servicio del sistema y eliminar todos los archivos generados:

1. Detenga el planificador.

   ```bash
   systemctl stop scheduler
   ```

1. Deshabilite el planificador.

   ```bash
   systemctl disable scheduler
   ```

1. Elimine el del servicio del planificador `systemd` archivo de unidad.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Vuelva a cargar `systemd` configuración del responsable.

   ```bash
   systemctl daemon-reload
   ```

1. Restablecer cualquiera `systemd` unidades de un estado fallido.

   ```bash
   systemctl reset-failed
   ```

1. Elimine el directorio de servicio del planificador.

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. Elimine el archivo binario del programador.

   ```bash
   rm /usr/local/bin/scheduler
   ```

Si configuró el agente para que se ejecute con cron en su lugar, siga las siguientes instrucciones:

1. Elimine el agente de la lista de crontab.

   ```bash
   crontab -e
   ```

1. Detenga el trabajo en ejecución.

   ```bash
   ps aux | grep scheduler
   ```

1. Elimine el directorio en el que instaló el agente.

   ```bash
   rm -rf swat-agent
   ```

## Resolución de problemas

### Claves de acceso no analizadas correctamente

Puede ver el siguiente error si las claves de acceso no se analizan correctamente:

```terminal
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

Para resolver este error, intente los siguientes pasos:

1. Realice una [instalación con script](#scripted), guarde el resultado y revise el resultado para ver si hay errores.
1. Revise los datos generados `config.yaml` y compruebe que la ruta a su instancia de Commerce y PHP es correcta.
1. Asegúrese de que el usuario que está ejecutando el planificador está en la [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md) El grupo Unix o es el mismo usuario que el propietario del sistema de archivos.
1. Asegúrese de que la variable [Conector de Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) Las claves de están instaladas correctamente e intente actualizarlas para conectar la extensión al sistema.
1. [Desinstalar](#uninstall) el agente después de actualizar las claves y vuelva a instalarlo con el [script de instalación](#scripted).
1. Ejecute el planificador y compruebe si sigue recibiendo el mismo error.
1. Si sigue recibiendo el mismo error, aumente el nivel de registro en `config.yaml` para depurar y abrir un ticket de asistencia.

### *SIGFAULT* Error

Si ve un *SIGFAULT* error al ejecutar el archivo binario, probablemente no lo ejecute como propietario de los archivos de Adobe Commerce y del agente.
Para resolverlo, compruebe si todos los archivos dentro del directorio del agente que tienen el mismo usuario que el propietario del archivo que tienen los archivos Adobe Commerce, y el binario también deben ejecutarse bajo ese usuario.
Puede usar el complemento `chown` para cambiar el propietario de los archivos y cambiar al usuario apropiado.
Asegúrese de que el mecanismo de daemonización (Cron o System.d) ejecuta el proceso con el usuario adecuado.

>[!INFO]
>
>Consulte [Cómo acceder a [!DNL Site-Wide Analysis Tool] y generar informes](../site-wide-analysis-tool/access.md).
