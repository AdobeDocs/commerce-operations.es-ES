---
title: Cambiar ID de incremento
description: Cambiar el ID de incremento de una entidad de la base de datos de Commerce.
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Cambiar ID de incremento

Este artículo explica cómo cambiar el ID de incremento de una entidad de la base de datos de Commerce (BD) (pedido, factura, nota de crédito, etc.) en un almacén de Commerce determinado mediante `ALTER TABLE` Instrucción SQL.

## Versiones afectadas

- Adobe Commerce (local): 2.x.x
- Adobe Commerce en infraestructura en la nube: 2.x.x
- MySQL: [cualquier versión compatible](../../installation/prerequisites/database/mysql.md)

## ¿Cuándo necesita cambiar el ID de incremento?

Es posible que tenga que cambiar el ID de incremento de las nuevas entidades de base de datos en estos casos:

- Después de una restauración de copia de seguridad en disco duro en un sitio activo
- Se han perdido algunos registros de pedidos, pero sus ID ya están siendo utilizados por las puertas de enlace de pago (como PayPal) para su cuenta de comerciante actual. Siendo así, las puertas de enlace de pago dejan de procesar nuevos pedidos que tienen los mismos ID, devolviendo el error &quot;ID de factura duplicado&quot;

>[!INFO]
>
>También puedes solucionar el problema de la pasarela de pago de PayPal permitiendo varios pagos por ID de factura en las Preferencias de recepción de pagos de PayPal. Consulte [Solicitud rechazada de puerta de enlace de PayPal: emisión de factura duplicada] en el _Base de conocimiento_.

## Pasos previos necesarios

1. Busque tiendas y entidades para las que se debe cambiar el nuevo ID de incremento.
1. Conéctese a su base de datos MySQL.
Para Adobe Commerce en la infraestructura en la nube, al principio, debe conectarse usando SSH a su entorno.
1. Compruebe el actual `auto_increment` para la tabla de secuencia de entidades mediante la siguiente consulta:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Si está comprobando un incremento automático para un pedido en el almacén con ID=1, el nombre de la tabla sería &quot;sequence_order_1&quot;.

Si el valor de `auto_increment` es &quot;1234&quot;, el siguiente pedido realizado en la tienda con `ID=1` tendrá el ID &quot;#100001234&quot;.

## Actualizar entidad para cambiar el ID de incremento

Actualice la entidad con la siguiente consulta:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
Importante: El nuevo valor de incremento debe ser bueno al actual.

Después de ejecutar la siguiente consulta:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

El siguiente pedido realizado en la tienda con `ID=1` tendrá el ID &quot;#100002000&quot;.

## Pasos adicionales recomendados en entornos de producción en la nube

Antes de ejecutar `ALTER TABLE` consulte en un entorno de producción de Adobe Commerce en la infraestructura en la nube y le recomendamos encarecidamente que siga estos pasos:

- Pruebe todo el procedimiento para cambiar el ID de incremento en el entorno de ensayo
- [Creación de una copia de seguridad DB] para restaurar la base de datos de producción en caso de error

<!-- Link Definitions -->

[Solicitud rechazada de puerta de enlace de PayPal: emisión de factura duplicada]: https://support.magento.com/hc/en-us/articles/115002457473
[Creación de una copia de seguridad DB]: https://support.magento.com/hc/en-us/articles/360003254334
[cualquier versión compatible]
