---
title: Configurar automáticamente bases de datos maestras
description: Consulte las directrices sobre la configuración automática de la solución de base de datos dividida.
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# Configurar automáticamente bases de datos maestras

{{ee-only}}

{{deprecate-split-db}}

En este tema se explica cómo empezar a utilizar la solución de base de datos dividida mediante:

1. Instalación de Adobe Commerce con una sola base de datos maestra (denominada `magento`)
1. Creación de dos bases de datos maestras adicionales para retirada y OMS (denominadas `magento_quote` y `magento_sales`)
1. Configuración de Adobe Commerce para utilizar las bases de datos de cierre de compra y ventas

>[!INFO]
>
>Esta guía supone que las tres bases de datos están en el mismo host que la aplicación Commerce y que se denominan `magento`, `magento_quote` y `magento_sales`. Sin embargo, la elección de dónde ubicar las bases de datos y sus nombres depende de usted. Esperamos que nuestros ejemplos faciliten el seguimiento de las instrucciones.

## Instalación del software de Adobe Commerce

Puede activar las bases de datos divididas en cualquier momento después de instalar el software de Adobe Commerce; es decir, puede agregar bases de datos divididas a un sistema de Adobe Commerce que ya tiene datos de cierre de compra y pedidos. Utilice las instrucciones del archivo LÉAME de Adobe Commerce o la [guía de instalación](../../installation/overview.md) para instalar el software de Adobe Commerce mediante una única base de datos maestra.

## Configurar bases de datos maestras adicionales

Cree las bases de datos maestras de OMS y de cierre de compra de la siguiente manera:

1. Inicie sesión en el servidor de la base de datos como cualquier usuario.
1. Introduzca el siguiente comando para llegar al símbolo del sistema de MySQL:

   ```bash
   mysql -u root -p
   ```

1. Escriba la contraseña del usuario MySQL `root` cuando se le solicite.
1. Escriba los siguientes comandos en el orden mostrado para crear instancias de base de datos denominadas `magento_quote` y `magento_sales` con los mismos nombres de usuario y contraseñas:

   ```shell
   create database magento_quote;
   ```

   ```shell
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   ```

   ```shell
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Escriba `exit` para salir del símbolo del sistema.

1. Compruebe las bases de datos de una en una:

   Base de datos de extracción:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   Base de datos del sistema de Order Management:

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Si se muestra el monitor MySQL, ha creado correctamente la base de datos. Si aparece un error, repita los comandos anteriores.

## Configuración de Commerce para utilizar las bases de datos maestras

Después de configurar un total de tres bases de datos maestras, utilice la línea de comandos para configurar Commerce para que las utilice. (El comando configura conexiones de base de datos y distribuye tablas entre las bases de datos maestras.)

### Primeros pasos

Vea [Ejecutar comandos](../cli/config-cli.md#running-commands) para iniciar sesión y ejecutar comandos CLI.

### Configurar la base de datos de retirada

Sintaxis del comando:

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Por ejemplo,

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

Se muestra el siguiente mensaje para confirmar que la configuración se ha realizado correctamente:

```
Migration has been finished successfully!
```

### Configurar la base de datos de OMS

Sintaxis del comando:

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Por ejemplo,

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

```bash
bin/magento setup:upgrade
```

Se muestra el siguiente mensaje para confirmar que la configuración se ha realizado correctamente:

```
Migration has been finished successfully!
```
