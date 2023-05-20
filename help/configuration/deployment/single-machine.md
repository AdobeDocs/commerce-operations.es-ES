---
title: Implementación de una sola máquina
description: Obtenga información sobre cómo implementar actualizaciones en Commerce en un servidor de producción mediante la línea de comandos.
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Implementación de un solo equipo

En este tema se proporcionan instrucciones para implementar actualizaciones en Commerce en un servidor de producción mediante la línea de comandos. Este proceso se aplica a los usuarios técnicos responsables de las tiendas que se ejecutan en un solo equipo con algunos temas y configuraciones regionales instalados.

## Suposiciones

- Ha instalado Commerce con [Compositor](../../installation/composer.md).
- Está aplicando actualizaciones directamente al servidor.

>[!WARNING]
>
>Esta guía no se aplica si ha utilizado `git clone` para instalar Commerce.
>Los desarrolladores colaboradores deben utilizar [esta guía][install] para actualizar su instalación de Commerce.

## Pasos de implementación

1. Inicie sesión en el servidor de producción como, o cambie a, la [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).

1. Cambie el directorio al directorio base de Commerce:

   ```bash
   cd <Commerce base directory>
   ```

1. Habilite el modo de mantenimiento con el comando:

   ```bash
   bin/magento maintenance:enable
   ```

1. Aplique actualizaciones a Commerce o sus componentes mediante el siguiente patrón de comandos:

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **paquete**: Nombre del paquete que desea actualizar.

   Por ejemplo:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **version**: La versión de destino del paquete que desea actualizar.

1. Actualizar componentes con Composer:

   ```bash
   composer update
   ```

1. Actualizar el esquema y los datos de la base de datos:

   ```bash
   bin/magento setup:upgrade
   ```

1. Compile el código:

   ```bash
   bin/magento setup:di:compile
   ```

1. Implementar contenido estático:

   ```bash
   bin/magento setup:static-content:deploy
   ```

1. Limpie la caché:

   ```bash
   bin/magento cache:clean
   ```

1. Salir del modo de mantenimiento:

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/
