---
title: Uso de déclencheur MySQL
description: Aprenda a utilizar los déclencheur MySQL de forma eficaz con Adobe Commerce.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 79a825a094a80892cf1a30aa7f5c61bd351c69f5
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---


# Prácticas recomendadas para el uso de déclencheur MySQL

Este artículo explica cómo evitar problemas de rendimiento al utilizar déclencheur MySQL. Los déclencheur se utilizan para registrar los cambios en las tablas de auditoría.

## Productos y versiones afectados

- Adobe Commerce local
- Adobe Commerce en infraestructura en la nube

>[!WARNING]
>
>Para Adobe Commerce en proyectos en la nube, pruebe siempre los cambios de configuración en el entorno de ensayo antes de cambiar la configuración para el entorno de producción.

## Comprender los impactos en el rendimiento

Los déclencheur se interpretan como código, lo que significa que MySQL no los precompila.

Al enganchar el espacio de transacciones de la consulta, los déclencheur añaden sobrecarga a un analizador e intérprete para cada consulta realizada con la tabla. Los déclencheur comparten el mismo espacio de transacción que las consultas originales y, mientras que esas consultas compiten por los bloqueos de la tabla, los déclencheur compiten de forma independiente por los bloqueos de otra tabla.

Esta sobrecarga adicional puede afectar negativamente al rendimiento del sitio si se utilizan muchos déclencheur.

>[!WARNING]
>
>Adobe Commerce no admite ningún déclencheur personalizado en la base de datos de Adobe Commerce porque los déclencheur personalizados pueden provocar incompatibilidades con versiones futuras de Adobe Commerce. Para conocer las prácticas recomendadas, consulte [Directrices generales de MySQL](../../../installation/prerequisites/database/mysql.md) en la documentación de Adobe Commerce.

## Usar déclencheur de forma eficaz

Para evitar problemas de rendimiento al usar déclencheur, siga estas directrices:

- Si tiene déclencheur personalizados que escriben algunos datos cuando se ejecuta el déclencheur, mueva esta lógica para escribir directamente en las tablas de auditoría. Por ejemplo, añadiendo una consulta adicional en el código de la aplicación, después de la consulta para la que pretendía crear el déclencheur.
- Revise los déclencheur personalizados existentes y considere la posibilidad de eliminarlos y escribirlos directamente en las tablas desde la aplicación. Compruebe los déclencheur existentes en la base de datos utilizando la variable [`SHOW TRIGGERS` Instrucción SQL](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Para obtener asistencia adicional, preguntas o inquietudes, [enviar un ticket de asistencia de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Información adicional

- [Requisitos previos de MySQL](../../../installation/prerequisites/database/mysql.md)
- [Prácticas recomendadas de bases de datos para Adobe Commerce en infraestructura en la nube](database-on-cloud.md)
