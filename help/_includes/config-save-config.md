---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# Actualizar la configuración compartida

**Para actualizar la configuración**:

1. Inicie sesión en su sistema de desarrollo como propietario del sistema de archivos o cambie a él.

1. Cambie a la raíz de la aplicación y ejecute el comando dump.

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   Por ejemplo, si Commerce está instalado en `/var/www/html/magento2`, introduzca:

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. Confirme que `app/etc/config.php` se ha actualizado.

   ```bash
   git status
   ```

   Respuesta de ejemplo:

   ```terminal
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >Do _not_ envíe cambios a `generated`, `pub/media`o `pub/static` directorios para control de código fuente. Los genera en su sistema de compilación. Es probable que el sistema de desarrollo tenga código, temas, etc., que no estén listos para usar en el sistema de producción.

1. Compruebe los cambios en `app/etc/config.php` solo para control de código fuente.

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
