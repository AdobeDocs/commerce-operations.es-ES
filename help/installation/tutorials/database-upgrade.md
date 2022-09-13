---
title: Actualización del esquema y los datos de la base de datos
description: Siga estos pasos para actualizar el esquema de la base de datos de Adobe Commerce o Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Actualización del esquema y los datos de la base de datos

Antes de utilizar este comando, debe [instalar la aplicación](../advanced.md).

## Actualización del esquema y los datos de la base de datos

Siempre que realice una acción que provoque el [esquema de base de datos](https://glossary.magento.com/database-schema) Para que los datos cambien, debe actualizarlos ejecutando el comando discutido en esta sección. A continuación se ofrece una lista parcial de motivos:

* Ha actualizado la aplicación utilizando la línea de comandos
* Ha instalado o actualizado un componente mediante la línea de comandos
* Ha habilitado o deshabilitado un componente mediante la línea de comandos

>[!NOTE]
>
>A *componente* puede ser un módulo, tema o paquete de idioma; no importa si el componente viene del Commerce Marketplace o no.

1. Inicie la actualización:

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Donde `--keep-generated` es un argumento opcional que no se actualiza [archivos de vista estáticos](../../configuration/cli/static-view-file-deployment.md). Este argumento opcional es para su uso *only* en circunstancias limitadas por integradores de sistemas experimentados. Debe usarse *only* en [modo de producción](../../configuration/bootstrap/application-modes.md#production-mode). Debería *not* para usar en [modo de desarrollador](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Limpie la caché:

   ```bash
   bin/magento cache:clean
   ```
