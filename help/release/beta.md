---
title: Versiones de Beta
description: Obtenga información sobre las versiones beta de Adobe Commerce y cómo participar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 4643c8392b6d92a2ccbbc2ec5b27d75c112d7521
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 0%

---

# Versiones beta de Adobe Commerce

Los programas beta de Adobe Commerce son una forma para que los comerciantes accedan a las funciones y el código de la versión preliminar, proporcionen comentarios y guíen el futuro de Adobe Commerce. Existen dos tipos de programas beta:

- Beta público: Hay un programa beta público disponible para todos los clientes y socios de Adobe Commerce
- Private Beta: Un programa beta privado puede requerir una aprobación basada en los criterios de calificación para participar

>[!IMPORTANT]
>
>Las versiones de Beta pueden contener defectos y se proporcionan &quot;TAL CUAL&quot; sin garantía de ningún tipo. Adobe no tiene obligación de mantener, corregir, actualizar, cambiar, modificar o admitir de otro modo (a través de los Servicios de soporte de Adobe o de otro modo) las versiones beta. Se recomienda a los clientes que tengan cuidado y no dependan en modo alguno del correcto funcionamiento o rendimiento de las versiones beta y/o de la documentación o los materiales adjuntos. Las funciones y las API de la versión beta están sujetas a cambios sin previo aviso. Por lo tanto, cualquier uso de las versiones beta es totalmente bajo el propio riesgo del cliente.

## Ventajas de participar

El acceso anticipado a las funciones que Adobe está desarrollando permite a los clientes y socios proporcionar comentarios, dar forma al desarrollo de productos y prepararse para adoptar nuevas funciones antes de la disponibilidad general.

## Programas actuales de Beta

Consulte las secciones siguientes para obtener una lista de los programas beta activos.

### Funciones de búsqueda mejoradas para Live Search (Beta público)

Esta versión beta admite tres nuevas funciones en la consulta [`productSearch` ](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/):

- **Búsqueda por niveles** - Buscar en otro contexto de búsqueda - Con esta capacidad, puede realizar hasta dos niveles de búsqueda para sus consultas de búsqueda. Por ejemplo:

   - **Búsqueda de nivel 1** - Busque &quot;motor&quot; en &quot;product_attribute_1&quot;.
   - **Búsqueda de nivel 2** - Busque &quot;número de pieza 123&quot; en &quot;product_attribute_2&quot;. En este ejemplo se busca &quot;número de pieza 123&quot; dentro de los resultados para &quot;motor&quot;.

  La búsqueda por capas está disponible tanto para la indexación de búsqueda `startsWith` como para la indexación de búsqueda `contains`, tal como se describe a continuación:

- **comienza con la indexación de búsqueda** - La búsqueda usa la indexación `startsWith`. Esta nueva capacidad permite:

   - Búsqueda de productos en los que el valor del atributo empieza con una cadena determinada.
   - Configuración de una búsqueda &quot;termina con&quot; para que los compradores puedan buscar productos en los que el valor del atributo termine con una cadena en particular. Para habilitar una búsqueda &quot;termina con&quot;, el atributo del producto debe ingerirse a la inversa y la llamada de API también debe ser una cadena invertida.

- **contiene indización de búsqueda**: la búsqueda de un atributo mediante contiene indización. Esta nueva capacidad permite:

   - Búsqueda de una consulta dentro de una cadena más grande. Por ejemplo, si un comprador busca el número de producto PE-123 en la cadena HAPE-123.

      - Nota: este tipo de búsqueda es diferente de la búsqueda de frases [existente](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase), que realiza una búsqueda de autocompletar. Por ejemplo, si el valor de atributo del producto es &quot;pantalones de exterior&quot;, una búsqueda de frase devuelve una respuesta para &quot;sin bandeja&quot;, pero no devuelve una respuesta para &quot;u hormigas&quot;. Sin embargo, una búsqueda contiene sí devuelve una respuesta para &quot;o hormigas&quot;.

Estas nuevas condiciones mejoran el mecanismo de filtrado de consultas de búsqueda para restringir los resultados de búsqueda. Estas nuevas condiciones no afectan a la consulta de búsqueda principal. Para participar en la versión beta, envía una solicitud por correo electrónico a [commerce-storefront-services](mailto:commerce-storefront-services@adobe.com).

Para instalar la versión beta de Live Search, consulta la [guía de Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install#install-the-live-search-beta).

### Integración de Experience Manager Assets para Commerce (Private Beta)

La integración de Experience Manager Assets para Commerce permite una gestión y un envío eficientes de un gran volumen de imágenes de productos de Experience Manager Assets a Adobe Commerce con un esfuerzo operativo bajo o nulo.

Características principales:

- Integración Plug and Play: proporcione una integración entre Experience Manager Assets y Adobe Commerce con tecnología de Adobe para que los comerciantes puedan centrarse en lo que más importa, con costes operativos reducidos y una mayor eficacia.

- Personalizar imágenes de productos a escala: utilice Experience Manager Assets para generar millones de variaciones de productos para experiencias de Commerce personalizadas con herramientas de edición sencillas basadas en la interfaz de usuario, creación de contenido generativa mediante el Adobe Firefly y flujos de trabajo de recursos asignados para garantizar la coherencia de la marca. Una vez que esté satisfecho con los recursos, envíelos sin problemas a sus tiendas de Commerce mediante la integración de Experience Manager Assets.

- Incorporación sencilla: simplifique la incorporación del comerciante con un proceso de sincronización configurable que permita la sincronización completa entre el repositorio de Experience Manager Assets y el catálogo de Commerce.

- Estrategia de coincidencia flexible: la integración incluye algoritmos de coincidencia de recursos predeterminados basados en SKU de productos que sincronizan imágenes entre AEM Assets y Commerce, y es extensible mediante Adobe Developer App Builder. Trabaje con su socio de soluciones para crear una estrategia de coincidencia de recursos personalizada sobre la integración para dar cabida a cualquier estructura de repositorio de administración de recursos.

Para participar en la versión beta, envía una solicitud por correo electrónico a [Shaun McCran](mailto:mccran@adobe.com).

### Integración del sistema IBM Sterling Order Management (Private Beta)

Este acelerador de integración para IBM Sterling Order Management permite a los clientes de Adobe Commerce empezar a utilizar las funciones avanzadas de gestión de pedidos con tecnología IBM Sterling OMS. Con esta integración, los comerciantes obtienen:

- Visibilidad en tiempo real de los niveles de inventario y fechas de entrega precisas para sus clientes.
- Abastecimiento automatizado de pedidos basado en reglas configurables, para que pueda optimizar su red de satisfacción de pedidos y su inventario.
- Una vista universal de los pedidos en todos los canales desde un único panel para que sus equipos de asistencia puedan ofrecer un servicio excepcional e identificar y gestionar las excepciones rápidamente.
- Flujo de administración de devoluciones con plantillas para simplificar la administración de devoluciones.

Para participar en esta versión beta, envía una solicitud por correo electrónico a [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Conexión de datos y Audience Activation (Beta público)

Se ha ampliado el uso compartido de datos entre Adobe Commerce y Adobe Experience Platform para impulsar experiencias personalizadas más potentes. Esta capacidad permite a los comerciantes:

- Compartir perfiles de clientes de Commerce
- Crear atributos personalizados

Para participar en esta versión beta, envía una solicitud por correo electrónico a [DataConnection@adobe.com](mailto:DataConnection@adobe.com).

### Adobe Commerce Foundation (Beta público)

Cada versión beta de Adobe Commerce Foundation incluye todos los cambios entregados al código principal de Adobe Commerce en la fecha programada de lanzamiento, incluidas, entre otras, las siguientes áreas funcionales:

- Últimas correcciones de seguridad
- Mejoras de rendimiento
- Mejoras de GraphQL
- Correcciones de errores de calidad generales
- Contribuciones comunitarias
- Cambios necesarios para admitir la compatibilidad con [servicios de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

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

Adobe no proporciona el servicio de soporte de Adobe estándar para las versiones beta.

Para enviar comentarios relacionados con las versiones beta, sigue nuestro [flujo regular de informes de problemas](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) en [GitHub](https://github.com/magento/magento2).

Nuestros equipos internos monitorizarán todos los problemas críticos notificados en relación con la última versión beta y les darán prioridad para que se resuelvan antes de la fecha de lanzamiento de GA.
