---
title: Implementación de una sola máquina
description: Obtenga información sobre cómo implementar actualizaciones en Commerce en un servidor de producción mediante la línea de comandos.
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
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
source-wordcount: '189'
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

