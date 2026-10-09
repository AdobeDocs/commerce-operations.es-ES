---
title: Actualización de módulos y extensiones
description: Utilice la interfaz de línea de comandos y el Compositor para actualizar los módulos y las extensiones de Adobe Commerce.
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%
---
# Actualización de módulos y extensiones

Para actualizar o actualizar un módulo o una extensión:

1. Descargue el archivo actualizado desde Marketplace u otro desarrollador de extensiones. Tome nota del nombre y la versión del módulo.

1. Exporte el contenido al directorio de instalación raíz de Adobe Commerce.

1. Si existe un paquete Composer para el módulo, ejecute una de las siguientes acciones.

   Actualización por nombre de módulo:

   ```shell
   composer update vendor/module-name
   ```

   Actualización por versión:

   ```shell
   composer require vendor/module-name ^x.x.x
   ```

1. Ejecute los siguientes comandos para actualizar, implementar y limpiar la caché.

   ```shell
   bin/magento setup:upgrade --keep-generated
   ```

   ```shell
   bin/magento setup:static-content:deploy
   ```

   ```shell
   bin/magento cache:clean
   ```

## Extensiones agrupadas de proveedor (VBE)

Adobe eliminó todos los [VBE](/help/upgrade/modules/upgrade.md) en 2.4.4. Los proveedores siguen admitiendo estas extensiones en Adobe Commerce Marketplace.

Si desea seguir utilizando estas extensiones con Adobe Commerce 2.4.4 y versiones posteriores, debe actualizar las dependencias de paquete correspondientes en el archivo `composer.json` _antes_ de actualizar a 2.4.4. Póngase en contacto con el proveedor para obtener el nombre y la versión del paquete que desea utilizar.

Consulte los siguientes listados de Adobe Commerce Marketplace para obtener más información:

- [Amazon Pay](https://commercemarketplace.adobe.com//amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://commercemarketplace.adobe.com//dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://commercemarketplace.adobe.com//klarna-m2-klarna.html)
- [Vértice](https://commercemarketplace.adobe.com//vertexinc-vertex-tax-module.html)
- [Yotpo](https://commercemarketplace.adobe.com//yotpo-module-yotpo.html)
