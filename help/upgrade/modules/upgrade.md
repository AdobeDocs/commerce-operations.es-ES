---
title: Módulos y extensiones de actualización
description: Utilice la interfaz de línea de comandos y el Compositor para actualizar los módulos y extensiones de Adobe Commerce y Magento Open Source.
source-git-commit: 70f1bda91023526fbc0024b6a6fef93c7633ecc2
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Módulos de actualización y extensiones

Para actualizar o actualizar un módulo o una extensión:

1. Descargue el archivo actualizado desde Marketplace u otro desarrollador de extensiones. Tome nota del nombre y la versión del módulo.

1. Exporte el contenido a su directorio de instalación raíz de Adobe Commerce o Magento Open Source.

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

## Extensiones agrupadas de proveedores (VBE)

Adobe eliminado todo [VBE](https://devdocs.magento.com/extensions/vendor/) en 2.4.4. Los proveedores siguen admitiendo estas extensiones en Adobe Commerce Marketplace.

Si desea seguir utilizando estas extensiones con Adobe Commerce y Magento Open Source 2.4.4 y versiones posteriores, debe actualizar las dependencias de paquete correspondientes en su `composer.json` file _before_ actualizar a 2.4.4. Póngase en contacto con el proveedor para obtener el nombre y la versión del paquete que va a usar.
