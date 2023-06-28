---
title: Conceptos de seguridad de Adobe Commerce de alojamiento propio
description: Obtenga información acerca de las ideas y conceptos de seguridad de alojamiento propio y las prácticas recomendadas que debe tener en cuenta. Aprenda conceptos como sistema de archivos de solo lectura, análisis de malware y muchos otros temas a tener en cuenta al alojar Adobe Commerce.
landing-page-description: Aprenda algunos conceptos y cosas de seguridad que debe tener en cuenta al alojar Adobe Commerce por su cuenta.
short-description: Aprenda estrategias y conceptos de seguridad para alojar Adobe Commerce usted mismo.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: c4912f02-0411-466f-8c77-d610de9eb35d
feature: Install, Security
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---

# Conceptos de seguridad

La seguridad siempre debe ser una consideración importante para cualquier cosa relacionada con un proyecto de comercio electrónico. Sin una fuerte postura de seguridad, la superficie que puede ser atacada es exponencialmente mayor. Los conceptos e ideas presentados proporcionan métodos que están probados para reducir las vulnerabilidades comunes típicamente explotadas.

Los siguientes conceptos no están en ningún orden en particular. Están pensados para proporcionar algunas ideas y conceptos a considerar. Muchas son gratuitas o requerirían una instalación y configuración mínimas y una monitorización posterior. Investigue estos temas fuera de este tutorial para asegurarse de que tiene una comprensión lo suficientemente profunda de los conceptos presentados aquí.

## Sistema de archivos de solo lectura

El concepto de sistema de archivos de solo lectura se tomó prestado de [Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. Esto elimina por completo un área principal utilizada por un mal actor. Muchos exploits han aprovechado la modificación de un archivo que se espera que esté en la aplicación Commerce para evitar ser detectado. En lugar de crear uno, el actor incorrecto cambia el contenido de un archivo existente para realizar una acción inesperada. Al hacer que el sistema de archivos sea de solo lectura, se reduce considerablemente este vector de ataque.

## Use los administradores de autenticación y contraseña de factor DOS

Nunca comparta contraseñas. Cada usuario administrador debe tener su propia cuenta con la ACL adecuada. Asegúrese de que la identificación de dos factores nunca se desactive ni elimine. Si proporciona acceso de administrador a un tercero, asegúrese de que la contraseña la genere un administrador de contraseñas y no la vuelva a utilizar nunca.

## Análisis de malware

Los análisis de malware generalmente se encuentran en un proveedor de alojamiento que intenta especializarse en Adobe Commerce. Esta biblioteca de malware y exploits conocidos es una lista cada vez más extensa a medida que se descubren, clasifican y diagnostican nuevas amenazas. Consultar si el proveedor de alojamiento tiene un servicio de este tipo y si se pueden ejecutar automáticamente o solo si se solicita. También hay servicios a los que puede suscribirse que pueden utilizar su propia biblioteca de vulnerabilidades conocidas para comprobar constantemente si su aplicación de comercio tiene vulnerabilidades. Algunos de ellos son solo externos, algunos se pueden añadir a la infraestructura para proporcionar un análisis interno profundo de todas las carpetas, archivos e incluso la base de datos. Hay algunos proveedores con años de experiencia en este campo, desde Sansec.io a Sucuri y por supuesto MageReport. Algunas son gratuitas y otras tienen un coste adicional. Saber que esto está disponible y tener una conversación reflexiva con su arquitecto de Adobe Commerce y con el equipo de DevOps le asegurará encontrar la solución correcta.

## Herramienta de análisis de todo el sitio para Commerce

El [Herramienta de análisis de todo el sitio](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} es una herramienta de autoservicio proactiva y un repositorio central que incluye información detallada del sistema y recomendaciones para garantizar la seguridad y la operabilidad de la instalación de Adobe Commerce. Proporciona monitorización del rendimiento, informes y consejos en tiempo real las 24 horas del día, los 7 días de la semana para identificar posibles problemas y una mejor visibilidad de las configuraciones de salud, seguridad y aplicaciones del sitio. Ayuda a reducir el tiempo de resolución y a mejorar la estabilidad y el rendimiento del sitio.

## Habilitar y comprobar la configuración del registro de acciones de administración

Esto se puede encontrar después de iniciar sesión en la administración de Adobe Commerce y navegar hasta Tiendas > Configuración > Avanzado > Administración > Administración > Registro de acciones de administración. Esto proporciona una lista de los eventos que se supervisan y registran. Es útil cuando se hace un análisis forense en un sitio explotado, si la sospecha es que obtuvieron acceso al administrador de comercio. Este registro e informe pueden ser útiles para ver qué eventos realizó el actor incorrecto. Si algún registro de acciones de administración está deshabilitado, esto es una señal de que alguien puede haberlo deshabilitado para ocultarlo, quite el registro al realizar ciertas acciones.

## Servidor Bastion para acceso ssh

Esto es más difícil de explicar que la mayoría de los temas del tutorial Conceptos de seguridad. La idea básica para esto es proporcionar un servidor que actúe como intermediario para el acceso ssh. De este modo, los servidores de producción nunca permiten conexiones ssh externas. Puede crear este servidor bastión y utilizar una máscara IP local para asegurarse de que solo los servidores designados pueden introducir SSH en ellos.

## Revisar los roles y permisos de ACL

A cada usuario administrador de Adobe Commerce se le asigna una función ACL. Esta función debe crearse para proporcionar solo la funcionalidad que debe realizar el trabajo. Las funciones ACL deben evaluarse a menudo para garantizar que no proporcionen más autoridad de la necesaria. Si es necesario, cree muchas funciones ACL con responsabilidades. Si se concede acceso a un tercero por alguna razón, deben desactivarse lo antes posible. Pregunte durante cuánto tiempo necesitan absolutamente acceder y establecer una fecha de caducidad automática al crear su usuario administrador.

## Auditoría frecuente de los usuarios administradores y del acceso de los usuarios SSH

Para detectar la creación de usuarios administradores no deseados o no autorizados, la lista de usuarios administradores debe auditarse con frecuencia. Una buena regla general es comprobar quién tiene SSH y acceso de administrador a la aplicación de Adobe Commerce mensualmente. Si se detectan nuevos usuarios, desactive su cuenta y siga las políticas y procedimientos de la empresa para ese incidente. Es más fácil restablecer el acceso de los usuarios que recuperarse de una explotación.

## Database cleansing

Limite el acceso a los datos de producción. Estos compañeros designados deben tener la capacidad de extraer bases de datos de producción y limpiarlas de datos reales. Si la eliminación de los datos es una opción, trunque las tablas adecuadas, como pedidos, presupuestos y clientes. Sin embargo, a veces se desea el conjunto completo de datos, pero los valores se pueden convertir en anónimos. Esto suele ocurrir en un entorno de ensayo. También resulta útil antes de las actualizaciones. Al tener el volumen real de datos, pero anonimizados, se garantiza que está probando y validando el tiempo para ejecutar una implementación para la actualización correctamente. Si tiene un conjunto limitado de datos, puede subestimar el proceso de actualización y el tiempo.

+++Ejemplo aleatorio de información del cliente Este es un ejemplo de cómo cambiar la dirección de correo electrónico del cliente con una cadena aleatoria y todos los campos de nombre y apellido en algunas tablas estándar en las que Adobe Commerce almacena datos. **Recuerde comprobar si hay datos confidenciales en todas las tablas, esta lista no incluye todas las tablas que pueden almacenar datos de clientes**

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


+++También puede truncar las tablas en lugar de intentar convertir en anónimas

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

+++Eliminar información por completo ejemplo Aquí tiene un ejemplo para eliminar todos los pedidos, presupuestos, notas de abono y más antes del lanzamiento o para un entorno de desarrollo inferior

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

[!BADGE Solo Adobe Commerce en la nube]{type=Informative}

El uso de variables de entorno ayuda al permitirle establecer ciertos valores que se pueden y deben cambiar para cada entorno. Por ejemplo, es posible que desee tener una URL de administración diferente para cada entorno. Al establecer este valor como Variable de entorno, puede configurarlo y también hacer referencia a este valor rápidamente desde la interfaz de usuario de Cloud cuando sea necesario.

Puede obtener más información sobre este tema en Experience League [Variables de entorno de Commerce en infraestructura en nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## Herramientas de análisis de vulnerabilidades de software

La canalización de CI/CD puede ser una herramienta potente y ayudar a automatizar algunas tareas. En particular, la oportunidad de que un desarrollador comprometa código que pueda ser explotable siempre es una posibilidad real. Las revisiones de código de igual a igual suelen capturar estos elementos, pero como es un ser humano, se producen errores. El análisis automatizado de código ayuda a reducir la oportunidad de que se produzcan vulnerabilidades inesperadas en una función recién introducida. Estas herramientas pueden incluso utilizarse para bloquear la combinación de código en la base de código activa. Existen muchas maneras y herramientas para ofrecer análisis de calidad y seguridad de código automatizados. Puede haber herramientas desarrolladas a medida robustas, pero requieren actualizaciones y ajustes constantes. Una alternativa es aplicar herramientas actualizadas de forma proactiva, como synk.io y el inspector de código de Amazon.

## Cortafuegos de aplicación web

Un firewall de aplicaciones web o WAF como se utiliza a menudo cuando se habla con DevOps o un proveedor de alojamiento.

Los firewalls de aplicaciones web (WAF) evitan que el tráfico malintencionado entre en sitios y redes filtrando el tráfico con un conjunto de reglas de seguridad. Déclencheur El tráfico que infringe cualquiera de las reglas se bloquea antes de que pueda dañar los sitios o la red.

El WAF en la nube de Adobe Commerce proporciona una política de WAF con un conjunto de reglas diseñado para proteger las aplicaciones web de Adobe Commerce de una amplia gama de ataques. Si elige una opción de alojamiento propio, es responsabilidad suya encontrar un WAF y configurar las reglas. Algunos proveedores de alojamiento y proveedores WAF tienen un conjunto genérico de reglas que son un buen comienzo, pero esperan que algo de trabajo funcione para su proyecto.

La WAF examina el tráfico web y de administración para identificar cualquier actividad sospechosa. Evalúa el tráfico de GET y de POST (llamadas a la API HTTP) y aplica el conjunto de reglas para determinar qué tráfico bloquear. El WAF puede bloquear una amplia variedad de ataques, incluidos ataques de inyección SQL, ataques de scripts entre sitios, ataques de exfiltración de datos y violaciones del protocolo HTTP.

Como servicio basado en la nube, WAF no requiere hardware ni software para instalar o mantener. Fastly, un socio tecnológico existente, proporciona el software y la experiencia. Su WAF de alto rendimiento y siempre activo reside en cada nodo de caché en la red de entrega global de Fastly.

Para obtener más información sobre el WAF en Adobe Commerce en la nube proporcionado por Fastly, lea la [Preguntas frecuentes sobre Adobe Commerce Knowledge Base](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
