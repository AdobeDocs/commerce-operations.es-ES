---
title: Aplicar parches
description: Obtenga información sobre los métodos para aplicar parches a un proyecto de Adobe Commerce o de Magento Open Source.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# Aplicar parches

Puede aplicar parches mediante cualquiera de los siguientes métodos:

- [Herramienta Parches de calidad](https://devdocs.magento.com/quality-patches/tool.html)
- [Línea de comandos](../patches/apply.md#command-line)
- [Compositor](../patches/apply.md#composer)

## Compositor

>[!IMPORTANT]
>
>Para aplicar parches oficiales de calidad, utilice la variable [Herramienta Parches de calidad](https://devdocs.magento.com/quality-patches/tool.html). Realice pruebas exhaustivas antes de implementar cualquier parche personalizado.

Para aplicar un parche personalizado con Composer:

1. Abra la aplicación de línea de comandos y vaya al directorio del proyecto.
1. Agregue la variable `cweagans/composer-patches` complemento de `composer.json` archivo.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Edite el `composer.json` y agregue la siguiente sección para especificar:
   - **Módulo:** *\&quot;magento/module-payment\&quot;*
   - **Título:** *\&quot;MAGETWO-56934: La página de cierre de compra se bloquea al realizar un pedido con Authorize.net con una tarjeta de crédito no válida\&quot;*
   - **Ruta al parche:** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

   Por ejemplo:

   ```json
   "extra": {
       "composer-exit-on-patch-failure": true,
       "patches": {
           "magento/module-payment": {
               "MAGETWO-56934: Checkout page freezes when ordering with Authorize.net with invalid credit card": "patches/composer/github-issue-6474.diff"
           }
       }
   }
   ```

   Si un parche afecta a varios módulos, debe crear varios archivos de parche dirigidos a varios módulos.

1. Aplique el parche. Utilice la variable `-v` solo si desea ver la información de depuración.

   ```bash
   composer -v install
   ```

1. Actualice el `composer.lock` archivo. El archivo de bloqueo rastrea qué parches se han aplicado a cada paquete del Compositor en un objeto.

   ```bash
   composer update --lock
   ```

## Línea de comandos

Para aplicar parches desde la línea de comandos:

1. Cargue el archivo local en el `<Magento_root>` en el servidor mediante FTP, SFTP, SSH o el método de transporte normal.
1. Inicie sesión en el servidor como [usuario administrador](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli.html#config-install-cli-first) y compruebe que el archivo se encuentra en el directorio correcto.
1. En la interfaz de la línea de comandos, ejecute los siguientes comandos según la extensión del parche:

   ```bash
   patch < patch_file_name.patch
   ```

   El comando supone que el archivo que se va a parchear se encuentra en relación con el archivo de parche.

   >[!NOTE]
   >
   >Si la línea de comandos muestra: `File to patch:`, significa que no puede localizar el archivo deseado, aunque la ruta parezca correcta. En el cuadro mostrado en el terminal de la línea de comandos, la primera línea muestra el archivo que se va a parchear. Copie la ruta del archivo y péguela en el `File to patch:` solicitud y pulse `Enter` y el parche debe completarse.

1. Para que se reflejen los cambios, actualice la caché en la sección Administración de **Sistema** > Herramientas > **Administración de caché**.

   Alternativamente, el parche se puede aplicar localmente con el mismo comando, luego se confirma y se empuja normalmente.
