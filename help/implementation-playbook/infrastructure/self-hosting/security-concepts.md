---
title: Conceptos de seguridad de Adobe Commerce de alojamiento propio
description: Obtenga información sobre ideas y conceptos de seguridad de alojamiento propio y prácticas recomendadas para tener en cuenta. Aprenda conceptos como sistema de archivos de solo lectura, análisis de malware y muchos otros temas para tener en cuenta al alojar adobe commerce.
landing-page-description: Aprenda algunos conceptos de seguridad y cosas que debe tener en cuenta al alojar Adobe Commerce por su cuenta.
short-description: Aprenda estrategias y conceptos de seguridad para hospedarse usted mismo en Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 0d5c2d3ae44008142797c7ac91530a9df98ae004
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Conceptos de seguridad

La seguridad siempre debe ser una consideración importante para todo lo relacionado con un proyecto de comercio electrónico. Sin una fuerte postura de seguridad, la superficie que puede ser atacada es exponencialmente mayor. Los conceptos e ideas presentados proporcionan métodos que se ha demostrado reducen las vulnerabilidades comunes que se suelen explotar.

Los siguientes conceptos no están en un orden determinado. Están pensados para proporcionar algunas ideas y conceptos a considerar. Muchos son gratuitos o requerirían una configuración y configuración mínimas y una supervisión posterior. Busque estos temas fuera de este tutorial para asegurarse de que tiene una comprensión lo suficientemente profunda de los conceptos presentados aquí.

## Sistema de archivos de sólo lectura

El concepto de sistema de archivos de solo lectura se tomó de [Adobe Commerce en una infraestructura ruidosa](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. Esto elimina completamente una área importante usada por un mal actor. Muchas vulnerabilidades han aprovechado la modificación de un archivo que se espera que esté en la aplicación Commerce para evitar la detección. En lugar de crear uno, el actor incorrecto cambia el contenido de un archivo existente para realizar una acción inesperada. Hacer que el sistema de archivos sea de solo lectura reduce significativamente este vector de ataque.

## Usar dos factores de autenticación y administradores de contraseña

Nunca comparta contraseñas. Cada usuario administrador debe tener su propia cuenta con la ACL adecuada. Asegúrese de que la identificación de dos factores nunca se desactive ni elimine. Si proporciona acceso de administrador a un tercero, asegúrese de que la contraseña la genera un administrador de contraseñas y nunca se reutiliza.

## Análisis de malware

Los análisis de malware generalmente se encuentran en un proveedor de alojamiento que intenta especializarse en Adobe Commerce. Esta biblioteca de software malicioso conocido y de explotación es una lista cada vez más extensa a medida que se descubren, prueban y diagnostican nuevas amenazas. Consultar si el proveedor de alojamiento dispone de dicho servicio y si se pueden ejecutar automáticamente o solo si así se solicita. También hay servicios a los que puede suscribirse que pueden usar su propia biblioteca de vulnerabilidades conocidas para comprobar constantemente su aplicación de comercio para detectar vulnerabilidades. Algunas de ellas son externas únicamente, otras se pueden agregar a la infraestructura para proporcionar un análisis profundo interno de todas las carpetas, archivos e incluso la base de datos. Hay algunos proveedores con años de experiencia en este campo, desde Sansec.io a Sucuri y por supuesto MageReport. Algunas son gratuitas y otras tienen un costo asociado. Saber que esto está disponible y tener una conversación cuidadosa con su arquitecto de Adobe Commerce y con el equipo de DevOps le asegurará de encontrar la solución correcta.

## Herramienta de análisis de todo el sitio para comercio

La variable [Herramienta de análisis de todo el sitio](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} es una herramienta de autoservicio proactiva y un repositorio central que incluye perspectivas y recomendaciones detalladas del sistema para garantizar la seguridad y la operabilidad de su instalación de Adobe Commerce. Proporciona monitoreo del rendimiento en tiempo real las 24 horas del día, los 7 días de la semana, informes y asesoramiento para identificar posibles problemas y una mejor visibilidad de las configuraciones de aplicaciones, seguridad y salud del sitio. Ayuda a reducir el tiempo de resolución y a mejorar la estabilidad y el rendimiento del sitio.

## Habilitar y verificar la configuración para el registro de acciones de administración

Esto se puede encontrar después de iniciar sesión en el administrador de Adobe Commerce y vaya a Tiendas > Configuración > Avanzadas > Administración > Registro de acciones de administración. Proporciona una lista de eventos que se supervisan y registran. Es útil cuando se realiza un análisis forense en un sitio explotado, si la sospecha es que han obtenido acceso al administrador de comercio. Este registro y este informe pueden ser útiles para ver qué eventos realizó el actor incorrecto. Si algún registro de acciones de administrador está deshabilitado, es un signo de que alguien puede haberlas deshabilitado para cubrir, elimine el registro al realizar ciertas acciones.

## Servidor de base para acceso ssh

Es más difícil explicar que la mayoría de los temas del tutorial Conceptos de seguridad . La idea básica de esto es proporcionar un servidor que actúe como intermediario para el acceso ssh. De este modo, los servidores de producción nunca permiten conexiones ssh externas. Puede crear este servidor de bastion y utilizar una máscara IP local para asegurarse de que solo los servidores designados estén autorizados a SSH en ellos.

## Revisar roles y permisos de ACL

A cada usuario administrador de Adobe Commerce se le asigna una función ACL. Esta función debe crearse para proporcionar solo la funcionalidad que debe realizar el trabajo. Las funciones ACL deben evaluarse con frecuencia para asegurarse de que no proporcionan más autoridad de la necesaria. Si es necesario, cree muchas funciones ACL con responsabilidades. Si se concede acceso a terceros por alguna razón, se deben desactivar lo antes posible. Pregúntale cuánto tiempo necesitan acceder y establecer una fecha de caducidad automática al crear su usuario administrador.

## Auditar usuarios administradores y acceso de usuarios SSH con frecuencia

Para detectar la creación de usuarios administradores no deseados o no autorizados, se debe auditar con frecuencia la lista de usuarios administradores. Una buena regla general es comprobar quién tiene SSH y acceso de administrador a la aplicación de Adobe Commerce mensualmente. Si se detecta algún usuario nuevo, deshabilite su cuenta y siga cualquier política y procedimiento de la empresa para ese incidente. Es más fácil restablecer el acceso de los usuarios que recuperarse de una explotación.

## Limpieza de bases de datos

Limitar el acceso a los datos de producción. Estos compañeros designados deben tener la capacidad de extraer bases de datos de producción y limpiarlas de datos reales. Si la eliminación de datos es una opción, trunque las tablas adecuadas, como pedidos, comillas y clientes. Sin embargo, a veces se desea el conjunto completo de datos, pero los valores se pueden anonimizar. Esto suele ocurrir en un entorno de ensayo. También es útil antes de las actualizaciones. Al tener el volumen real de datos, pero anonimizado garantiza que está probando y validando el tiempo para ejecutar una implementación para la actualización correctamente. Si tiene un conjunto limitado de datos, puede subestimar el proceso y el tiempo de actualización.

+++Ejemplo de información aleatoria del cliente Aquí se muestra un ejemplo de cómo cambiar la dirección de correo electrónico del cliente con una cadena aleatoria y todos los campos de nombre y apellido en algunas tablas estándar que Adobe Commerce almacena datos. **Recuerde comprobar que todas las tablas contienen datos confidenciales, esta lista no incluye todas las tablas que pueden almacenar datos de clientes**

```SQL
SET FOREIGN_KEY_CHECKS=0;
UPDATE customer_entity SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE email_contact SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE sales_invoice_grid SET customer_email = 'customer@example.com', customer_name  = 'Jack Smith';
UPDATE sales_order SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Smith', remote_ip = '127.0.0.1';
UPDATE sales_order_address SET region = 'Ohio', postcode = '12345-1234', lastname = 'Smith', street = '123 Main street', region_id = 44, city = 'Phoenix', telephone = NULL, firstname = 'Jane', company = NULL;
UPDATE sales_order_grid SET customer_email = 'customer@example.com', shipping_name = 'Jack', billing_name = 'Jack Smith', billing_address = '123 Main Street', shipping_address = '321 Pine Street', customer_name = 'Jane Smith';
UPDATE sales_shipment_grid SET customer_email = 'customer@example.com', customer_name = 'Jane Smith', billing_address = '123 Main street', billing_name = 'Jack Doe', shipping_name = 'Susie Smith';
UPDATE quote SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Jones', customer_dob = NULL, remote_ip = '127.0.0.1';
UPDATE quote_address SET email = 'customer@example.com', firstname = 'Jack', lastname = 'Smith', company = NULL, street = '123 Main st', city = 'AnyCity', region = 'Some State', region_id = 44, postcode = '12345-1234', telephone = NULL;
UPDATE magento_rma SET customer_custom_email = 'customer@example.com' WHERE customer_custom_email IS NOT NULL;
UPDATE customer_address_entity SET firstname = 'Jack', lastname = 'Smith', telephone = '909-555-1212', postcode = NULL,  region = NULL, street = '123 Main street', city = 'Anycity', company = NULL;
UPDATE customer_grid_flat SET name = 'Jane Doe', email = 'customer@example.com', dob = NULL, gender = NULL, taxvat = NULL, shipping_full = '', billing_full = '', billing_firstname = 'Jack', billing_lastname = 'Smith', billing_telephone = NULL, billing_postcode = NULL, billing_country_id = NULL, billing_region = NULL, billing_street = '123 Main street', billing_city = 'Anycity', billing_fax = NULL, billing_vat_id = NULL, billing_company = NULL;
UPDATE sales_creditmemo_grid SET billing_name = 'Sally', billing_address = '123 Main Street', customer_name = 'Jack Smith', customer_email = 'customer@example.com';
    
UPDATE magento_rma_grid SET customer_name = 'Jack Smith';
SET FOREIGN_KEY_CHECKS=1;
```

+++


+++También puede truncar tablas en lugar de intentar anonimizar

```SQL
SET FOREIGN_KEY_CHECKS=0;
TRUNCATE customer_log;  
TRUNCATE customer_visitor;  
TRUNCATE magento_logging_event;
TRUNCATE oauth_consumer;
TRUNCATE oauth_nonce;
TRUNCATE oauth_token;
TRUNCATE password_reset_request_event;
TRUNCATE acknowledgement;
TRUNCATE acknowledgement_report;
TRUNCATE avatax_log;
TRUNCATE avatax_queue;
TRUNCATE cron_schedule;
SET FOREIGN_KEY_CHECKS=1;
```

+++

+++Quitar la información completamente ejemplo A continuación se muestra un ejemplo para eliminar todos los pedidos, las comillas, los notas de crédito y mucho más antes del lanzamiento o para un entorno de desarrollo inferior

```SQL
DELETE FROM `gift_message`;
DELETE FROM `inventory_reservation`;
DELETE FROM `quote`;
DELETE FROM `quote_address`;
DELETE FROM `quote_address_item`;
DELETE FROM `quote_id_mask`;
DELETE FROM `quote_item`;
DELETE FROM `quote_item_option`;
DELETE FROM `quote_payment`;
DELETE FROM `quote_shipping_rate`;
DELETE FROM `reporting_orders`;
DELETE FROM `sales_bestsellers_aggregated_daily`;
DELETE FROM `sales_bestsellers_aggregated_monthly`;
DELETE FROM `sales_bestsellers_aggregated_yearly`;
DELETE FROM `sales_creditmemo`;
DELETE FROM `sales_creditmemo_comment`;
DELETE FROM `sales_creditmemo_grid`;
DELETE FROM `sales_creditmemo_item`;
DELETE FROM `sales_invoice`;
DELETE FROM `sales_invoiced_aggregated`;
DELETE FROM `sales_invoiced_aggregated_order`;
DELETE FROM `sales_invoice_comment`;
DELETE FROM `sales_invoice_grid`;
DELETE FROM `sales_invoice_item`;
DELETE FROM `sales_order`;
DELETE FROM `sales_order_address`;
DELETE FROM `sales_order_aggregated_created`;
DELETE FROM `sales_order_aggregated_updated`;
DELETE FROM `sales_order_grid`;
DELETE FROM `sales_order_item`;
DELETE FROM `sales_order_payment`;
DELETE FROM `sales_order_status_history`;
DELETE FROM `sales_order_tax`;
DELETE FROM `sales_order_tax_item`;
DELETE FROM `sales_payment_transaction`;
DELETE FROM `sales_refunded_aggregated`;
DELETE FROM `sales_refunded_aggregated_order`;
DELETE FROM `sales_shipment`;
DELETE FROM `sales_shipment_comment`;
DELETE FROM `sales_shipment_grid`;
DELETE FROM `sales_shipment_item`;
DELETE FROM `sales_shipment_track`;
DELETE FROM `sales_shipping_aggregated`;
DELETE FROM `sales_shipping_aggregated_order`;
DELETE FROM `tax_order_aggregated_created`;
DELETE FROM `tax_order_aggregated_updated`;
DELETE FROM `magento_rma`;
DELETE FROM `magento_rma_grid`;
DELETE FROM `magento_rma_item_entity`;
DELETE FROM `magento_rma_status_history`;
DELETE FROM `magento_sales_creditmemo_grid_archive`;
DELETE FROM `magento_sales_invoice_grid_archive`;
DELETE FROM `magento_sales_order_grid_archive`;
DELETE FROM `magento_sales_shipment_grid_archive`;
DELETE FROM `sequence_creditmemo_0`;
DELETE FROM `sequence_creditmemo_1`;
DELETE FROM `sequence_creditmemo_2`;
DELETE FROM `sequence_creditmemo_7`;
DELETE FROM `sequence_invoice_0`;
DELETE FROM `sequence_invoice_1`;
DELETE FROM `sequence_invoice_2`;
DELETE FROM `sequence_invoice_7`;
DELETE FROM `sequence_order_0`;
DELETE FROM `sequence_order_1`;
DELETE FROM `sequence_order_2`;
DELETE FROM `sequence_order_7`;
DELETE FROM `sequence_rma_item_0`;
DELETE FROM `sequence_rma_item_1`;
DELETE FROM `sequence_rma_item_2`;
DELETE FROM `sequence_rma_item_7`;
DELETE FROM `sequence_shipment_0`;
DELETE FROM `sequence_shipment_1`;
DELETE FROM `sequence_shipment_2`;
DELETE FROM `sequence_shipment_7`;

## USE THE FOLLOWING WITH CAUTION - CAN CAUSE ISSUES WITH TAX/PAYMENT PROCESSORS IF YOU REUSE ORDER NUMBERS, ETC.

ALTER TABLE sequence_creditmemo_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_7 AUTO_INCREMENT=1;
```

+++

## Usar variables de entorno

[!BADGE Adobe Commerce solo en la nube]{type=Informative}

El uso de variables de entorno ayuda al permitirle establecer ciertos valores que se pueden y se deben cambiar para cada entorno. Por ejemplo, es posible que desee tener una dirección URL de administración diferente para cada entorno. Al establecer este valor como una variable de entorno, puede configurarlo y también hacer referencia a este valor rápidamente desde la interfaz de usuario de Cloud cuando sea necesario.

Puede leer más sobre este tema en Experience League [Variables de entorno de Commerce on Cloud Infrastructure](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## Herramientas de análisis de vulnerabilidades de software

La canalización CI/CD puede ser una herramienta potente y ayudar a automatizar algunas tareas. En particular, la oportunidad para un desarrollador de cometer código que pueda ser explotable siempre es una posibilidad real. Las revisiones del código de los pares normalmente capturan esos artículos, pero como es un ser humano, ocurren errores. El análisis automatizado de código ayuda a reducir la oportunidad de detectar vulnerabilidades inesperadas en una función recién introducida. Estas herramientas pueden estar listas para bloquear la combinación de código en la base de código en directo. Existen muchas maneras y herramientas de ofrecer seguridad de código y análisis de calidad automatizados. Puede haber potentes herramientas personalizadas desarrolladas, pero requieren actualizaciones y ajustes constantes. Una alternativa es aplicar herramientas actualizadas proactivamente, como synk.io y el inspector de código de Amazon.

## Cortafuegos de aplicaciones web

Un servidor de seguridad de aplicación web o WAF, como se usa a menudo cuando se habla con DevOps o un proveedor de alojamiento.

Los cortafuegos de las aplicaciones web (WAF) impiden que el tráfico malintencionado entre en sitios y redes filtrando el tráfico contra un conjunto de reglas de seguridad. El tráfico que déclencheur cualquiera de las reglas está bloqueado antes de que pueda dañar los sitios o la red.

El WAF de nube de Adobe Commerce proporciona una política WAF con un conjunto de reglas diseñadas para proteger sus aplicaciones web de Adobe Commerce de una amplia gama de ataques. Si elige una opción de alojamiento propio, su responsabilidad es encontrar un WAF y configurar las reglas. Algunos proveedores de alojamiento y proveedores de WAF tienen un conjunto genérico de reglas que son un buen comienzo, sin embargo, esperan que algunos trabajos hagan que las cosas funcionen para su proyecto.

La WAF examina el tráfico web y administrativo para identificar cualquier actividad sospechosa. Evalúa el tráfico del GET y del POST (llamadas a la API HTTP) y aplica el conjunto de reglas para determinar qué tráfico bloquear. El WAF puede bloquear una amplia variedad de ataques, incluidos ataques de inyección de SQL, ataques de scripts en sitios múltiples, ataques de exfiltración de datos y violaciones del protocolo HTTP.

Como servicio basado en la nube, WAF no requiere hardware ni software para instalar o mantener. Por último, un socio tecnológico existente proporciona el software y la experiencia. Su WAF de alto rendimiento y siempre activo reside en cada nodo de caché a través de la red de entrega global de Finfinidad.

Para obtener más información sobre el WAF en Adobe Commerce en la nube proporcionada por Finfinito, lea la [Preguntas frecuentes sobre la Base de conocimiento de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
