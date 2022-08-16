---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---
# Actualizar sistema de producción

**Para actualizar el sistema de producción**:

1. Inicie sesión en el sistema de producción como propietario del sistema de archivos.
1. Cambie a la raíz de la aplicación y habilite el modo de mantenimiento.

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   Para obtener más opciones, como la posibilidad de establecer una lista blanca de direcciones IP, consulte [`magento maintenance:enable`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. Detenga a los trabajadores en cola en ejecución estableciendo `cron_run` a `false` en `app/etc/env.php` de la siguiente manera:

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Actualice la configuración.

   ```bash
   bin/magento app:config:import
   ```

1. Finalmente, `kill` cualquier proceso activo del consumidor.

   ```bash
   kill <PID>
   ```

   Donde `PID` es el ID de proceso que se va a eliminar, por ejemplo:

   ```bash
   kill 1234
   ```

1. Extraer código del control de código fuente.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Actualice la configuración.

   ```bash
   bin/magento app:config:import
   ```

1. Limpie la caché.

   ```bash
   bin/magento cache:clean
   ```

1. Fin del modo de mantenimiento.

   ```bash
   bin/magento maintenance:disable
   ```