---
title: Versiones de Beta
description: Obtenga información sobre las versiones beta de Adobe Commerce y cómo participar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: c27867be74dfaa1bcd782a23db27db29fdccc4e3
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---

# Versiones beta de Adobe Commerce

Los programas beta de Adobe Commerce son una forma para que los comerciantes accedan a las funciones y el código de la versión preliminar, proporcionen comentarios y guíen el futuro de Adobe Commerce. Existen dos tipos de programas beta:

- Beta público: Hay un programa beta público disponible para todos los clientes y socios de Adobe Commerce
- Private Beta: Un programa beta privado puede requerir una aprobación basada en los criterios de calificación para participar

>[!IMPORTANT]
>
>Beta lanzamientos pueden contener defectos y se proporcionan &quot;TAL CUAL&quot; sin garantía de ningún tipo. Adobe no tendrá ninguna obligación de mantener, corregir, actualizar, cambiar, modificar o admitir de otro modo (a través de los servicios de soporte de Adobe o de otro modo) las versiones beta. Se recomienda a los clientes que tengan cuidado y que no confíen de ninguna manera en el correcto funcionamiento o rendimiento de las versiones beta y/o de cualquier documentación o material que lo acompañe. Las funciones y las API en versión beta están sujetas a cambios sin previo aviso. En consecuencia, cualquier uso de las versiones beta es bajo el propio riesgo del cliente.

## Beneficios de participar

Obtener acceso temprano a las funciones que Adobe Systems está desarrollando proporciona a los clientes y socios la capacidad de proporcionar comentarios, dar forma al desarrollo de productos y prepararse para adoptar nuevas capacidades antes de la disponibilidad general.

## Programas de Beta actuales

Consulte las secciones siguientes para obtener una lista de los programas beta activos.

### Adobe Commerce Optimizer

Adobe Commerce Optimizer mejora su experiencia de comercio electrónico con una tienda de alto rendimiento, lo que aumenta el tráfico orgánico, la participación de los clientes y los ingresos.

Con Adobe Commerce Optimizer, puede:

- Haga crecer y escale su catálogo sin tener que cambiar la plataforma de toda su pila de comercio.
- Ingiera datos de catálogo de cualquier origen.
- Definir canales y directivas empresariales.
- Cree búsquedas y recomendaciones personalizadas con IA y ML.
- Vea la disponibilidad de datos de productos cruciales, incluido el estado de sincronización y los datos de eventos de tienda para una implementación y solución de problemas precisas.

[Más información](https://experienceleague.adobe.com/docs/commerce/optimizer/overview.html) sobre Adobe Commerce Optimizer. Si desea participar en el programa de acceso anticipado de Adobe Commerce Optimizer, envíe una solicitud por correo electrónico a [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com).

### Funciones de búsqueda mejoradas para Live Search (Beta público)

Esta versión beta admite tres nuevas funciones en la consulta [`productSearch` ](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/):

- **Búsqueda por niveles** - Buscar en otro contexto de búsqueda - Con esta capacidad, puede realizar hasta dos niveles de búsqueda para sus consultas de búsqueda. Por ejemplo:

   - **Búsqueda de nivel 1** - Busque &quot;motor&quot; en &quot;product_attribute_1&quot;.
   - **Búsqueda de nivel 2** - Busque &quot;número de pieza 123&quot; en &quot;product_attribute_2&quot;. En este ejemplo se busca &quot;número de pieza 123&quot; dentro de los resultados para &quot;motor&quot;.

  La búsqueda estratificada está disponible tanto para la indexación `contains` búsqueda como `startsWith` para la indexación búsqueda, tal y como se describe a continuación:

- **startsWith búsqueda indexación** : Search utilizar `startsWith` la indexación. Esta nueva capacidad permite:

   - Buscar productos en los que el valor del atributo comience con una cadena determinada.
   - La configuración de un búsqueda &quot;termina con&quot; para que los compradores puedan búsqueda productos donde el valor del atributo termina con una cadena en particular. Para habilitar una búsqueda &quot;termina con&quot;, el atributo del producto debe ingerirse a la inversa y la llamada a la API también debe ser una cadena invertida.

- **contiene indización de búsqueda**: la búsqueda de un atributo mediante contiene indización. Esta nueva capacidad permite:

   - Búsqueda de una consulta dentro de una cadena más grande. Por ejemplo, si un comprador busca el número de producto PE-123 en la cadena HAPE-123.

      - Nota: este tipo de búsqueda es diferente de la búsqueda de frases [existente](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase), que realiza una búsqueda de autocompletar. Por ejemplo, si el valor de atributo del producto es &quot;pantalones al aire libre&quot;, una frase búsqueda devuelve una respuesta para &quot;out pan&quot;, pero no devuelve una respuesta para &quot;oor ants&quot;. A contiene búsqueda, sin embargo, devuelve una respuesta para &quot;oor ants&quot;.

Estas nuevas condiciones mejoran el mecanismo de filtrado de consulta de búsqueda para restringir búsqueda resultados. Estas nuevas condiciones no afectan a la consulta de búsqueda principal. Para participar en la versión beta, envíe un solicitud de correo electrónico a [commerce-store-services](mailto:commerce-storefront-services@adobe.com).

Para instalar la versión beta de Live Search, consulta la [guía de Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install#install-the-live-search-beta).

### Integración del sistema IBM Sterling Order Management (Private Beta)

Este acelerador de integración para IBM Sterling Order Management permite a los clientes de Adobe Commerce empezar a utilizar las funciones avanzadas de gestión de pedidos con tecnología IBM Sterling OMS. Con esta integración, los comerciantes obtienen:

- Visibilidad en tiempo real de los niveles de inventario y fechas de entrega precisas para sus clientes.
- Abastecimiento automatizado de pedidos basado en reglas configurables, para que pueda optimizar su red de satisfacción de pedidos y su inventario.
- Una vista universal de pedidos a través de canales desde un solo panel para que sus equipos de soporte puedan ofrecer un servicio excepcional e identificar y manejar excepciones rápidamente.
- Un flujo de gestión de devoluciones con plantillas para simplificar la gestión de devoluciones.

Para participar en esta versión beta, envíe un solicitud de correo electrónico a [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Adobe Systems Fundación de Comercio (Beta Pública)

Cada versión beta de Adobe Systems Commerce Foundation incluye todos los cambios entregados al código principal de Adobe Systems Commerce en la fecha de lanzamiento programada, incluidas, entre otras, las siguientes áreas funcionales:

- Últimas correcciones de seguridad
- Mejoras de rendimiento
- Mejoras de GraphQL
- Correcciones de errores de calidad generales
- Contribuciones comunitarias
- Cambios necesarios para admitir la compatibilidad con [los servicios de Adobe Systems Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### Convenciones y programación de nombres

Adobe suele publicar parches beta dos veces al año.

Los paquetes de la versión de Beta tienen un sufijo `-betaX`. Por ejemplo, los paquetes de la versión beta de Adobe Commerce 2.4.7 utilizan la siguiente convención de nombres:

- `2.4.7-beta1`
- `2.4.7-beta2`

Consulte la [programación de versiones](schedule.md) para ver la lista de próximas fechas de lanzamiento de la versión beta pública.

#### Acceso a la versión de Beta

Las versiones beta de Adobe Commerce se distribuyen de la misma manera que cualquier otra versión de parche de Adobe Commerce: como metapaquetes de Compositor en `https://repo.magento.com`. El código fuente está disponible en [GitHub](https://github.com/magento/magento2).

Consulte [Inicio rápido de la instalación del compositor](../installation/composer.md) para obtener más información.

#### Informe de problemas

Adobe no proporciona el servicio de asistencia estándar de Adobe para las versiones beta.

Para enviar comentarios relacionados con las versiones beta, seguir nuestro [flujo regular de sistema de informes de](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) edición en [GitHub](https://github.com/magento/magento2).

Nuestros equipos internos monitor todos los problemas esencial reportados en relación con la última versión beta y priorizarán que se resuelvan antes de la fecha de lanzamiento de GA.
