---
source-git-commit: 10a6329502bc63ec06bac0652301770bd8e2935a
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---
# 2.4.7 mejoras de seguridad

Hasta la fecha no se han producido ataques confirmados relacionados con estos problemas. Sin embargo, es posible que se aprovechen ciertas vulnerabilidades para acceder a la información de los clientes o hacerse cargo de las sesiones de administrador. La mayoría de estos problemas requieren que un atacante obtenga acceso primero al administrador. Como resultado, le recordamos que tome todas las medidas necesarias para proteger a su administrador, incluidas, entre otras, las siguientes:

* INCLUSIÓN EN LA LISTA DE PERMITIDOS IP
* [Autenticación de doble factor](https://developer.adobe.com/commerce/testing/functional-testing-framework/two-factor-authentication/)
* Uso de una VPN
* Uso de una ubicación única en lugar de `/admin`
* Buena higiene de las contraseñas

Las mejoras de seguridad para esta versión mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

* **Cambios en el comportamiento de las claves de caché no generadas**:

   * Las claves de caché no generadas para bloques ahora incluyen prefijos que difieren de los prefijos para las claves generadas automáticamente. (Las claves de caché no generadas son claves que se establecen mediante sintaxis de directiva de plantilla o la variable `setCacheKey` o `setData` métodos.)
   * Las claves de caché no generadas para bloques ahora solo deben contener letras, dígitos, guiones (-) y caracteres de subrayado (_).  <!-- AC-9831 -->

* **Limitaciones en el número de códigos de cupones generados automáticamente**. Commerce ahora limita el número de códigos de cupones que se generan automáticamente. El máximo predeterminado es 250 000. Los comerciantes pueden utilizar el nuevo **[!UICONTROL Code Quantity Limit]** opción de configuración (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) para evitar que el sistema se vea abrumado con muchos cupones. <!-- AC-8753 -->

* **Optimización del proceso predeterminado de generación de URL de administración**. La generación de la URL de administración predeterminada está optimizada para aumentar la aleatoriedad, lo que hace que las URL generadas sean menos predecibles. <!-- AC-9028 -->

* **Se agregó compatibilidad con Integridad de los subrecursos (SRI)** cumplir con los requisitos de PCI 4.0 para la verificación de la integridad de las secuencias de comandos en las páginas de pago. La compatibilidad con la Integridad de los subrecursos (SRI) proporciona hashes de integridad para todos los recursos JavaScript que residen en el sistema de archivos local. La función SRI predeterminada solo se implementa en las páginas de pago de las áreas de administración y tienda. Sin embargo, los comerciantes pueden ampliar la configuración predeterminada a otras páginas. Consulte [Integridad de subrecursos](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) en el _Guía para desarrolladores de Commerce PHP_.<!--AC-1153-->

* **Cambios en la Política de seguridad de contenido (CSP)**: actualizaciones y mejoras de configuración de las Políticas de seguridad de contenido (CSP) de Adobe Commerce para cumplir con los requisitos de PCI 4.0. Para obtener más información, consulte [Políticas de seguridad de contenido](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) en el _Guía para desarrolladores de Commerce PHP_. <!--AC-11513-->

   * La configuración predeterminada CSP para páginas de pago para áreas de administración y tienda de Commerce es ahora `restrict` modo. Para las demás páginas, la configuración predeterminada es `report-only` modo.  En las versiones anteriores a 2.4.7, el CSP se configuraba en `report-only` modo para todas las páginas.

   * Se ha agregado un proveedor nonce para permitir la ejecución de scripts en línea en un CSP. El proveedor nonce facilita la generación de cadenas nonce únicas para cada solicitud. A continuación, las cadenas se adjuntan al encabezado CSP.

   * Se han añadido opciones para configurar URI personalizados para que informen de infracciones de CSP en la página Crear pedido de la página Administrador y Cierre de compra de la tienda. Puede agregar la configuración desde el Administrador o agregando el URI al `config.xml` archivo.

     >[!NOTE]
     >
     >Actualizar la configuración de CSP a `restrict` Este modo podría bloquear los scripts en línea existentes en las páginas de pago de la administración y de la tienda, lo que provoca el siguiente error en el explorador cuando se carga una página: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Corrija estos errores actualizando la configuración de la lista blanca para permitir los scripts necesarios. Consulte [Solución de problemas](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) en el _Guía para desarrolladores de Commerce PHP_.

* Una nueva configuración de caché de página completa puede ayudar a mitigar los riesgos asociados con el protocolo HTTP `{BASE-URL}/page_cache/block/esi` punto final. Este extremo admite fragmentos de contenido cargados dinámicamente y sin restricciones desde controladores de diseño y estructuras de bloque de Commerce. El nuevo **[!UICONTROL Handles params size]** La configuración de establece el valor del punto de conexión `handles` , que determina el número máximo permitido de identificadores por API. El valor predeterminado de esta propiedad es 100. Los comerciantes pueden cambiar este valor desde el Administrador (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles params size]**). Consulte [Configuración de la aplicación de Commerce para que utilice Barniz](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/configure-varnish-commerce.html). <!-- AC-9113 -->

* **Limitación de velocidad nativa para la información de pago transmitida a través de las API de REST y GraphQL**. Los comerciantes ahora pueden [configurar limitación de velocidad](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales#rate-limiting) para la información de pago transmitida mediante REST y GraphQL. Esta capa adicional de protección apoya la prevención de ataques de tarjeta y potencialmente disminuye el volumen de ataques de tarjeta que prueban muchos números de tarjeta de crédito a la vez. Se trata de un cambio en el comportamiento predeterminado de un extremo REST existente. Consulte [Limitación de velocidad](https://developer.adobe.com/commerce/webapi/get-started/rate-limiting/).

* El comportamiento predeterminado del [isEmailAvailable](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL query y el ([V1/customers/isEmailAvailable](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) El extremo REST ha cambiado. De forma predeterminada, las API ahora siempre devuelven `true`. Los comerciantes pueden activar el comportamiento original configurando la variable *[Habilitar cierre de compra de invitados](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/checkout)* en la opción Administrador para `yes`, pero hacerlo puede exponer la información del cliente a usuarios no autenticados.
