---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# Actualizar sistema de compilación

**Para actualizar el sistema de generación**:

1. Inicie sesión en el sistema de generación como propietario del sistema de archivos.
1. Cambie al directorio raíz de la aplicación.

   ```bash
   cd <Magento root dir>
   ```

1. Extraer los cambios a `app/etc/config.php` desde el control de código fuente.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Compile el código.

   ```bash
   bin/magento setup:di:compile
   ```

1. Una vez compilado el código, genere archivos de vista estática.

   ```bash
   bin/magento setup:static-content:deploy -f
   ```

1. Comprobar los cambios en el control de código fuente.

   ```bash
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
