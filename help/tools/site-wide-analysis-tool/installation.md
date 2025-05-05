---
title: Guía de instalación
description: Utilice este guía para instalar [!DNL Site-Wide Analysis Tool] en su sitio Web
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 0%

---

# Guía de instalación

>[!IMPORTANT]
>
>A partir del 23 de abril de 2024, el se retirará del [!DNL Site-Wide Analysis Tool] mercado para todos los clientes locales de Adobe Systems Commerce.

Proporciona [!DNL Site-Wide Analysis Tool] monitoreo de rendimiento en tiempo real las 24 horas del día, los 7 días de la semana, informes y recomendaciones para garantizar la seguridad y operatividad de Adobe Systems Commerce en instalaciones infraestructura en la nube. También proporciona información detallada sobre los parches disponibles e instalados, las extensiones de terceros y la instalación de Adobe Systems Commerce.

>[!INFO]
>
>Aprenda [a habilitar](../site-wide-analysis-tool/access.md) y [!DNL Site-Wide Analysis Tool] generar informes.

Si tiene una instalación local de Adobe Systems Commerce, instale un agente en su infraestructura para usar el herramienta. No es necesario instalar el agente en Adobe Systems Commerce en infraestructura en la nube proyectos.

## Agente

El [!DNL Site-Wide Analysis Tool] agente le permite usar el [!DNL Site-Wide Analysis Tool] para instalaciones locales de Adobe Systems Commerce.

El [!DNL Site-Wide Analysis Tool] agente recopila datos aplicación y empresariales, los analiza y proporciona información adicional sobre el estado de su instalación para que pueda mejorar experiencia del cliente. Supervisa su aplicación y le ayuda a identificar problemas de rendimiento, seguridad, disponibilidad y aplicación.

La instalación del agente requiere los siguientes pasos:

1. Compruebe los requisitos del sistema.

1. Configure las claves de API en la [!UICONTROL Commerce Services Connector] extensión.

1. Instale el agente.

1. Ejecute el agente.

>[!INFO]
>
>El agente admite instalaciones de comercio Adobe Systems nodo múltiples. Instale y configure el agente en cada nodo.

## requisitos del sistema

La infraestructura local debe cumplir los siguientes requisitos antes de instalar el agente:

- Sistemas operativos

   - [!DNL Linux x86-64] distribuciones, como [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian], y similares

  >[!IMPORTANT]
  >
  >Adobe Systems El comercio no es compatible con [!DNL Microsoft Windows] o [!DNL macOS].

- Adobe Systems Commerce 2.4.5-p1 o posterior (debido a la dependencia de Service Connector)

- [!DNL Commerce Services Connector extension]

- PHP CLI

- Utilidades Bash/shell

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

El agente requiere que la [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) extensión esté instalada en el sistema y [configurada](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) con claves API. Para comprobar que la extensión está instalada, ejecute el siguiente comando:

```bash
bin/magento module:status Magento_ServicesId
```

Si ha instalado la extensión y la ha configurado con una clave de API existente para un servicio diferente, **DEBE volver a generar la clave** de API y actualizarla en el Administrador de Adobe Systems Commerce del agente.

1. Ponga su sitio web en [modo](../../installation/tutorials/maintenance-mode.md) de mantenimiento.

1. Inicie sesión en [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > Si tiene problemas para acceder a su cuenta, consulte [No se puede iniciar sesión en el soporte de Adobe Systems Commerce o nube cuenta](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) para obtener ayuda sobre la solución de problemas.

1. Haga clic en **[!UICONTROL API Portal]**.

1. Haga clic **[!UICONTROL Delete]** junto a la clave de API existente.

1. [Configure](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) una nueva clave de API.

>[!IMPORTANT]
>
> Si genera nuevas claves en API Portal, actualice inmediatamente las claves de API en el [!DNL Admin configuration]archivo . Si genera nuevas claves y no actualiza las claves en , [!DNL Admin]sus extensiones SaaS dejarán de funcionar y perderá datos valiosos.

Si la extensión no está instalada, siga estas instrucciones para instalarla:

1. añadir la extensión del `composer.json` archivo e instálela.

   ```bash
   composer require magento/services-id
   ```

1. Habilite la extensión.

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

1. [Configure las claves](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) de API para conectar la extensión al sistema.

## Instale el agente

Hemos creado un [script](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) de shell para simplificar la instalación. Se recomienda utilizar la secuencia de comandos de shell, pero puede seguir el método de [instalación](#manual) manual si es necesario.

>[!INFO]
>
>Una vez instalado el agente, se actualizará automáticamente cuando haya una versión nueva disponible.

### Guión

1. Descargue y ejecute la secuencia de comandos del shell.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >Se recomienda instalar el agente fuera del directorio del proyecto de Adobe Systems Commerce raíz.

1. Verifique la instalación.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Después de descargar e instalar el agente, [configúrelo para que se ejecute](#run-the-agent) mediante uno de los métodos siguientes:

   - [Servicio](#service) (preferido si tiene acceso root)

   - [Cron](#cron)

### Manual {#manual}

Si no desea utilizar nuestro [script](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) de shell para instalar el agente, debe instalarlo manualmente siguiendo estos pasos:

1. Crear un directorio al que desee descargar el agente.

   >[!TIP]
   >
   >Se recomienda instalar el agente fuera del directorio del proyecto de Adobe Systems Commerce raíz.

1. Descargue el archivo binario y descomprímalo.

   >[!INFO]
   >
   >Para usar el [!DNL Site-Wide Analysis Tool], primero debe leer y aceptar los Condiciones de uso que se presentan cuando accede al panel desde el Administrador de comercio de Adobe Systems.

   Para la **arquitectura AMD64** :

   1. Descargue el archivo lanzador.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Descomprima el archivo lanzador.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   Para la **arquitectura ARM64** :

   1. Descargue el archivo lanzador.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. Descomprima el archivo lanzador.

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

1. *(Opcional)* Verificar la suma de comprobación.

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. Crear el `config.yaml` archivo con el siguiente contenido.

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

1. Después de descargar e instalar el agente, debe [configurarlo para que se ejecute](#run-the-agent) mediante uno de los métodos siguientes:

   - [Servicio](#service) (preferido si tiene acceso root)

   - [Cron](#cron)

## Ejecutar el agente {#run-the-agent}

Se recomienda configurar el agente para que se ejecute como un servicio. Si tiene acceso limitado a su infraestructura y no tiene permisos de root, debe usar [cron](#cron) en su lugar.

### Servicio {#service}

1. Crear un archivo `(/etc/systemd/system/scheduler.service)` de unidad systemd con la siguiente configuración (reemplácelo `<filesystemowner>` con el usuario UNIX® que posee el directorio donde están instalados el agente y el software de Adobe Systems Commerce). Si ha descargado el agente como usuario raíz, cambie el directorio y los archivos anidados propietario.

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

1. Launch el servicio.

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. Valide que el servicio está en funcionamiento.

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

Si no tiene permisos de root o no tiene permisos para configurar un servicio como root, puede usar cron en su lugar.

Actualiza tu cron schedule:

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## Desinstalar

Ejecute los siguientes comandos para desinstalar el servicio de su sistema y eliminar todos los archivos generados:

1. Parada el planificador.

   ```bash
   systemctl stop scheduler
   ```

1. Deshabilite el planificador.

   ```bash
   systemctl disable scheduler
   ```

1. Quitar el archivo unitario del `systemd` servicio de planificador.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Vuelva a cargar la configuración del `systemd` administrador.

   ```bash
   systemctl daemon-reload
   ```

1. Restablecer unidades `systemd` de un estado con errores.

   ```bash
   systemctl reset-failed
   ```

1. Quitar el directorio del servicio planificador.

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. Quitar el archivo binario planificador.

   ```bash
   rm /usr/local/bin/scheduler
   ```

Si ha configurado el agente para que se ejecute con cron en su lugar, utilice las siguientes instrucciones:

1. Quitar el agente desde el lista crontab.

   ```bash
   crontab -e
   ```

1. Parada el trabajo en ejecución.

   ```bash
   ps aux | grep scheduler
   ```

1. Quitar el directorio donde instaló el agente.

   ```bash
   rm -rf swat-agent
   ```

## Resolución de problemas

### Las teclas de acceso no se analizan correctamente

Puede ver el siguiente error si sus claves de acceso no se analizan correctamente:

```
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

Para resolver este error, pruebe los siguientes pasos:

1. Realice una [instalación](#scripted) programada, guarde el resultado y revise el resultado en busca de errores.
1. Revise el archivo generado `config.yaml` y compruebe que la ruta de acceso a su instancia de comercio y PHP es correcta.
1. Asegúrese de que el usuario que ejecuta el planificador está en el sistema de [archivos propietario](../../installation/prerequisites/file-system/overview.md) Unix grupo o es el mismo usuario que el sistema de archivos propietario.
1. Asegúrese de que las claves del [conector de Commerce Services estén](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) instaladas correctamente e intente actualizarlas para conectar la extensión al sistema.
1. [Desinstale](#uninstall) el agente después de actualizar las claves y vuelva a instalarlo con el script[&#128279;](#scripted) de instalación.
1. Ejecute el planificador y compruebe si sigue recibiendo el mismo error.
1. Si sigue recibiendo el mismo error, aumente el nivel de registro en la `config.yaml` depurar y abra un vale de soporte.

### *Error SIGFAULT*

Si ve un *error SIGFAULT* al ejecutar binario, probablemente no lo ejecute como el propietario de archivo de Adobe Systems archivos Commerce y Agent.
Para resolverlo, compruebe si todos los archivos dentro del directorio del agente que tienen el mismo usuario que el propietario del archivo que tienen los archivos Adobe Systems Commerce y binarios también deben ejecutarse bajo esa usuario.
Puede utilizar el `chown` comando para cambiar el propietario de archivos y cambiar al usuario adecuado.
Asegúrese de que su mecanismo de demonización (Cron o System.d) ejecuta el proceso bajo la usuario apropiada.

>[!INFO]
>
>Consulte [Cómo acceder [!DNL Site-Wide Analysis Tool] y generar informes](../site-wide-analysis-tool/access.md).
