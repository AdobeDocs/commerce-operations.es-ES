---
title: Aplicar parches
description: Obtenga información sobre los métodos para aplicar parches a un proyecto de Adobe Commerce o de Magento Open Source.
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Aplicar parches

Puede aplicar parches utilizando cualquiera de los siguientes métodos:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [Línea de comandos](../patches/apply.md#command-line)
- [Compositor](../patches/apply.md#composer)

## Compositor

>[!IMPORTANT]
>
>Para aplicar parches de calidad oficiales, use el [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Realice siempre pruebas exhaustivas antes de implementar cualquier parche personalizado.

Para aplicar un parche personalizado con Composer:

1. Abra la aplicación de línea de comandos y vaya al directorio del proyecto.
1. Añada el `cweagans/composer-patches` del complemento a `composer.json` archivo.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Edite el `composer.json` y agregue la siguiente sección para especificar:
   - **Módulo:** *\&quot;magento/module-payment\&quot;*
   - **Título:** *\&quot;MAGETWO-56934: La página de cierre de compra se bloquea al realizar el pedido con Authorize.net con una tarjeta de crédito no válida\&quot;*
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

1. Aplique el parche. Utilice el `-v` sólo si desea ver información de depuración.

   ```bash
   composer -v install
   ```

1. Actualice el `composer.lock` archivo. El archivo de bloqueo registra qué parches se han aplicado a cada paquete Composer de un objeto.

   ```bash
   composer update --lock
   ```

## Línea de comandos

Para aplicar parches desde la línea de comandos:

1. Cargue el archivo local en `<Magento_root>` en el servidor mediante FTP, SFTP, SSH o el método de transporte normal.
1. Inicie sesión en el servidor como [usuario administrador](../../configuration/cli/config-cli.md#prerequisites) y compruebe que el archivo se encuentra en el directorio correcto.
1. En la interfaz de línea de comandos, ejecute los siguientes comandos según la extensión del parche:

   ```bash
   patch < patch_file_name.patch
   ```

   El comando supone que el archivo al que se va a aplicar el parche se encuentra en relación con el archivo de parche.

   >[!NOTE]
   >
   >Si la línea de comandos muestra: `File to patch:`, significa que no puede localizar el archivo deseado, aunque la ruta parezca correcta. En el cuadro que se muestra en el terminal de la línea de comandos, la primera línea muestra el archivo al que se va a aplicar el parche. Copie la ruta de archivo y péguela en `File to patch:` preguntar y pulsar `Enter` y el parche debe completarse.

1. Para que se reflejen los cambios, actualice la caché en el Administrador en **Sistema** > Herramientas > **Administración de caché**.

   Como alternativa, el parche se puede aplicar localmente con el mismo comando, luego confirmarse e insertarse normalmente.
