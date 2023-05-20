---
title: Revertir base de datos dividida
description: Revertir de una implementación de base de datos dividida en desuso a una implementación de base de datos única.
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Revertir desde base de datos dividida

{{ee-only}}

Para clientes de Adobe Commerce que han implementado [Dividir base de datos](multi-master.md), en el siguiente tema se describe cómo revertir o volver a migrar a una única base de datos. Recomendamos que los comerciantes de Adobe Commerce que actualmente utilizan la base de datos dividida y planean actualizar a la versión 2.4.2 y posteriores revisen estos pasos, así como nuestras [anuncio](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) sobre la obsolescencia planificada de la base de datos dividida.

La reversión de una base de datos dividida a una única base de datos implica la creación de copias de seguridad de la `magento_quote` y `magento_sales` bases de datos antes de cargarlas en el `magento_main` base de datos.

En este ejemplo, iniciamos sesión en las tres bases de datos, que están instaladas en el mismo host (`magento2-mysql`) como usuario &quot;raíz&quot;. Debe reemplazar estos valores con los valores adecuados para las bases de datos.

1. Cree una copia de seguridad del `magento_quote` base de datos:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Cree una copia de seguridad del `magento_sales` base de datos:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Cargue el `magento_quote` en la base de datos `magento_main` base de datos:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Cargue el `magento_sales` en la base de datos `magento_main` base de datos:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Suelte el `magento_sales` base de datos:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Suelte el `magento_quote` base de datos:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Elimine la configuración de implementación para `checkout` y `sales` en el `connections` y `resources` secciones de la `env.php` archivo.
1. Restaurar claves externas:

   ```bash
   bin/magento setup:upgrade
   ```

## Verifique su trabajo

Para comprobar que la implementación de una base de datos única funciona correctamente, realice las siguientes tareas y compruebe que los datos se agregan a `magento_main` tablas de base de datos con una herramienta de base de datos como [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. Compruebe que se hayan restaurado las claves externas. Por ejemplo, la variable `QUOTE_STORE_ID_STORE_STORE_ID` clave en el `quote` tabla de base de datos.
1. Compruebe que los clientes pueden realizar pedidos desde la tienda.
1. Compruebe que los pedidos creados antes de revertir la base de datos dividida a una única base de datos están disponibles en el Administrador.
