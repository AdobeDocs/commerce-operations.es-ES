---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# Actualizar la configuración compartida

**Para actualizar la configuración**:

1. Inicie sesión en el sistema de desarrollo como propietario del sistema de archivos o cambie a.

1. Cambie a la raíz de la aplicación y ejecute el comando dump.

   ```shell
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   Por ejemplo, si Commerce está instalado en `/var/www/html/magento2`, escriba:

   ```shell
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. Confirme que `app/etc/config.php` se ha actualizado.

   ```shell
   git status
   ```

   Respuesta de ejemplo:

   ```text
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >_no_ envía cambios a los directorios `generated`, `pub/media` o `pub/static` al control de código fuente. Estos archivos se generan en el sistema de compilación. Es probable que el sistema de desarrollo tenga código, temas, etc., que no estén listos para usarlos en el sistema de producción.

1. Proteja sus cambios en `app/etc/config.php` solo para el control de código fuente.

   ```shell
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
