---
title: Implementación de una sola máquina
description: Obtenga información sobre cómo implementar actualizaciones en Commerce en un servidor de producción mediante la línea de comandos.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# Implementación de una sola máquina

En este tema se proporcionan instrucciones para implementar actualizaciones en Commerce en un servidor de producción mediante la línea de comandos. Este proceso se aplica a los usuarios técnicos responsables de las tiendas que se ejecutan en un solo equipo con algunos temas y configuraciones regionales instalados.

## Suposiciones

- Ha instalado Commerce utilizando [Compositor].
- Está aplicando actualizaciones directamente al servidor.

>[!WARNING]
>
>Esta guía no se aplica si ha utilizado `git clone` para instalar Commerce.
>Los desarrolladores colaboradores deben utilizar [esta guía][install] para actualizar su instalación de Commerce.

## Pasos de implementación

1. Inicie sesión en el servidor de producción como o cambie a la [propietario del sistema de archivos][file-owner].

1. Cambie el directorio al directorio base de Commerce:

   ```bash
   cd <Commerce base directory>
   ```

1. Habilite el modo de mantenimiento mediante el comando :

   ```bash
   bin/magento maintenance:enable
   ```

1. Aplique actualizaciones a Commerce o sus componentes mediante el siguiente patrón de comandos:

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **paquete**: El nombre del paquete que desea actualizar.

   Por ejemplo:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **version**: La versión de destino del paquete que desea actualizar.

1. Actualizar componentes con el Compositor:

   ```bash
   composer update
   ```

1. Actualice el esquema y los datos de la base de datos:

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

1. Modo de mantenimiento de salida:

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/
[composer]: ../../installation/composer.md
[file-owner]: ../../installation/prerequisites/file-system/overview.md
