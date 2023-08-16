---
title: Varios sitios web o tiendas
description: Descubra cómo puede iniciar varios sitios web o implementar vistas de tiendas con diferentes opciones, dominios y contenido.
exl-id: 724d75d9-13fc-40f9-951a-69aa407adb6f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Varios sitios web o tiendas

Una sola instancia del software de Adobe Commerce le permite iniciar varios sitios web o almacenar vistas que utilizan atributos y contenido diferentes, como:

- Idiomas predeterminados
- Nombres de dominio
- Categorías
- Productos
- Divisas

Esta solución flexible permite que un administrador y un código de Commerce administren y muestren diferentes tiendas. Puede configurar los sitios web, las tiendas y las vistas de las tiendas en el Administrador de. Utilice determinadas variables en hosts virtuales para iniciar la aplicación de Commerce mediante estos sitios web o vistas de tiendas.

Un uso típico es configurar tiendas con diferentes opciones en diferentes dominios. Por ejemplo, puede tener un conjunto de categorías y productos en un dominio y otro conjunto de categorías y productos en un dominio independiente en un idioma diferente.

Puede configurar los sitios web, las tiendas y las vistas de las tiendas en el administrador de Commerce. Utilice el `MAGE_RUN_TYPE` y `MAGE_RUN_CODE` en hosts virtuales para iniciar la aplicación de Commerce mediante estos sitios web o vistas de tiendas.

Tenga en cuenta los siguientes términos:

- **Sitio web**: es el contenedor de nivel superior para sitios, métodos de envío, métodos de pago y mucho más. Para crear sitios completamente independientes que no compartan el carro de compras, los métodos de envío u otros, debe crear sitios web independientes.

  Las cuentas de cliente del sitio web se pueden compartir entre varios sitios web dentro de una sola instancia de Commerce. Un sitio web contiene al menos una tienda. Los precios de catálogo deben gestionarse a nivel de sitio web.

- **Almacenar**: se encuentra en un sitio web. A su vez, una tienda contiene al menos una *vista de tienda*.

  Varias tiendas pueden compartir el carro de compras, sesiones de usuarios, puertas de enlace de pago y mucho más, pero tienen estructuras de catálogo y precios de catálogo independientes.

  La cantidad de catálogo (inventario) no se puede administrar en el nivel de tienda. El inventario solo se administra en el nivel del sitio web o global.

  Las vistas de tienda cambian la forma en que se presentan las páginas y, por lo general, se utilizan para mostrar una tienda con diferentes diseños o idiomas. Puede administrar distintas monedas por vista de tienda.

  Cada sitio web y cada vista de tienda deben tener un identificador único. Este identificador es necesario para utilizar `MAGE_RUN_TYPE` y `MAGE_RUN_CODE` como se indica a continuación:

- `MAGE_RUN_TYPE` puede ser `store` o `website`

   - Uso `website` para cargar un sitio web en la tienda.
   - Uso `store` para cargar cualquier vista de tienda en tu tienda.

- `MAGE_RUN_CODE` es el sitio web único o el código de vista de tienda que corresponde a `MAGE_RUN_TYPE`

A continuación se muestra un resumen de las tareas que debe realizar:

1. [Configure sitios web, tiendas y vistas de tiendas en el Administrador de.](ms-admin.md)
1. Cree un host virtual para cargar muchos sitios web o un host virtual por sitio web de Commerce o vista de tienda para permitir directivas específicas para cada tienda.
1. Pasar los valores de `MAGE_RUN_TYPE` y `MAGE_RUN_CODE` al servidor web.
