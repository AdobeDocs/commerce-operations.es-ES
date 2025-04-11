---
title: Versiones Beta
description: Obtenga más información sobre las versiones beta de Adobe Systems Commerce y aprenda a participar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: c523b57270370d87be0f2ab0513f7908bb0a7173
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---

# Versiones beta de Adobe Systems Commerce

Adobe Systems programas beta de Commerce son una forma para que los comerciantes obtengan acceso a funciones y código de prelanzamiento, proporcionen comentarios y guía el futuro de Adobe Systems Commerce. Hay dos tipos de programas beta:

- Beta público: hay una programa beta pública disponible para todos los clientes y socios de Adobe Systems Commerce
- Beta privado: un programa beta privado puede requerir una aprobación basada en los criterios de calificación para participar

>[!IMPORTANT]
>
>Beta lanzamientos pueden contener defectos y se proporcionan &quot;TAL CUAL&quot; sin garantía de ningún tipo. Adobe Systems no tendrá ninguna obligación de mantener, corregir, actualizar, cambiar, modificar o apoyar (a través de Adobe Systems Servicios de soporte o de otro modo) las versiones beta. Se recomienda a los clientes que tengan cuidado y que no confíen de ninguna manera en el correcto funcionamiento o rendimiento de las versiones beta y/o de cualquier documentación o material que lo acompañe. Las funciones y las API en versión beta están sujetas a cambios sin previo aviso. En consecuencia, cualquier uso de las versiones beta es bajo el propio riesgo del cliente.

## Beneficios de participar

Obtener acceso temprano a las funciones que Adobe Systems está desarrollando proporciona a los clientes y socios la capacidad de proporcionar comentarios, dar forma al desarrollo de productos y prepararse para adoptar nuevas capacidades antes de la disponibilidad general.

## Programas de Beta actuales

Consulte las siguientes secciones para obtener una lista de los programas beta activos.

### Adobe Commerce Optimizer

Adobe Systems Commerce Optimizer mejora su experiencia comercio electrónico con un escaparate de alto rendimiento, lo que aumenta la tráfico orgánica, el participación al cliente y la ingresos.

Con Adobe Systems Commerce Optimizer puedes:

- Haga crecer y escale su catálogo sin tener que cambiar la plataforma de toda su pila de comercio.
- Ingiera datos de catálogo de cualquier origen.
- Definir canales de negocio y políticas.
- Crear recomendaciones y búsqueda personalizados mediante IA y ML.
- Ver disponibilidad crucial de los datos del producto, incluidos el estado de sincronización y los datos de eventos del escaparate para una implementación y solución de problemas precisos.

[Obtén más](https://experienceleague.adobe.com/docs/commerce/optimizer/overview.html) información sobre Adobe Systems Commerce Optimizer. Si desea gustar participar en el programa de acceso anticipado de Adobe Systems Commerce Optimizer, envíe un solicitud de correo electrónico a [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com).

### Capacidades de búsqueda mejoradas para Search en vivo (Beta públicas)

Esta versión beta admite tres nuevas capacidades en la [`productSearch` consulta](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/):

- **El búsqueda** en capas (Search dentro de otro contexto búsqueda) Con esta capacidad, puede realizar hasta dos capas de búsqueda para sus consultas búsqueda. Por ejemplo:

   - **Capa 1 búsqueda** - Search para &quot;motor&quot; en &quot;product_attribute_1&quot;.
   - **Capa 2 búsqueda** - Search para &quot;número de pieza 123&quot; en &quot;product_attribute_2&quot;. Este ejemplo busca &quot;número de pieza 123&quot; dentro de los resultados de &quot;motor&quot;.

  La búsqueda estratificada está disponible tanto para la indexación `contains` búsqueda como `startsWith` para la indexación búsqueda, tal y como se describe a continuación:

- **startsWith búsqueda indexación** : Search utilizar `startsWith` la indexación. Esta nueva capacidad permite:

   - Buscar productos en los que el valor del atributo comience con una cadena determinada.
   - La configuración de un búsqueda &quot;termina con&quot; para que los compradores puedan búsqueda productos donde el valor del atributo termina con una cadena en particular. Para habilitar una búsqueda &quot;termina con&quot;, el atributo del producto debe ingerirse a la inversa y la llamada a la API también debe ser una cadena invertida.

- **contiene búsqueda indexación** -Search un atributo que utiliza contiene indexación. Esta nueva capacidad permite:

   - Buscar un consulta dentro de una cadena más grande. Por ejemplo, si un comprador busca el número de producto &quot;PE-123&quot; en la cadena &quot;HAPE-123&quot;.

      - Nota: Este tipo de búsqueda es diferente del búsqueda](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase) de frases existente[, que realiza un búsqueda de autocompletado. Por ejemplo, si el valor de atributo del producto es &quot;pantalones al aire libre&quot;, una frase búsqueda devuelve una respuesta para &quot;out pan&quot;, pero no devuelve una respuesta para &quot;oor ants&quot;. A contiene búsqueda, sin embargo, devuelve una respuesta para &quot;oor ants&quot;.

Estas nuevas condiciones mejoran el mecanismo de filtrado de consulta de búsqueda para restringir búsqueda resultados. Estas nuevas condiciones no afectan a la consulta de búsqueda principal. Para participar en la versión beta, envíe un solicitud de correo electrónico a [commerce-store-services](mailto:commerce-storefront-services@adobe.com).

Para instalar la versión beta de Live Search, consulte el [guía de Live Search](https://experienceleague.adobe.com/en/docs/commerce/live-search/install#install-the-live-search-beta).

### Integración del sistema de gestión de pedidos de IBM Sterling (Beta privado)

Este acelerador de integración para IBM Sterling Order Management permite a los clientes de Adobe Systems Commerce comenzar con capacidades avanzadas de gestión de pedidos impulsadas por IBM Sterling OMS. Con esta integración, los comerciantes obtienen:

- Visibilidad en tiempo real de los niveles de inventario y fechas de envío precisas para sus clientes.
- Abastecimiento automatizado para pedidos basado en reglas configurables, para que pueda optimizar su red de cumplimiento y inventario.
- Una vista universal de pedidos a través de canales desde un solo panel para que sus equipos de soporte puedan ofrecer un servicio excepcional e identificar y manejar excepciones rápidamente.
- Un flujo de gestión de devoluciones con plantillas para simplificar la gestión de devoluciones.

Para participar en esta versión beta, envíe un solicitud de correo electrónico a [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Adobe Systems Fundación de Comercio (Beta Pública)

Cada versión beta de Adobe Systems Commerce Foundation incluye todos los cambios entregados al código principal de Adobe Systems Commerce en la fecha de lanzamiento programada, incluidas, entre otras, las siguientes áreas funcionales:

- Últimas correcciones de seguridad
- Mejoras en el rendimiento
- Mejoras de GraphQL
- Correcciones de errores de calidad general
- Contribuciones de la comunidad
- Cambios necesarios para admitir la compatibilidad con [los servicios de Adobe Systems Commerce](https://experienceleague.adobe.com/docs/commerce/user-guides/home.html)

#### Convención de nomenclatura y programación

Adobe Systems generalmente lanza parches beta dos veces al año.

Beta paquetes de lanzamiento tienen un `-betaX` sufijo. Por ejemplo, los paquetes de la versión beta de Adobe Systems Commerce 2.4.7 utilizan la siguiente convención de nomenclatura:

- `2.4.7-beta1`
- `2.4.7-beta2`

Consulte el [calendario](schedule.md) de lanzamiento para conocer la lista de las próximas fechas de lanzamiento de la versión beta pública.

#### Acceso a la versión de Beta

Adobe Systems versiones beta de Commerce se distribuyen de la misma manera que cualquier otra versión de parche de Adobe Systems Commerce: como metapaquetes de Composer en `https://repo.magento.com`. El código fuente está disponible en [GitHub](https://github.com/magento/magento2).

Consulte [la inicio](../installation/composer.md) de instalación rápida de Composer para obtener más información.

#### Problema sistema de informes

Adobe Systems no proporciona el servicio de asistencia estándar de Adobe Systems para las versiones beta.

Para enviar comentarios relacionados con las versiones beta, seguir nuestro [flujo regular de sistema de informes de](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) edición en [GitHub](https://github.com/magento/magento2).

Nuestros equipos internos monitor todos los problemas esencial reportados en relación con la última versión beta y priorizarán que se resuelvan antes de la fecha de lanzamiento de GA.
