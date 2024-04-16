---
title: Actualización de módulos y extensiones
description: Utilice la interfaz de línea de comandos y el Compositor para actualizar los módulos y las extensiones de Adobe Commerce.
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# Actualización de módulos y extensiones

Para actualizar o actualizar un módulo o una extensión:

1. Descargue el archivo actualizado desde Marketplace u otro desarrollador de extensiones. Tome nota del nombre y la versión del módulo.

1. Exporte el contenido al directorio de instalación raíz de Adobe Commerce o de Magento Open Source.

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

## Extensiones agrupadas de proveedor (VBE)

Adobe eliminado todo [VBE](https://devdocs.magento.com/extensions/vendor/) en 2.4.4. Los proveedores siguen admitiendo estas extensiones en Adobe Commerce Marketplace.

Si desea seguir utilizando estas extensiones con Adobe Commerce 2.4.4 y versiones posteriores, debe actualizar las dependencias de paquete correspondientes en su `composer.json` archivo _antes_ actualización a 2.4.4. Póngase en contacto con el proveedor para obtener el nombre y la versión del paquete que desea utilizar.

Consulte los siguientes listados de Adobe Commerce Marketplace para obtener más información:

- [Amazon Pay](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html)
- [Vértice](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [Yotpo](https://marketplace.magento.com/yotpo-module-yotpo.html)
