---
title: Aplicar parches
description: Obtenga información sobre los métodos para aplicar parches a un proyecto de Adobe Commerce.
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Aplicar parches

Puede aplicar parches utilizando cualquiera de los siguientes métodos:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es){target="_blank"}
- [Línea de comandos](../patches/apply.md#command-line)
- [Compositor](../patches/apply.md#composer)


>[!TIP]
>
>Consulte las [prácticas recomendadas](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md) para obtener información sobre los parches centralizados para Adobe Commerce a escala empresarial.

## Compositor

>[!IMPORTANT]
>
>Para aplicar parches de calidad oficiales, use [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es){target="_blank"}. Realice siempre pruebas exhaustivas antes de implementar cualquier parche personalizado.

Para aplicar un parche personalizado con Composer:

1. Abra la aplicación de línea de comandos y vaya al directorio del proyecto.
1. Agregar el complemento `cweagans/composer-patches` al archivo `composer.json`.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Edite el archivo `composer.json` y agregue la siguiente sección para especificar:
   - **Módulo:** *\&quot;magento/module-payment\&quot;*
   - **Título:** *\&quot;MAGETWO-56934: La página de cierre de compra se bloquea al realizar pedidos con Authorize.net con tarjeta de crédito no válida\&quot;*
   - **Ruta de acceso al parche:** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

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

1. Aplique el parche. Utilice la opción `-v` solo si desea ver información de depuración.

   ```bash
   composer -v install
   ```

1. Actualizar el archivo `composer.lock`. El archivo de bloqueo registra qué parches se han aplicado a cada paquete Composer de un objeto.

   ```bash
   composer update --lock
   ```

## Línea de comandos

Para aplicar parches desde la línea de comandos:

1. Cargue el archivo local en el directorio `<Magento_root>` del servidor mediante FTP, SFTP, SSH o el método de transporte normal.
1. Inicie sesión en el servidor como [usuario administrador](../../configuration/cli/config-cli.md#prerequisites) y compruebe que el archivo se encuentra en el directorio correcto.
1. En la interfaz de línea de comandos, ejecute los siguientes comandos según la extensión del parche:

   ```bash
   patch < patch_file_name.patch
   ```

   El comando supone que el archivo al que se va a aplicar el parche se encuentra en relación con el archivo de parche.

   >[!NOTE]
   >
   >Si la línea de comandos muestra: `File to patch:`, significa que no puede encontrar el archivo deseado, aunque la ruta de acceso parezca correcta. En el cuadro que se muestra en el terminal de la línea de comandos, la primera línea muestra el archivo al que se va a aplicar el parche. Copie la ruta de acceso del archivo y péguela en el símbolo del sistema `File to patch:`, presione `Enter` y la revisión debería completarse.

1. Para que se reflejen los cambios, actualice la caché en el Administrador en **Sistema** > Herramientas > **Administración de caché**.

   Como alternativa, el parche se puede aplicar localmente con el mismo comando, luego confirmarse e insertarse normalmente.
