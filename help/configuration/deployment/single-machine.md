---
title: Implementación de una sola máquina
description: Obtenga información sobre cómo implementar actualizaciones en Commerce en un servidor de producción mediante la línea de comandos.
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 1%

---

# Implementación de un solo equipo

En este tema se proporcionan instrucciones para implementar actualizaciones en Commerce en un servidor de producción mediante la línea de comandos. Este proceso se aplica a los usuarios técnicos responsables de las tiendas que se ejecutan en un solo equipo con algunos temas y configuraciones regionales instalados.

## Suposiciones

- Ha instalado Commerce con [Composer](../../installation/composer.md).
- Está aplicando actualizaciones directamente al servidor.

>[!WARNING]
>
>Esta guía no se aplica si utilizó `git clone` para instalar Commerce.
>Los desarrolladores colaboradores deben usar [esta guía](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies) para actualizar su instalación de Commerce.

## Pasos de implementación

1. Inicie sesión en el servidor de producción como [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md) o cambie a él.

1. Cambie al directorio base de Commerce:

   ```shell
   cd <Commerce base directory>
   ```

1. Habilite el modo de mantenimiento con el comando:

   ```shell
   bin/magento maintenance:enable
   ```

1. Aplique actualizaciones a Commerce o a sus componentes mediante el siguiente patrón de comandos:

   ```shell
   composer require-commerce <package> <version> --no-update
   ```

   **paquete**: El nombre del paquete que desea actualizar.

   Por ejemplo:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **versión**: La versión de destino del paquete que desea actualizar.

1. Actualizar componentes con Composer:

   ```shell
   composer update
   ```

1. Actualizar el esquema y los datos de la base de datos:

   ```shell
   bin/magento setup:upgrade
   ```

1. Compile el código:

   ```shell
   bin/magento setup:di:compile
   ```

1. Implementar contenido estático:

   ```shell
   bin/magento setup:static-content:deploy
   ```

1. Limpie la caché:

   ```shell
   bin/magento cache:clean
   ```

1. Salir del modo de mantenimiento:

   ```shell
   bin/magento maintenance:disable
   ```

