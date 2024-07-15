---
title: Revertir base de datos dividida
description: Revertir de una implementación de base de datos dividida en desuso a una implementación de base de datos única.
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Revertir desde base de datos dividida

{{ee-only}}

Para los clientes de Adobe Commerce que han implementado [Split Database](multi-master.md), en el siguiente tema se describe cómo revertir o volver a migrar a una sola base de datos. Recomendamos a los comerciantes de Adobe Commerce que actualmente usan la base de datos dividida y planean actualizar a la versión 2.4.2 y posteriores y revisar estos pasos, así como nuestro [anuncio](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) sobre la obsolescencia planeada de la base de datos dividida.

La reversión de una base de datos dividida a una única base de datos implica la creación de copias de seguridad de las bases de datos `magento_quote` y `magento_sales` antes de cargarlas en la única base de datos `magento_main`.

En este ejemplo, iniciamos sesión en las tres bases de datos, que están instaladas en el mismo host (`magento2-mysql`) que el usuario &quot;raíz&quot;. Debe reemplazar estos valores con los valores adecuados para las bases de datos.

1. Crear una copia de seguridad de la base de datos `magento_quote`:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Crear una copia de seguridad de la base de datos `magento_sales`:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Cargar la base de datos `magento_quote` en la base de datos `magento_main`:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Cargar la base de datos `magento_sales` en la base de datos `magento_main`:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Soltar la base de datos `magento_sales`:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Soltar la base de datos `magento_quote`:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Quite la configuración de implementación para `checkout` y `sales` en las secciones `connections` y `resources` del archivo `env.php`.
1. Restaurar claves externas:

   ```bash
   bin/magento setup:upgrade
   ```

## Verifique su trabajo

Para comprobar que la implementación de la base de datos única funciona correctamente, realice las siguientes tareas y compruebe que los datos se agregan a las tablas de base de datos de `magento_main` mediante una herramienta de base de datos como [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. Compruebe que se hayan restaurado las claves externas. Por ejemplo, la clave `QUOTE_STORE_ID_STORE_STORE_ID` de la tabla de base de datos `quote`.
1. Compruebe que los clientes pueden realizar pedidos desde la tienda.
1. Compruebe que los pedidos creados antes de revertir la base de datos dividida a una única base de datos están disponibles en el Administrador.
