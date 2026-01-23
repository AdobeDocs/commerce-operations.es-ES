---
title: Implementación de una sola máquina
description: Obtenga información sobre cómo implementar actualizaciones en Commerce en un servidor de producción mediante la línea de comandos.
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '180'
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

   ```bash
   cd <Commerce base directory>
   ```

1. Habilite el modo de mantenimiento con el comando:

   ```bash
   bin/magento maintenance:enable
   ```

1. Aplique actualizaciones a Commerce o a sus componentes mediante el siguiente patrón de comandos:

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **paquete**: El nombre del paquete que desea actualizar.

   Por ejemplo:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **versión**: La versión de destino del paquete que desea actualizar.

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

