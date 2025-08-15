---
title: Prácticas recomendadas para modificar tablas de base de datos
description: Obtenga información sobre cómo y cuándo modificar tablas de bases de datos de Adobe Commerce y de terceros.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 0%

---

# Prácticas recomendadas para modificar tablas de base de datos

Este artículo proporciona prácticas recomendadas para modificar tablas de base de datos creadas por [!DNL Adobe Commerce] o módulos de terceros. Comprender cuándo y cómo modificar tablas de forma eficaz ayuda a garantizar la viabilidad y estabilidad a largo plazo de su plataforma de comercio.

Migrar desde [!DNL Magento 1] y otras plataformas de comercio electrónico, o trabajar con módulos del mercado [!DNL Adobe Commerce], puede requerir agregar y guardar datos adicionales. Su primer instinto podría ser agregar una columna a una tabla de la base de datos o ajustar una existente. Sin embargo, solo debe modificar una tabla principal [!DNL Adobe Commerce] (o una tabla de proveedores de terceros) en situaciones limitadas.

## Por qué Adobe recomienda evitar las modificaciones

El motivo principal para evitar la modificación de las tablas principales es que Adobe Commerce incluye una lógica subyacente que contiene consultas SQL sin procesar. Los cambios en la estructura de la tabla pueden producir efectos adversos inesperados que son difíciles de solucionar. El cambio también puede afectar a las operaciones de DDL (lenguaje de definición de datos), lo que provoca efectos inesperados e impredecibles en el rendimiento.

Otro motivo para evitar cambiar la estructura de la tabla de la base de datos es que los cambios pueden causar problemas si el equipo de desarrollo principal o los desarrolladores de terceros cambian la estructura de sus tablas de base de datos. Por ejemplo, hay algunas tablas de base de datos principales que tienen una columna denominada `additional_data`. Siempre ha sido un tipo de columna `text`. Sin embargo, por motivos de rendimiento, el equipo principal podría cambiar la columna a `longtext`. Este tipo de columna es un alias para JSON. Al convertir a este tipo de columna, se agregan mejoras de rendimiento y capacidad de búsqueda a esa columna, que no existe como tipo `text`. Puede obtener más información sobre este tema en [Tipo de datos JSON](https://mariadb.com/kb/en/json-data-type/){target="_blank"}.

## Saber cuándo guardar o quitar datos

Adobe recomienda determinar primero si es necesario guardar estos datos. Si mueve datos de un sistema heredado, cualquier dato que pueda eliminar le ahorrará tiempo y esfuerzo durante la migración. (Hay formas de archivar los datos si es necesario acceder a ellos más adelante). Para ser un buen administrador de la aplicación y el rendimiento, está bien retar una solicitud para guardar datos adicionales. Su objetivo es garantizar que guardar los datos sea un requisito para satisfacer una necesidad empresarial que no se puede rellenar de otra manera.

### Datos heredados

Si el proyecto contiene datos heredados, como pedidos antiguos o registros de clientes, considere un método de búsqueda alternativo. Por ejemplo, si la empresa requiere acceso a los datos solo para referencia ocasional, considere implementar una búsqueda externa de la base de datos antigua alojada fuera de la plataforma de comercio en lugar de migrar los datos antiguos a [!DNL Adobe Commerce].

Esta situación requeriría que la base de datos se migrara a un servidor, ofreciendo ya sea una interfaz web para leer los datos, o quizás capacitación en el uso de MySQL Workbench o herramientas similares. Excluir estos datos de la nueva base de datos acelera la migración, ya que permite al equipo de desarrollo centrarse en el nuevo sitio en lugar de solucionar los problemas de migración de datos.

Otra opción relacionada para mantener los datos externos al comercio pero que le permite utilizarlos en tiempo real sería aprovechar otras herramientas, como GraphQL mesh. Esta opción combina diferentes fuentes de datos y las devuelve como una sola respuesta.

Por ejemplo, puede `stitch` agrupar pedidos antiguos de una base de datos externa, tal vez el sitio antiguo de Magento 1 que se ha retirado del mercado. A continuación, utilizando GraphQL mesh, muéstrelos como parte del historial de pedidos de los clientes. Estos pedidos antiguos se pueden combinar con los pedidos del entorno actual [!DNL Adobe Commerce].

Para obtener más información sobre el uso de la malla de API con GraphQL, consulte [Qué es la malla de API](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) y [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}.

## Migración de datos heredados con atributos de extensión

Si determina que los datos heredados requieren migración o que los nuevos datos deben guardarse en [!DNL Adobe Commerce], Adobe recomienda usar [atributos de extensión](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}. El uso de atributos de extensión para guardar datos adicionales ofrece las siguientes ventajas:

- Puede controlar los datos que se mantienen y la estructura de la base de datos, que garantiza que los datos se guarden con el tipo de columna correcto y los índices adecuados.
- La mayoría de las entidades de [!DNL Adobe Commerce] admiten el uso de atributos de extensión.
- Los atributos de extensión son un mecanismo independiente del almacenamiento que proporciona la flexibilidad para guardar los datos en la ubicación óptima para su proyecto.

Dos ejemplos de ubicaciones de almacenamiento son las tablas de base de datos y [!DNL Redis]. Las cosas clave que hay que tener en cuenta al elegir una ubicación son si la ubicación presenta una complejidad adicional o afecta al rendimiento.

### Considerar otras alternativas

Como desarrollador, es vital considerar siempre el uso de herramientas fuera de su entorno de [!DNL Adobe Commerce], como GraphQL mesh y Adobe App Builder. Estas herramientas pueden ayudarle a conservar el acceso a los datos, pero no afectan a la aplicación principal de comercio ni a sus tablas de base de datos subyacentes. Con este enfoque, expone sus datos a través de una API. A continuación, agregue una fuente de datos a la configuración de App Builder. Con GraphQL Mesh, puedes combinar esas fuentes de datos y producir una única respuesta como se menciona en [datos heredados](#legacy-data).

Para obtener más información sobre GraphQL mesh, consulte [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}. Para obtener información acerca de Adobe App Builder, consulte [Presentación de App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=es){target="_blank"}.

## Modificación de una tabla principal o de una tabla de terceros

Si decide almacenar datos modificando una tabla de base de datos de módulo principal [!DNL Adobe Commerce] o de terceros, siga las siguientes directrices para minimizar el impacto en la estabilidad y el rendimiento.

- Agregue solo las columnas nuevas.
- Nunca modifique el valor _type_ de una columna existente. Por ejemplo, no cambie un `integer` por un `varchar` para satisfacer su caso de uso único.
- Evite añadir columnas a tablas de atributos EAV. Estas tablas ya están sobrecargadas de lógica y responsabilidad.
- Antes de ajustar una tabla, determine su tamaño. Cambiar tablas grandes afecta a la implementación, lo que puede causar minutos u horas de retraso cuando se aplican cambios.

## Prácticas recomendadas para modificar una tabla de base de datos externa

Adobe recomienda seguir estos pasos cuando agregue una columna a una tabla de la base de datos principal o a una tabla de terceros:

1. Cree un módulo con un nombre en el área de nombres que represente lo que está actualizando.

   Por ejemplo: `app/code/YourCompany/Customer`

1. Cree los archivos apropiados para habilitar el módulo (consulte [Crear un módulo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html?lang=es){target="_blank"}.

1. Cree un archivo denominado `db_schema.xml` en la carpeta `etc` y realice los cambios correspondientes.

   Si corresponde, genere un archivo de `db_schema_whitelist.json`. Vea [Esquema declarativo](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"} para obtener más información.

### Impactos potenciales

Añadir una columna a una base de datos externa puede afectar al proyecto de Adobe Commerce de las siguientes maneras:

- Las actualizaciones podrían ser más complicadas.
- Las implementaciones se ven afectadas si la tabla que se modifica es grande.
- Las migraciones a una nueva plataforma podrían ser más complicadas.

## Formas de evitar la modificación de tablas principales

Puede evitar modificar las tablas de la base de datos de Adobe Commerce mediante [atributos de extensión](#migrate-legacy-data-with-extension-attributes). Otra alternativa es usar una columna especial (`additional_data`) que se encuentra en algunas tablas principales para almacenar datos y guardarlos en formato JSON.

### Guardar datos en una columna de datos con codificación JSON

Algunas tablas principales tienen una columna `additional_data` que contiene datos con codificación JSON. Esta columna ofrece una forma nativa de asignar datos adicionales en un campo. El uso de este método evita agregar una tabla para elementos de datos pequeños y simples que almacenan información para la recuperación de datos sin un requisito de búsqueda. La columna `additional_data` suele estar disponible solamente en el nivel de elemento, no para toda la oferta o el pedido.

- Ventajas de usar el campo `additional_data`

   - No se necesitan campos adicionales, lo que mantiene un número mínimo de columnas. Esto resulta útil en el flujo de ventas, donde ya hay muchas tablas implicadas. Es mejor no añadir más complejidad a este proceso ya complicado. Este método satisface muchos casos de uso, pero no todos.

- Desventajas

   - Este método es ideal solo para almacenar datos de solo lectura. Este problema se produce porque el código tendría que ser no serializado para modificar y generar el objeto para agregar dependencias o relaciones de base de datos.

   - Es difícil utilizar las operaciones de la base de datos para buscar estos campos. La búsqueda con este método es lenta.

   - Se debe tener especial cuidado al almacenar los datos en la columna `additional_data` para evitar activar operaciones de serialización o anulación de serialización que podrían romper el código al crear un JSON no válido o provocar errores de lectura durante el tiempo de ejecución.

   - Estos campos deben declararse claramente en el código para que un desarrollador pueda encontrarlos fácilmente.

   - Otros problemas que pueden ocurrir pueden ser muy difíciles de diagnosticar. Por ejemplo, con algunas funciones PHP nativas si no utiliza los métodos envoltorios [!DNL Adobe Commerce] proporcionados por la aplicación principal, el resultado final de los datos transformados puede ser diferente del formato esperado. Utilice siempre las funciones de envoltorio para garantizar la coherencia y la previsibilidad de los datos que se guardan o recuperan.

Estos son ejemplos de tablas que tienen la columna y la estructura de la columna `additional_data`.

```mysql
MariaDB [main]> DESCRIBE quote_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)


MariaDB [main]> DESCRIBE sales_order_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)
```

En las versiones 2.4.3, 2.4.4 y 2.4.5 hay diez tablas que tienen la columna `additional_data`.

```mysql
MariaDB [magento]> SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('additional_data') AND TABLE_SCHEMA='main';
+------------------------+
| TABLE_NAME             |
+------------------------+
| sales_shipment_item    |
| sales_creditmemo_item  |
| sales_invoice_item     |
| catalog_eav_attribute  |
| sales_order_payment    |
| quote_address_item     |
| quote_payment          |
| quote_item             |
| magento_reward_history |
| sales_order_item       |
+------------------------+
10 rows in set (0.020 sec)
```
