---
title: Verificar base de datos dividida
description: Obtenga información sobre cómo comprobar que una configuración de base de datos dividida de Commerce funciona correctamente.
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Verificar base de datos dividida

{{ee-only}}

{{deprecate-split-db}}

Después de la configuración, las bases de datos maestras se configuran de la siguiente manera:

- Base de datos principal de Commerce: 369 tablas
- Base de datos de Commerce quote: 11 tablas
- Base de datos de ventas de Commerce: 55 tablas

Para comprobar que las bases de datos divididas funcionan correctamente, realice las siguientes tareas y compruebe que los datos se agregan a las tablas de base de datos con una herramienta de base de datos como [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| Qué se debe verificar | Cómo verificar |
| -------------- | ------------- |
| la base de datos quote funciona | Agregar elementos a un carro de compras. Compruebe que se han agregado filas a las tablas `quote`, `quote_address` y `quote_item` de la base de datos de ofertas. |
| la base de datos de ventas funciona | Complete un pedido (cualquier forma de pago, incluido el cheque o giro postal). Compruebe que se han agregado filas a las tablas `sales_order_address`, `sales_order_item` y `sales_order_payment` de la base de datos de ventas. |

>[!WARNING]
>
>Debe realizar una copia de seguridad de las dos instancias de base de datos adicionales manualmente. Commerce realiza una copia de seguridad solo de la instancia de base de datos principal. El comando [`magento setup:backup --db`](../../installation/tutorials/backup.md) y las opciones de administración no hacen una copia de seguridad de las tablas adicionales.
