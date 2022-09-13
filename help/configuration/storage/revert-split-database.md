---
title: Revertir base de datos dividida
description: Revertir de una implementación de base de datos dividida obsoleta a una implementación de base de datos única.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# Revertir desde base de datos dividida

{{ee-only}}

Para los clientes de Adobe Commerce que han implementado [Dividir base de datos](multi-master.md), en el siguiente tema se describe cómo revertir o migrar de nuevo a una sola base de datos. Recomendamos a los comerciantes de Adobe Commerce que actualmente utilicen la base de datos dividida y que planifiquen actualizar a la versión 2.4.2 y posteriores que revisen estos pasos, así como nuestra [anuncio](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) sobre la desaprobación planificada de la base de datos dividida.

Para revertir de una base de datos dividida a una única base de datos, es necesario crear copias de seguridad de `magento_quote` y `magento_sales` bases de datos antes de cargarlas en el `magento_main` base de datos.

En este ejemplo, iniciamos sesión en las tres bases de datos, que están instaladas en el mismo host (`magento2-mysql`) como el usuario &quot;raíz&quot;. Debe reemplazar estos valores con los valores adecuados para sus bases de datos.

1. Cree una copia de seguridad de la variable `magento_quote` base de datos:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Cree una copia de seguridad de la variable `magento_sales` base de datos:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Cargue el `magento_quote` en la `magento_main` base de datos:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Cargue el `magento_sales` en la `magento_main` base de datos:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Suelte las `magento_sales` base de datos:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Suelte las `magento_quote` base de datos:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Elimine la configuración de implementación para `checkout` y `sales` en el `connections` y `resources` secciones de `env.php` archivo.
1. Restaurar claves externas:

   ```bash
   bin/magento setup:upgrade
   ```

## Verificar su trabajo

Para verificar que la implementación de la base de datos única funciona correctamente, realice las siguientes tareas y verifique que los datos se agreguen al `magento_main` tablas de base de datos utilizando una herramienta de base de datos como [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. Compruebe que se hayan restaurado las claves externas. Por ejemplo, la variable `QUOTE_STORE_ID_STORE_STORE_ID` en la variable `quote` tabla de base de datos.
1. Compruebe que los clientes pueden realizar pedidos desde la tienda.
1. Compruebe que los pedidos creados antes de revertir la base de datos dividida a una sola base de datos estén disponibles en el Administrador.
