---
title: Configuración automática de bases de datos maestras
description: Consulte las directrices sobre la configuración automática de la solución de base de datos dividida.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 1%

---


# Configuración automática de bases de datos maestras

{{ee-only}}

{{deprecate-split-db}}

En este tema se explica cómo empezar a utilizar la solución de división de bases de datos mediante:

1. Instalación de Adobe Commerce con una sola base de datos maestra (denominada `magento`)
1. Creación de dos bases de datos maestras adicionales para [cierre de compra](https://glossary.magento.com/checkout) y OMS (nombre `magento_quote` y `magento_sales`)
1. Configuración de Adobe Commerce para utilizar las bases de datos de cierre de compra y ventas

>[!INFO]
>
>Esta guía asume que las tres bases de datos están en el mismo host que la aplicación Commerce y que tienen su nombre `magento`, `magento_quote`y `magento_sales`. Sin embargo, usted puede elegir dónde ubicar las bases de datos y cómo se denominan. Esperamos que nuestros ejemplos hagan que las instrucciones sean más fáciles de seguir.

## Instalación del software de Adobe Commerce

Puede habilitar bases de datos divididas en cualquier momento después de instalar el software de Adobe Commerce; en otras palabras, puede agregar bases de datos divididas a un sistema de Adobe Commerce que ya tenga datos de cierre de compra y pedido. Utilice las instrucciones de Adobe Commerce README o la [guía de instalación](../../installation/overview.md) para instalar el software de Adobe Commerce utilizando una única base de datos maestra.

## Configuración de bases de datos maestras adicionales

Cree las bases de datos maestras de cierre de compra y OMS de la siguiente manera:

1. Inicie sesión en el servidor de la base de datos como cualquier usuario.
1. Introduzca el siguiente comando para llegar al símbolo del sistema MySQL:

   ```bash
   mysql -u root -p
   ```

1. Introduzca el MySQL `root` contraseña del usuario cuando se le pida.
1. Introduzca los siguientes comandos en el orden mostrado para crear instancias de base de datos con el nombre `magento_quote` y `magento_sales` con los mismos nombres de usuario y contraseñas:

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

1. Entrar `exit` para salir del símbolo del sistema.

1. Compruebe las bases de datos de una en una:

   Base de datos de cierre de compra:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   Base de datos del sistema de gestión de pedidos:

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Si aparece el monitor MySQL, ha creado la base de datos correctamente. Si aparece un error, repita los comandos anteriores.

## Configuración de Commerce para utilizar las bases de datos maestras

Después de configurar un total de tres bases de datos maestras, utilice la línea de comandos para configurar Commerce para utilizarlas. (El comando configura conexiones de base de datos y distribuye tablas entre las bases de datos maestras).

### Primeros pasos

Consulte [Ejecución de comandos](../cli/config-cli.md#running-commands) para iniciar sesión y ejecutar comandos CLI.

### Configuración de la base de datos de cierre de compra

Sintaxis de comandos:

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Por ejemplo,

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

Se muestra el siguiente mensaje para confirmar que la configuración se ha realizado correctamente:

```terminal
Migration has been finished successfully!
```

### Configuración de la base de datos OMS

Sintaxis de comandos:

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Por ejemplo,

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

Se muestra el siguiente mensaje para confirmar que la configuración se ha realizado correctamente:

```terminal
Migration has been finished successfully!
```
