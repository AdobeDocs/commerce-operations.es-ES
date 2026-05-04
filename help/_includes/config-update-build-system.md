---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# Actualizar sistema de compilación

**Para actualizar el sistema de compilación**:

1. Inicie sesión en el sistema de generación como propietario del sistema de archivos.
1. Cambie al directorio raíz de la aplicación.

   ```shell
   cd <Magento root dir>
   ```

1. Extraer los cambios de `app/etc/config.php` del control de código fuente.

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. Compile el código.

   ```shell
   bin/magento setup:di:compile
   ```

1. Una vez compilado el código, genere archivos de vista estática.

   ```shell
   bin/magento setup:static-content:deploy -f
   ```

1. Comprobar los cambios en el control de código fuente.

   ```shell
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
