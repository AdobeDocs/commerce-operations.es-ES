---
title: Cambiar ID de incremento
description: Cambie el ID de incremento para una entidad de la base de datos de comercio.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# Cambiar ID de incremento

En este artículo se explica cómo cambiar el ID de incremento de una entidad de la base de datos de comercio (DB) (pedido, factura, nota de crédito, etc.) en un almacén de comercio concreto mediante el uso de la variable `ALTER TABLE` instrucción SQL.

## Versiones afectadas

- Adobe Commerce (local): 2.x.x
- Adobe Commerce en infraestructura de nube: 2.x.x
- MySQL: [cualquier versión compatible](../../installation/prerequisites/database/mysql.md)

## ¿Cuándo necesita cambiar el ID de incremento?

Puede que necesite cambiar el ID de incremento para nuevas entidades de base de datos en estos casos:

- Después de una restauración de copia de seguridad en un sitio en vivo
- Algunos registros de pedidos se han perdido, pero sus ID ya están siendo utilizados por las puertas de enlace de pago (como PayPal) para su cuenta comercial actual. En este caso, las puertas de enlace de pago dejan de procesar nuevos pedidos que tengan los mismos ID y devuelven el error &quot;ID de factura duplicada&quot;

>[!INFO]
>
>También puede solucionar el problema de la puerta de enlace de pago para PayPal permitiendo múltiples pagos por ID de factura en Preferencias de Recepción de Pagos de PayPal. Consulte [Solicitud rechazada de puerta de enlace de PayPal: problema de factura duplicada] en el _Base de conocimientos_.

## Pasos previos

1. Busque tiendas y entidades para las que se debe cambiar el nuevo ID de incremento.
1. Conéctese a la base de datos MySQL.
Para Adobe Commerce en infraestructura de nube, al principio debe conectarse mediante SSH a su entorno.
1. Compruebe el `auto_increment` para la tabla de secuencia de entidades utilizando la siguiente consulta:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Si está comprobando un incremento automático de un pedido en la tienda con ID=1, el nombre de la tabla sería &quot;sequence_order_1&quot;.

Si el valor de la variable `auto_increment` es &quot;1234&quot;, el siguiente pedido se coloca en la tienda con `ID=1` tendrá el ID &quot;#100001234&quot;.

## Actualizar entidad para cambiar el ID de incremento

Actualice la entidad con la siguiente consulta:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
Importante: El nuevo valor de incremento debe ser bueno que el actual.

Después de ejecutar la siguiente consulta:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

El siguiente pedido se coloca en la tienda con `ID=1` tendrá el ID &quot;#100002000&quot;.

## Pasos recomendados adicionales para entornos de producción en la nube

Antes de ejecutar el `ALTER TABLE` en un entorno de producción de Adobe Commerce en la infraestructura de la nube, se recomienda realizar estos pasos:

- Pruebe todo el procedimiento para cambiar el ID de incremento en el entorno de ensayo
- [Crear una copia de seguridad de base de datos] para restaurar la base de datos de producción en caso de error

<!-- Link Definitions -->

[Solicitud rechazada de puerta de enlace de PayPal: problema de factura duplicada]: https://support.magento.com/hc/en-us/articles/115002457473
[Crear una copia de seguridad de base de datos]: https://support.magento.com/hc/en-us/articles/360003254334
[cualquier versión compatible]
