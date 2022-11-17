---
title: Prácticas recomendadas para modificar tablas de bases de datos
description: Obtenga información sobre cómo y cuándo modificar las tablas de Adobe Commerce y de bases de datos de terceros.
role: Developer, Architect
feature: Best Practices
feature-set: Commerce
last-substantial-update: 2022-11-15T00:00:00Z
source-git-commit: 570fa4877f578f636736f0404169ed215fd06b24
workflow-type: tm+mt
source-wordcount: '1469'
ht-degree: 0%

---

# Prácticas recomendadas para modificar tablas de bases de datos

Este artículo proporciona prácticas recomendadas para modificar tablas de base de datos creadas por [!DNL Adobe Commerce] o módulos de terceros. Comprender cuándo y cómo modificar las tablas de forma eficaz ayuda a garantizar la viabilidad y estabilidad a largo plazo de su plataforma de comercio.

Migración desde [!DNL Magento 1] y otras plataformas de comercio electrónico, o trabajando con módulos de [!DNL Adobe Commerce] Marketplace puede requerir agregar y guardar datos adicionales. Su primer instinto podría ser agregar una columna a una tabla de base de datos o ajustar una existente. Sin embargo, solo debe modificar un núcleo [!DNL Adobe Commerce] (o tabla de proveedor de terceros) en situaciones limitadas.

## Por qué el Adobe recomienda evitar modificaciones

El motivo principal para evitar modificar las tablas principales es que Adobe Commerce incluye lógica subyacente que contiene consultas SQL sin procesar. Los cambios en la estructura de la tabla pueden provocar efectos secundarios inesperados que son difíciles de solucionar. El cambio también puede afectar a las operaciones de DDL (lenguaje de definición de datos), lo que provoca un impacto inesperado e impredecible en el rendimiento.

Otra razón para evitar cambiar la estructura de la tabla de la base de datos es que los cambios pueden causar problemas si el equipo de desarrollo principal o los desarrolladores de terceros cambian la estructura de sus tablas de base de datos. Por ejemplo, hay algunas tablas de base de datos principales que tienen una columna llamada `additional_data`. Esto siempre ha sido un `text` tipo de columna. Sin embargo, por motivos de rendimiento, el equipo principal puede cambiar la columna a `longtext`. Este tipo de columna es un alias para JSON. Al convertir a este tipo de columna, se añaden mejoras de rendimiento y capacidad de búsqueda a esa columna, que no existe como `text` tipo . Puede leer más sobre este tema en [Tipo de datos JSON](https://mariadb.com/kb/en/json-data-type/){target=&quot;_blank&quot;}.

## Saber cuándo guardar o eliminar datos

Adobe recomienda que determine primero si necesita guardar estos datos. Si está moviendo datos de un sistema heredado, cualquier dato que pueda eliminar ahorra tiempo y esfuerzo durante la migración. (Existen formas de archivar los datos si es necesario acceder a ellos más adelante). Para ser un buen administrador de la aplicación y el rendimiento, está bien cuestionar una solicitud para guardar datos adicionales. Su objetivo es garantizar que guardar los datos sea un requisito para satisfacer una necesidad empresarial que no se pueda cubrir de otra manera.

### Datos heredados

Si el proyecto contiene datos preexistentes, como pedidos antiguos o registros de clientes, considere un método de búsqueda alternativo. Por ejemplo, si la empresa requiere acceso a los datos solo para una referencia ocasional, considere la posibilidad de implementar una búsqueda externa de la antigua base de datos alojada fuera de la plataforma de comercio en lugar de migrar los datos antiguos a [!DNL Adobe Commerce].

Esta situación requeriría que la base de datos se migrara a un servidor, ofreciendo una interfaz web para leer los datos, o quizás entrenando en el uso de MySQL Workbench o herramientas similares. Excluir estos datos de la nueva base de datos acelera la migración, ya que permite que el equipo de desarrollo se centre en el nuevo sitio en lugar de solucionar problemas de migración de datos.

Otra opción relacionada para mantener los datos externos al comercio, pero permitirle usarlos en tiempo real, sería aprovechar otras herramientas, como la red GraphQL. Esta opción combina diferentes fuentes de datos y las devuelve como una sola respuesta.

Por ejemplo, puede `stitch` agrupa los pedidos antiguos de una base de datos externa, tal vez el sitio antiguo del Magento 1 que se ha retirado. A continuación, con la red GraphQL, muéstrelas como parte del historial de pedidos de los clientes. Estos pedidos antiguos pueden combinarse con los pedidos de su [!DNL Adobe Commerce] entorno.

Para obtener más información sobre el uso de la red de API con GraphQL, consulte [¿Qué es API Mesh?](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target=&quot;_blank&quot;}) y [Puerta de enlace de malla de GraphQL](https://developer.adobe.com/graphql-mesh-gateway/){target=&quot;_blank&quot;}.

## Migración de datos heredados con atributos de extensión

Si determina que los datos heredados requieren migración, o que los nuevos datos deben guardarse en [!DNL Adobe Commerce], el Adobe recomienda utilizar [atributos de extensión](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target=&quot;_blank&quot;}. El uso de atributos de extensión para guardar datos adicionales ofrece las siguientes ventajas:

- Puede controlar los datos que se mantienen y la estructura de la base de datos, lo que garantiza que los datos se guarden con el tipo de columna correcto y los índices adecuados.
- La mayoría de las entidades de [!DNL Adobe Commerce] y [!DNL Magento Open Source] admiten el uso de atributos de extensión.
- Los atributos de extensión son un mecanismo independiente del almacenamiento que proporciona la flexibilidad para guardar los datos en la ubicación óptima del proyecto.

Dos ejemplos de ubicaciones de almacenamiento son tablas de bases de datos y [!DNL Redis]. Los aspectos clave a tener en cuenta al elegir una ubicación son si la ubicación introduce una complejidad adicional o afecta al rendimiento.

### Considerar otras alternativas

Como desarrollador, es vital considerar siempre el uso de herramientas fuera de su [!DNL Adobe Commerce] como Mesh de GraphQL y Adobe App Builder. Estas herramientas pueden ayudarle a conservar el acceso a los datos, pero no tienen ningún impacto en la aplicación de comercio principal o en las tablas de base de datos subyacentes. Con este método, puede exponer los datos a través de una API. A continuación, agregue una fuente de datos a la configuración de App Builder . Con GraphQL Mesh, puede combinar esas fuentes de datos y producir una sola respuesta, como se menciona en [datos heredados](#legacy-data).

Para obtener más información sobre la red de GraphQL, consulte [Puerta de enlace de malla de GraphQL](https://developer.adobe.com/graphql-mesh-gateway/){target=&quot;_blank&quot;}. Para obtener información sobre el Generador de aplicaciones de Adobe, consulte [Presentación de App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target=&quot;_blank&quot;}.

## Modificación de una tabla principal o de una tabla de terceros

Si decide almacenar datos modificando un núcleo [!DNL Adobe Commerce] Para la tabla de base de datos de módulos de terceros, utilice las siguientes directrices para minimizar el impacto en la estabilidad y el rendimiento.

- Añada solo columnas nuevas.
- No modifique nunca el _type_ de una columna existente. Por ejemplo, no cambie un `integer` a `varchar` para satisfacer su caso de uso único.
- Evite añadir columnas a las tablas de atributos EAV. Estas tablas ya están sobrecargadas de lógica y responsabilidad.
- Antes de ajustar una tabla, determine su tamaño. Cambiar tablas grandes afecta a la implementación, lo que puede provocar minutos o horas de retraso cuando se aplican los cambios.

## Prácticas recomendadas para modificar una tabla de base de datos externa

Adobe recomienda seguir estos pasos cuando agregue una columna a una tabla de base de datos principal o a una tabla de terceros:

1. Cree un módulo con un nombre en el espacio de nombres que represente lo que está actualizando.

   Por ejemplo: `app/code/YourCompany/Customer`

1. Cree los archivos adecuados para habilitar el módulo (consulte [Creación de un módulo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target=&quot;_blank&quot;}.

1. Cree un archivo llamado `db_schema.xml` en el `etc` y realice los cambios correspondientes.

   Si corresponde, genere un `db_schema_whitelist.json` archivo. Consulte [Esquema declarativo](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target=&quot;_blank&quot;} para obtener más información.

### Posibles impactos

Añadir una columna a una base de datos externa puede afectar al proyecto de Adobe Commerce de las siguientes maneras:

- Las actualizaciones podrían ser más complicadas.
- Las implementaciones se ven afectadas si la tabla que se modifica es grande.
- Las migraciones a una nueva plataforma podrían ser más complicadas.

## Formas de evitar la modificación de tablas principales

Puede evitar modificar las tablas de la base de datos de Adobe Commerce mediante [atributos de extensión](#migrate-legacy-data-with-extension-attributes). Otra alternativa es utilizar una columna especial (`additional_data`) que se encuentra en algunas tablas principales para almacenar datos y guardarlos en formato codificado JSON.

### Guardar datos en una columna de datos con codificación JSON

Algunas tablas principales tienen un `additional_data` que contiene datos con codificación JSON. Esta columna ofrece una forma nativa de asignar datos adicionales en un campo. El uso de este método evita agregar una tabla para elementos de datos pequeños y simples que almacenan información para la recuperación de datos sin un requisito de búsqueda. La variable `additional_data` generalmente, la columna solo está disponible en el nivel de elemento, no para todo el presupuesto o pedido.

- Ventajas de utilizar la variable `additional_data` field

   - No se necesitan campos adicionales, lo que mantiene el número mínimo de columnas. Esto es útil en el flujo de ventas, donde ya hay muchas tablas involucradas. Es mejor no agregar más complejidad a este proceso ya complicado. Este método satisface muchos casos de uso, pero no todos.

- Desventajas

   - Este método es ideal solo para almacenar datos de solo lectura. Este problema se debe a que nuestro código tendría que anular la serialización para modificar y crear el objeto con el fin de añadir dependencias o relaciones de base de datos.

   - Es difícil utilizar operaciones de base de datos para buscar estos campos. La búsqueda con este método es lenta.

   - Se debe tener cuidado adicional cuando se almacenen datos en la variable `additional_data` para evitar activar operaciones de serialización o deserialización que podrían romper el código creando un JSON no válido o causando errores de lectura durante el tiempo de ejecución.

   - Estos campos deben declararse claramente en el código, para que un desarrollador pueda encontrarlos fácilmente.

   - Otros problemas que pueden ocurrir y que pueden ser muy difíciles de diagnosticar. Por ejemplo, con algunas funciones nativas de PHP si no se usa [!DNL Adobe Commerce] métodos wrapper proporcionados por la aplicación principal, el resultado final de los datos transformados puede ser diferente del formato esperado. Utilice siempre las funciones de ajuste para garantizar la coherencia y la previsibilidad de los datos que se guardan o recuperan.

A continuación se muestran ejemplos de tablas que tienen la columna y estructura para la variable `additional_data` para abrir el Navegador.

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
