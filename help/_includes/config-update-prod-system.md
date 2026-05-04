---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# Actualizar sistema de producción

**Para actualizar el sistema de producción**:

1. Inicie sesión en el sistema de producción como propietario del sistema de archivos.
1. Cambie a la raíz de la aplicación y habilite el modo de mantenimiento.

   ```shell
   cd <Magento root dir>
   ```

   ```shell
   bin/magento maintenance:enable
   ```

   Para obtener opciones adicionales, como la posibilidad de establecer una lista blanca de direcciones IP, vea [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md).

1. Detenga los trabajadores de cola en ejecución estableciendo `cron_run` en `false` en `app/etc/env.php` de la siguiente manera:

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Actualice la configuración.

   ```shell
   bin/magento app:config:import
   ```

1. Finalmente, `kill` cualquier proceso de consumidor activo.

   ```shell
   kill <PID>
   ```

   Donde `PID` es el ID de proceso que se va a eliminar, por ejemplo:

   ```shell
   kill 1234
   ```

1. Extraer código del control de código fuente.

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. Actualice la configuración.

   ```shell
   bin/magento app:config:import
   ```

1. Limpie la caché.

   ```shell
   bin/magento cache:clean
   ```

1. Finalizar modo de mantenimiento.

   ```shell
   bin/magento maintenance:disable
   ```
