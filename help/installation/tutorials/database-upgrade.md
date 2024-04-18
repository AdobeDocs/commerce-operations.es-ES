---
title: Actualizar el esquema y los datos de la base de datos
description: Siga estos pasos para actualizar el esquema de la base de datos de Adobe Commerce.
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Actualizar el esquema y los datos de la base de datos

Antes de utilizar este comando, debe [instalar la aplicación](../advanced.md).

## Actualizar el esquema y los datos de la base de datos

Cada vez que realice una acción que provoque cambios en el esquema o los datos de la base de datos, debe actualizarlos ejecutando el comando que se describe en esta sección. A continuación se ofrece una lista parcial de motivos:

* Ha actualizado la aplicación mediante la línea de comandos
* Ha instalado o actualizado un componente mediante la línea de comandos
* Ha habilitado o deshabilitado un componente mediante la línea de comandos

>[!NOTE]
>
>A *componente* puede ser un módulo, una temática o un paquete de idioma; no importa si el componente procede del Commerce Marketplace o no.

1. Inicie la actualización:

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Donde `--keep-generated` es un argumento opcional que no se actualiza [archivos de vista estática](../../configuration/cli/static-view-file-deployment.md). Este argumento opcional es para uso *solamente* en circunstancias limitadas por integradores de sistemas experimentados. Debe usarse. *solamente* in [modo de producción](../../configuration/bootstrap/application-modes.md#production-mode). Debería *no* se utilizará en [modo de desarrollador](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Limpie la caché:

   ```bash
   bin/magento cache:clean
   ```
