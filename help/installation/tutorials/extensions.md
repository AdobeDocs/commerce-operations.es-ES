---
title: Administración de extensiones de terceros
description: Siga estos pasos para instalar, habilitar, actualizar y desinstalar una extensión de Adobe Commerce.
exl-id: b564662a-2e5f-4fa9-bae1-ca7498478fa9
source-git-commit: 6da0e70acc77d2171d6336ab632e6a9a8dd16c67
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 0%

---


# Administración de extensiones de terceros

El código que amplía o personaliza el comportamiento de Adobe Commerce se denomina extensión. Si lo desea, puede empaquetar y distribuir extensiones en [Commerce Marketplace](https://commercemarketplace.adobe.com/) u otro sistema de distribución de extensiones.

Las extensiones incluyen:

- Módulos (ampliación de las funciones de Adobe Commerce)
- Temas (cambia la apariencia de tu tienda y administrador)
- Paquetes de idioma (localice la tienda y el administrador)

>[!TIP]
>
>En este tema se explica cómo utilizar la interfaz de línea de comandos para administrar las extensiones de terceros que compra al Commerce Marketplace. Puede utilizar el mismo procedimiento para instalar _cualquiera_ Extensión; todo lo que necesita es el nombre y la versión Compositor de la extensión. Para encontrarlo, abra el de la extensión de `composer.json` y anote los valores de `"name"` y `"version"`.

## Instalar

Antes de la instalación, es posible que desee:

1. Haga una copia de seguridad de la base de datos.
1. Activar modo de mantenimiento:

   ```bash
   bin/magento maintenance:enable
   ```

Para instalar una extensión, debe:

1. Obtenga una extensión del Commerce Marketplace u otro desarrollador de extensiones.
1. Si instala una extensión desde el Commerce Marketplace, asegúrese de que la variable `repo.magento.com` el repositorio existe en su `composer.json` archivo:

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. Obtenga el nombre y la versión del compositor de la extensión.
1. Actualice el `composer.json` en el proyecto con el nombre y la versión de la extensión.
1. Compruebe que la extensión de está instalada correctamente.
1. Habilite y configure la extensión de.

### Obtener información de extensión

Si ya conoce el nombre y la versión del compositor de la extensión, omita este paso y continúe con [Actualice su `composer.json` archivo](#update-composer-dependencies).

Para obtener el nombre y la versión del compositor de la extensión desde el Commerce Marketplace:

1. Iniciar sesión en [Commerce Marketplace](https://commercemarketplace.adobe.com/) con el nombre de usuario y la contraseña que utilizó para adquirir la extensión de.

1. En la esquina superior derecha, haga clic en **Su nombre** > **Mi perfil**.

   ![Acceder a su cuenta de Marketplace](../../assets/installation/marketplace-my-profile.png)

1. Clic **Mis compras**.

   ![Historial de compras de Marketplace](../../assets/installation//marketplace-my-purchases.png)

1. Busque la extensión que desea instalar y haga clic en **Detalles técnicos**.

   ![Los detalles técnicos muestran el nombre de Compositor de la extensión.](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>También puede encontrar el nombre del compositor y la versión de _cualquiera_ extensión (tanto si la compró en Commerce Marketplace como en otro sitio) en el `composer.json` archivo.

### Actualizar dependencias del Compositor

Añada el nombre y la versión de la extensión a su `composer.json` archivo:

1. Vaya al directorio del proyecto y actualice el `composer.json` archivo.

   ```bash
   composer require <component-name>:<version>
   ```

   Por ejemplo,

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. Introduzca su [claves de autenticación](../prerequisites/authentication-keys.md). Su clave pública es su nombre de usuario; su clave privada es su contraseña.

1. Espere a que Composer termine de actualizar las dependencias del proyecto y asegúrese de que no hay errores:

   ```terminal
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

### Verificar instalación

Para comprobar que la extensión de está instalada correctamente, ejecute el siguiente comando:

```bash
bin/magento module:status J2t_Payplug
```

De forma predeterminada, la extensión está probablemente deshabilitada:

```terminal
Module is disabled
```

El nombre de la extensión tiene el formato `<VendorName>_<ComponentName>`; este es un formato diferente del nombre del Compositor. Utilice este formato para activar la extensión de. Si no está seguro del nombre de la extensión, ejecute:

```bash
bin/magento module:status
```

Y busque la extensión en &quot;Lista de módulos desactivados&quot;.

### Activar

Algunas extensiones no funcionan correctamente a menos que borre primero los archivos de vista estática generados. Utilice el `--clear-static-content` para borrar los archivos de vista estática al activar una extensión.

1. Habilite la extensión y borre los archivos de vista estática:

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

1. Registre la extensión:

   ```bash
   bin/magento setup:upgrade
   ```

1. Vuelva a compilar el proyecto: en el modo de producción, puede recibir un mensaje que indique &quot;Vuelva a ejecutar el comando de compilación del Magento&quot;. La aplicación no le pide que ejecute el comando de compilación en modo de desarrollador.

   ```bash
   bin/magento setup:di:compile
   ```

1. Compruebe que la extensión esté habilitada:

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   Debería ver la salida que verifica que la extensión ya no está deshabilitada:

   ```terminal
   Module is enabled
   ```

1. Limpie la caché:

   ```bash
   bin/magento cache:clean
   ```

1. Configure la extensión en Administración según sea necesario.

>[!TIP]
>
>Si se producen errores al cargar la tienda en un explorador, utilice el siguiente comando para borrar la caché: `bin/magento cache:flush`.

## Actualizar

Para actualizar o actualizar un módulo o una extensión:

1. Descargue el archivo actualizado desde Marketplace u otro desarrollador de extensiones. Tome nota del nombre y la versión del módulo.

1. Exporte el contenido al directorio raíz de la aplicación.

1. Si existe un paquete Composer para el módulo, ejecute una de las siguientes acciones.

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

## Desinstalar

Debe ponerse en contacto con el proveedor de la extensión para obtener instrucciones sobre cómo quitar una extensión de terceros. Las instrucciones deben proporcionar la siguiente información:

- Cómo revertir los cambios de la tabla de base de datos
- Cómo revertir los cambios de datos de la base de datos
- Qué archivos se deben eliminar o revertir

>[!CAUTION]
>
>Realice los pasos de desinstalación en un entorno que no sea de producción _primero_ y realice pruebas exhaustivas antes de su implementación en el entorno de producción de.

Las siguientes instrucciones proporcionan información general para desinstalar extensiones de terceros:

1. Elimine la extensión del repositorio del proyecto de Adobe Commerce.

   - Para las extensiones basadas en Compositor, elimine la extensión de su Adobe Commerce `composer.json` archivo.

     ```bash
     composer remove <package-name>
     ```

   - Para las extensiones no basadas en Compositor, elimine los archivos físicos del repositorio del proyecto de Adobe Commerce.

     ```bash
     rm -rf app/code/<vendor-name>/<module-name>
     ```

1. Si la variable `config.php` está bajo control de código fuente en el repositorio del proyecto de Adobe Commerce, elimine la extensión de la `config.php` archivo.

1. Pruebe la base de datos local para asegurarse de que las instrucciones proporcionadas por el proveedor funcionan según lo esperado.

1. Compruebe que la extensión de está correctamente deshabilitada y que el sitio web funciona según lo esperado en el entorno de ensayo.

1. Implemente los cambios en el entorno de producción.
