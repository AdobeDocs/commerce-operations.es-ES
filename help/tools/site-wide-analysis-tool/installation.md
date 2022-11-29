---
title: Guía de instalación
description: "Utilice esta guía para instalar [!DNL Site-Wide Analysis Tool] para su sitio web"
source-git-commit: bfcedda38f91f5dba8880bb1593ad40a6e3f8041
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 0%

---

# Guía de instalación

La variable [!DNL Site-Wide Analysis Tool] proporciona monitoreo, informes y recomendaciones de rendimiento en tiempo real las 24 horas del día, los 7 días de la semana para garantizar la seguridad y operabilidad de Adobe Commerce en instalaciones de infraestructura en la nube. También proporciona información detallada sobre los parches disponibles e instalados, las extensiones de terceros y la instalación de Adobe Commerce.

>[!INFO]
>
>Más información [cómo habilitar](../site-wide-analysis-tool/access.md) el [!DNL Site-Wide Analysis Tool] y generar informes.

Si tiene una instalación local de Adobe Commerce, debe instalar un agente en la infraestructura para utilizar la herramienta. No es necesario instalar el agente en Adobe Commerce en proyectos de infraestructura en la nube.

## Agente

La variable [!DNL Site-Wide Analysis Tool] El agente le permite usar la variable [!DNL Site-Wide Analysis Tool] para instalaciones locales de Adobe Commerce.

La variable [!DNL Site-Wide Analysis Tool] El agente recopila datos de aplicaciones y negocios, los analiza y proporciona perspectivas adicionales sobre el estado de su instalación para que pueda mejorar la experiencia del cliente. Supervisa su aplicación y le ayuda a identificar problemas de rendimiento, seguridad, disponibilidad y aplicaciones.

La instalación del agente requiere los siguientes pasos:

1. Compruebe los requisitos del sistema.

1. Configure las claves de API en la variable [!UICONTROL Commerce Services Connector] extensión.

1. Instale el agente.

1. Ejecute el agente.

>[!INFO]
>
>El agente admite instalaciones de Adobe Commerce de varios nodos. Debe instalar y configurar el agente en cada nodo.

## Requisitos del sistema

Su infraestructura local debe cumplir los siguientes requisitos antes de instalar el agente:

- Sistemas operativos

   - [!DNL Linux x86-64] distribuciones, como [!DNL RedHat Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian]y similares
   >[!IMPORTANT]
   >
   >Adobe Commerce no es compatible con [!DNL Microsoft Windows] o [!DNL macOS].

- Adobe Commerce 2.4.1 o posterior

- [!DNL Commerce Services Connector extension]

- CLI de PHP

- Utilidades Flash/shell

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

El agente requiere la variable [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) extensión que se instalará en el sistema y [configurado](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) con claves de API. Para comprobar que la extensión está instalada, ejecute el siguiente comando:

```bash
bin/magento module:status Magento_ServicesConnector
```

Si ha instalado la extensión y la ha configurado utilizando una clave de API existente para un servicio diferente, **DEBE regenerar la clave de API** y actualícelo en Adobe Commerce Admin para el agente.

1. Coloque el sitio web en [modo de mantenimiento](../../installation/tutorials/maintenance-mode.md).

1. Iniciar sesión [accounts.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

1. Haga clic **[!UICONTROL API Portal]**.

1. Haga clic en **[!UICONTROL Delete]** junto a la clave de API existente.

1. [Configurar](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) una nueva clave de API.

>[!IMPORTANT]
>
> Si genera nuevas claves en el portal de API, actualice inmediatamente las claves de API en la variable [!DNL Admin configuration]. Si genera claves nuevas y no las actualiza en la variable [!DNL Admin], sus extensiones SaaS ya no funcionarán y perderá datos valiosos.

Si la extensión no está instalada, siga las siguientes instrucciones para instalarla:

1. Añada la extensión a la `composer.json` e instálelo.

   ```bash
   composer require magento/services-connector:1.*
   ```

1. Active la extensión .

   ```bash
   bin/magento module:enable Magento_ServicesConnector
   ```

1. Actualice el esquema de la base de datos.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configuración de claves de API](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) para conectar la extensión al sistema.

## Instale el agente

Hemos creado un [script shell](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) para simplificar la instalación. Se recomienda utilizar el script shell, pero se puede seguir el [instalación manual](#manual) si es necesario.

>[!INFO]
>
>Una vez instalado el agente, se actualizará automáticamente cuando haya una nueva versión disponible.

### Secuencia de comandos

1. Descargue y ejecute el script shell.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >Se recomienda instalar el agente fuera del directorio raíz del proyecto de Adobe Commerce.

1. Verifique la instalación.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Después de descargar e instalar el agente, debe [configúrelo para que se ejecute](#run-the-agent) utilizando uno de los siguientes métodos:

   - [Servicio](#service) (preferible si tiene acceso raíz)

   - [Cron](#cron)

### Manual {#manual}

Si no desea usar nuestra [script shell](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) para instalar el agente, debe instalarlo manualmente siguiendo estos pasos:

1. Cree un directorio donde desee descargar el agente.

   >[!TIP]
   >
   >Se recomienda instalar el agente fuera del directorio raíz del proyecto de Adobe Commerce.

1. Descargue el archivo binario y desempaquete.

   >[!INFO]
   >
   >Para usar la variable [!DNL Site-Wide Analysis Tool], primero debe leer y aceptar las condiciones de uso que se presentan al acceder al tablero desde el administrador de Adobe Commerce.

   Para la variable **AMD64** arquitectura:

   1. Descargue el archivo del lanzador.

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Desempaquete el archivo del lanzador.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```
   Para la variable **ARM64** arquitectura:

   1. Descargue el archivo del lanzador.

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-arm64.tar.gz
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

1. *(Opcional)* Verifique la suma de comprobación.

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. Cree la variable `config.yaml` con el siguiente contenido.

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

1. Verifique la instalación.

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Después de descargar e instalar el agente, debe [configúrelo para que se ejecute](#run-the-agent) utilizando uno de los siguientes métodos:

   - [Servicio](#service) (preferible si tiene acceso raíz)

   - [Cron](#cron)

## Ejecutar el agente {#run-the-agent}

Se recomienda configurar el agente para que se ejecute como servicio. Si tiene acceso limitado a su infraestructura y no tiene permisos de raíz, debe usar [cron](#cron) en su lugar.

### Servicio {#service}

1. Crear un archivo de unidad sistémica `(/etc/systemd/system/scheduler.service)` con la siguiente configuración (reemplace `<filesystemowner>` con el usuario de Unix que posee el directorio donde están instalados el agente y el software de Adobe Commerce). Si descargó el agente como usuario raíz, cambie el directorio y el propietario de los archivos anidados.

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

1. Valide que el servicio esté activo y en ejecución.

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

Si no tiene permisos de raíz o no tiene permisos para configurar un servicio como raíz, puede usar cron en su lugar.

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

1. Eliminación del `systemd` archivo de unidad.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Vuelva a cargar el `systemd` configuración del administrador.

   ```bash
   systemctl daemon-reload
   ```

1. Restablecer cualquier `systemd` unidades de un estado fallido.

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

1. Elimine el agente de la lista crontab.

   ```bash
   crontab -e
   ```

1. Detenga el trabajo en ejecución.

   ```bash
   ps aux | grep scheduler
   ```

1. Elimine el directorio donde instaló el agente.

   ```bash
   rm -rf swat-agent
   ```

## Anular el archivo de configuración

Puede anular los valores especificados en el archivo de configuración durante la instalación mediante variables de entorno. Esto preserva la compatibilidad con versiones anteriores del agente. Consulte la tabla siguiente para conocer los valores recomendados:

| PROPIEDAD | DESCRIPCIÓN |
| --- | --- |
| `SWAT_AGENT_APP_NAME` | Nombre de empresa o sitio que proporcionó al instalar el agente |
| `SWAT_AGENT_APPLICATION_PHP_PATH` | Ruta a su intérprete de CLI de PHP (generalmente `/usr/bin/php`) |
| `SWAT_AGENT_APPLICATION_MAGENTO_PATH` | Directorio raíz en el que está instalada la aplicación de Adobe Commerce (normalmente `/var/www/html`) |
| `SWAT_AGENT_APPLICATION_DB_USER` | Usuario de base de datos para la instalación de Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_PASSWORD` | Contraseña de la base de datos del usuario especificado para la instalación de Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_HOST` | Host de base de datos para la instalación de Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_NAME` | Nombre de base de datos para la instalación de Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_PORT` | Puerto de base de datos para la instalación de Adobe Commerce (normalmente `3306`) |
| `SWAT_AGENT_APPLICATION_DB_TABLE_PREFIX` | Prefijo de tabla para la instalación de Adobe Commerce (valor predeterminado: `empty`) |
| `SWAT_AGENT_APPLICATION_DB_REPLICATED` | Si la instalación de Adobe Commerce tiene una instancia de base de datos secundaria (normalmente `false`) |
| `SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH` | Directorio temporal para el agente (normalmente `/usr/local/swat-agent/tmp`) |
| `SWAT_AGENT_RUN_CHECKS_ON_START` | Recopilación de datos en la primera ejecución (normalmente `1`) |
| `SWAT_AGENT_LOG_LEVEL` | Determina qué eventos se registran en función de la gravedad (normalmente `error`) |
| `SWAT_AGENT_ENABLE_AUTO_UPGRADE` | Habilita la actualización automática (se requiere reiniciar después de una actualización); el agente no comprueba si hay actualizaciones si la opción está desactivada; `true` o `false`) |
| `SWAT_AGENT_IS_SANDBOX=false` | Habilitar el modo de entorno limitado para utilizar el agente en el entorno de ensayo |

>[!INFO]
>
>Consulte [Cómo acceder [!DNL Site-Wide Analysis Tool] y generar informes](../site-wide-analysis-tool/access.md).
