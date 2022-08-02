---
title: Múltiples sitios web o tiendas
description: Aprenda cómo iniciar varios sitios web o implementar vistas de tiendas con diferentes opciones, dominios y contenido.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---


# Múltiples sitios web o tiendas

Una sola instancia del software de Adobe Commerce permite iniciar varios sitios web o almacenar vistas que utilicen atributos y contenido diferentes, como:

- Idiomas predeterminados
- Nombres de dominio
- Categorías
- Productos
- Monedas

Esta solución flexible permite un código de base de comercio y [Administrador](https://glossary.magento.com/magento-admin) para administrar y mostrar diferentes tiendas. Los sitios web, las tiendas y las vistas de las tiendas se configuran en Administración. Utilice ciertas variables en los hosts virtuales para iniciar la aplicación de comercio con estos sitios web o vistas de tienda.

Un uso habitual es configurar tiendas con diferentes opciones en distintos dominios. Por ejemplo, puede tener un conjunto de categorías y productos en un dominio y otro conjunto de categorías y productos en un dominio separado en un idioma diferente.

Los sitios web, las tiendas y las vistas de las tiendas se configuran en Comercio [Administrador](https://glossary.magento.com/admin). Utilice la variable `MAGE_RUN_TYPE` y `MAGE_RUN_CODE` en hosts virtuales para iniciar la aplicación Commerce con estos sitios web o vistas de tienda.

Tenga en cuenta los siguientes términos:

- **Sitio web**: es el contenedor de nivel superior para sitios, métodos de envío, métodos de pago y mucho más. Para crear sitios completamente separados que no compartan carro, métodos de envío u otros, debe crear sitios web independientes.

   Las cuentas de cliente de sitio web se pueden compartir entre varios sitios web dentro de una sola instancia de Commerce. Un sitio web contiene al menos una tienda. Los precios del catálogo deben administrarse a nivel de sitio web.

- **Tienda**—está contenido en un sitio web. A su vez, una tienda contiene al menos una *vista de tienda*.

   Varias tiendas pueden compartir carros, sesiones de usuario, puertas de enlace de pago y mucho más, pero tienen estructuras de catálogo y precio de catálogo independientes.

   La cantidad del catálogo (inventario) no se puede administrar en el nivel de tienda. El inventario se administra solo en el sitio web o a nivel global.

   Las vistas de la tienda cambian la forma en que se presentan las páginas y, por lo general, se utilizan para mostrar una tienda con diferentes diseños o idiomas. Puede administrar distintas monedas por vista de tienda.

   Cada sitio web y cada vista de tienda deben tener un identificador único. Este identificador es necesario para utilizar la variable `MAGE_RUN_TYPE` y `MAGE_RUN_CODE` de la siguiente manera:

- `MAGE_RUN_TYPE` puede `store` o `website`

   - Uso `website` para cargar un sitio web en tu tienda.
   - Uso `store` para cargar cualquier vista de tienda en tu tienda.

- `MAGE_RUN_CODE` es el código de vista de tienda o sitio web único que corresponde a `MAGE_RUN_TYPE`

A continuación se muestra un resumen de las tareas que debe realizar:

1. [Configure sitios web, tiendas y vistas de tienda en Administración.](ms-admin.md)
1. Cree un host virtual para cargar muchos sitios web o un host virtual por cada sitio web de comercio o vista de tienda para permitir directivas específicas para cada tienda.
1. Transfiera los valores de `MAGE_RUN_TYPE` y `MAGE_RUN_CODE` al servidor web.
