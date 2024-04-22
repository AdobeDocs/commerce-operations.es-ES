---
title: Versiones beta
description: Obtenga información sobre las versiones beta de Adobe Commerce y cómo participar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 1dd4b44c6aa685795e16dccebfaf073dcc0062f2
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# Versiones beta de Adobe Commerce

Los programas beta de Adobe Commerce son una forma para que los comerciantes accedan a las funciones y el código de la versión preliminar, proporcionen comentarios y guíen el futuro de Adobe Commerce. Existen dos tipos de programas beta:

- Beta pública: hay un programa beta público disponible para todos los clientes y socios de Adobe Commerce
- Beta privada: un programa beta privado puede requerir una aprobación basada en criterios de calificación para poder participar

>[!IMPORTANT]
>
>Las versiones beta pueden contener defectos y se proporcionan &quot;TAL CUAL&quot; sin garantía de ningún tipo. Adobe no tiene obligación de mantener, corregir, actualizar, cambiar, modificar o admitir de otro modo (a través de los Servicios de soporte de Adobe o de otro modo) las versiones beta. Se recomienda a los clientes que tengan cuidado y no dependan en modo alguno del correcto funcionamiento o rendimiento de las versiones beta y/o de la documentación o los materiales adjuntos. Las funciones y las API de la versión beta están sujetas a cambios sin previo aviso. Por lo tanto, cualquier uso de las versiones beta es totalmente bajo el propio riesgo del cliente.

## Ventajas de participar

El acceso anticipado a las funciones que Adobe está desarrollando permite a los clientes y socios proporcionar comentarios, dar forma al desarrollo de productos y prepararse para adoptar nuevas funciones antes de la disponibilidad general.

## Programas beta actuales

Consulte las secciones siguientes para obtener una lista de los programas beta activos.

### Integración del sistema IBM Sterling Order Management (versión beta privada)

Este acelerador de integraciones para IBM Sterling Order Management permite a los clientes de Adobe Commerce empezar a utilizar las funciones avanzadas de gestión de pedidos con tecnología IBM Sterling OMS. Con esta integración, los comerciantes obtienen:
- Visibilidad en tiempo real de los niveles de inventario y fechas de entrega precisas para sus clientes.
- Abastecimiento automatizado de pedidos basado en reglas configurables, para que pueda optimizar su red de satisfacción de pedidos y su inventario.
- Una vista universal de los pedidos en todos los canales desde un único panel para que sus equipos de asistencia puedan ofrecer un servicio excepcional e identificar y gestionar las excepciones rápidamente.
- Flujo de administración de devoluciones con plantillas para simplificar la administración de devoluciones.

Para participar en esta versión beta, envíe una solicitud por correo electrónico a [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Conexión de datos y Audience Activation (beta pública)

Se ha ampliado el uso compartido de datos entre Adobe Commerce y Adobe Experience Platform para impulsar experiencias personalizadas más potentes. Esta capacidad permite a los comerciantes:
- Compartir perfiles de clientes de Commerce
- Crear atributos personalizados
- Obtenga información de Commerce en Real-Time CDP y Adobe Journey Optimizer
- Compatibilidad con varios conjuntos y flujos de datos

Para participar en esta versión beta, envíe una solicitud por correo electrónico a [DataConnection@adobe.com](mailto:DataConnection@adobe.com).

### Backoffice Integration Starter Kit (versión beta privada)

La oficina trasera [integration starter kit](https://developer-stage.adobe.com/commerce/extensibility/app-development/starter-kit/) proporciona a los desarrolladores un acelerador para crear integraciones impulsadas por eventos con sistemas como ERP, CRM y OMS. Con el Starter Kit, puede reducir los costes de desarrollo hasta en un 50%. El Starter Kit también sigue las prácticas recomendadas de Adobe Commerce, que reducen significativamente el coste de mantenimiento. Los aspectos destacados del Starter Kit incluyen:
- Sincronización de datos para objetos de uso común como productos, pedidos, clientes, existencias y envíos
- Modelos arquitectónicos siguiendo las prácticas recomendadas
- Incorporación de scripts para acelerar el desarrollo

Para participar en esta versión beta, complete el [formulario de inscripción](https://forms.office.com/r/YbYArqE3DT).

### Adobe Commerce Foundation (versión beta pública)

Cada versión beta de Adobe Commerce Foundation incluye todos los cambios entregados al código principal de Adobe Commerce en la fecha programada de lanzamiento, incluidas, entre otras, las siguientes áreas funcionales:

- Últimas correcciones de seguridad
- Mejoras de rendimiento
- Mejoras de GraphQL
- Correcciones de errores de calidad generales
- Contribuciones comunitarias
- Cambios necesarios para admitir la compatibilidad con [Servicios de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### Convenciones y programación de nombres

Adobe suele publicar parches beta dos veces al año.

Los paquetes de la versión beta tienen un `-betaX` sufijo. Por ejemplo, los paquetes de la versión beta de Adobe Commerce 2.4.7 utilizan la siguiente convención de nombres:

- `2.4.7-beta1`
- `2.4.7-beta2`

Consulte la [programación de versiones](schedule.md) para obtener la lista de fechas públicas de lanzamiento de la beta.


#### Acceso a la versión beta

Las versiones beta de Adobe Commerce se distribuyen de la misma manera que cualquier otra versión de parches de Adobe Commerce: como metapaquetes de Composer en `https://repo.magento.com`. El código fuente está disponible en [GitHub](https://github.com/magento/magento2).

Consulte [Inicio rápido de la instalación del Compositor](../installation/composer.md) para obtener más información.

#### Informe de problemas

Adobe no proporciona el servicio de soporte de Adobe estándar para las versiones beta.

Para enviar comentarios relacionados con las versiones beta, siga nuestros [flujo regular de informes de problemas](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) el [GitHub](https://github.com/magento/magento2).

Nuestros equipos internos monitorizarán todos los problemas críticos notificados en relación con la última versión beta y les darán prioridad para que se resuelvan antes de la fecha de lanzamiento de GA.
