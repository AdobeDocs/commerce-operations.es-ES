---
title: Verificar base de datos dividida
description: Obtenga información sobre cómo verificar que una configuración de base de datos dividida en comercio funciona correctamente.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# Verificar base de datos dividida

{{ee-only}}

{{deprecate-split-db}}

Después de la configuración, las bases de datos maestras se configuran de la siguiente manera:

- Base de datos de comercio principal: 369 cuadros
- Base de datos de ofertas de comercio: 11 cuadros
- Base de datos de ventas comerciales: 55 tablas

Para comprobar que las bases de datos divididas funcionan correctamente, realice las siguientes tareas y verifique que los datos se agreguen a las tablas de la base de datos con una herramienta de base de datos como [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| Qué verificar | Comprobar |
| -------------- | ------------- |
| la base de datos de comillas funciona | Agregar elementos a un carro de compras. Verifique que se hayan agregado filas a la base de datos de presupuesto `quote`, `quote_address`y `quote_item` tablas. |
| la base de datos de ventas está funcionando | Realizar un pedido (cualquier forma de pago, incluyendo cheque/giro). Verifique que se hayan agregado filas a la base de datos de ventas `sales_order_address`, `sales_order_item`y `sales_order_payment` tablas. |

>[!WARNING]
>
>Debe realizar una copia de seguridad de las dos instancias de base de datos adicionales manualmente. Commerce realiza una copia de seguridad solo de la instancia de base de datos principal. La variable [`magento setup:backup --db`](../../installation/tutorials/backup.md) las opciones de comando y administración no hacen una copia de seguridad de las tablas adicionales.
