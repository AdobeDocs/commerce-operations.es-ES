---
title: Instalación de una extensión
description: Siga estos pasos para instalar una extensión de Adobe Commerce o Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---


# Instalación de una extensión

El código que amplía o personaliza el comportamiento de Adobe Commerce y Magento Open Source se denomina extensión. Opcionalmente, puede empaquetar y distribuir extensiones en la variable [Commerce Marketplace](https://marketplace.magento.com) u otro sistema de distribución de extensiones.

Las extensiones incluyen:

- Módulos (ampliación de las funciones de Adobe Commerce y Magento Open Source)
- Temas (cambiar la apariencia de su tienda y administrador)
- Paquetes de idioma (localice la tienda y el administrador)

>[!TIP]
>
>En este tema se explica cómo utilizar la línea de comandos para instalar las extensiones que compra al Commerce Marketplace. Puede utilizar el mismo procedimiento para instalar _any_ extensión; todo lo que necesita es el nombre y la versión del Compositor de la extensión. Para encontrarlo, abra el informe `composer.json` y observe los valores de `"name"` y `"version"`.

Antes de la instalación, es posible que desee:

1. Haga una copia de seguridad de la base de datos.
1. Habilitar modo de mantenimiento:

   ```bash
   bin/magento maintenance:enable
   ```

Para instalar una extensión, debe:

1. Obtenga una extensión del Commerce Marketplace o de otro desarrollador de extensiones.
1. Si instala una extensión desde el Commerce Marketplace, asegúrese de que la variable `repo.magento.com` el repositorio existe en su `composer.json` archivo:

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. Obtenga el nombre y la versión del Compositor de extensiones.
1. Actualice el `composer.json` en el proyecto con el nombre y la versión de la extensión.
1. Compruebe que la extensión está instalada correctamente.
1. Habilite y configure la extensión de .

## Obtenga el nombre y la versión del Compositor de extensiones

Si ya conoce el nombre y la versión del Compositor de extensiones, omita este paso y continúe con [Actualice su `composer.json` file](#update-your-composer-file).

Para obtener el nombre y la versión del Compositor de la extensión del Commerce Marketplace:

1. Iniciar sesión en [Commerce Marketplace](https://marketplace.magento.com) con el nombre de usuario y la contraseña que utilizó para comprar la extensión.

1. En la esquina superior derecha, haga clic en **Su nombre** > **Mi perfil**.

   ![Acceda a su cuenta de Marketplace](../../assets/installation/marketplace-my-profile.png)

1. Haga clic en **Mis compras**.

   ![Historial de compras en Marketplace](../../assets/installation//marketplace-my-purchases.png)

1. Busque la extensión que desea instalar y haga clic en **Detalles técnicos**.

   ![Los detalles técnicos muestran el nombre del Compositor de la extensión](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>También puede encontrar el nombre y la versión del Compositor de _any_ (ya sea que la haya comprado en el Commerce Marketplace o en otro lugar) en la extensión de `composer.json` archivo.

## Actualizar el archivo del Compositor

Añada el nombre y la versión de la extensión a su `composer.json` archivo:

1. Vaya al directorio del proyecto y actualice la `composer.json` archivo.

   ```bash
   composer require <component-name>:<version>
   ```

   Por ejemplo,

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. Escriba la [claves de autenticación](../prerequisites/authentication-keys.md). Su clave pública es su nombre de usuario; la clave privada es su contraseña.

1. Espere a que el Compositor termine de actualizar las dependencias del proyecto y asegúrese de que no haya errores:

   ```terminal
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

## Verificar la extensión

Para comprobar que la extensión está instalada correctamente, ejecute el siguiente comando:

```bash
bin/magento module:status J2t_Payplug
```

De forma predeterminada, la extensión probablemente esté deshabilitada:

```terminal
Module is disabled
```

El nombre de la extensión tiene el formato `<VendorName>_<ComponentName>`; este es un formato diferente al nombre del Compositor. Utilice este formato para activar la extensión de . Si no está seguro del nombre de la extensión, ejecute:

```bash
bin/magento module:status
```

Y busque la extensión en &quot;Lista de módulos deshabilitados&quot;.

## Habilitar la extensión

Algunas extensiones no funcionan correctamente a menos que borre primero los archivos de vista estáticos generados. Utilice la variable `--clear-static-content` para borrar los archivos de vista estáticos al activar una extensión.

1. Habilite la extensión y borre los archivos de vista estáticos:

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   Debería ver el siguiente resultado:

   ```terminal
   The following modules have been enabled:
   - J2t_Payplug
   
   To make sure that the enabled modules are properly registered, run 'setup:upgrade'.
   Cache cleared successfully.
   Generated classes cleared successfully. Please run the 'setup:di:compile' command to generate classes.
   Generated static view files cleared successfully.
   ```

1. Registre la extensión de :

   ```bash
   bin/magento setup:upgrade
   ```

1. Recompile el proyecto: En el modo Producción, puede recibir un mensaje para &quot;Vuelva a ejecutar el comando de compilación del Magento&quot;. La aplicación no le solicita que ejecute el comando de compilación en modo de desarrollador.

   ```bash
   bin/magento setup:di:compile
   ```

1. Compruebe que la extensión esté habilitada:

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   Debería ver los resultados que verifican que la extensión ya no está deshabilitada:

   ```terminal
   Module is enabled
   ```

1. Limpie la caché:

   ```bash
   bin/magento cache:clean
   ```

1. Configure la extensión en Admin según sea necesario.

>[!TIP]
>
>Si se producen errores al cargar la tienda en un explorador, utilice el siguiente comando para borrar la caché: `bin/magento cache:flush`.

## Actualizar una extensión

Para actualizar o actualizar un módulo o una extensión:

1. Descargue el archivo actualizado desde Marketplace u otro desarrollador de extensiones. Tome nota del nombre y la versión del módulo.

1. Exporte el contenido al directorio raíz de la aplicación.

1. Si existe un paquete Composer para el módulo, ejecute uno de los siguientes.

   Actualización por nombre de módulo:

   ```bash
   composer update vendor/module-name
   ```

   Actualización por versión:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. Ejecute los siguientes comandos para actualizar, implementar y limpiar la caché.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
