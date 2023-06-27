---
title: Ofrecer Experiencias A Escala
description: Aprenda a ofrecer experiencias a escala con Adobe Commerce y Adobe Experience Manager.
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Ofrezca experiencias a escala con Adobe Commerce, Commerce Integration Framework y Adobe Experience Manager

AEM Un patrón de integración recomendado entre los usuarios de Adobe Commerce AEM y los de que utilizan CIF como conector es poseer la capa de presentación (el &quot;vidrio&quot;) y Adobe Commerce para impulsar el back-end comercial como un back-end &quot;sin encabezado&quot;. AEM Este enfoque de integración aprovecha las ventajas de cada aplicación: las capacidades de creación, personalización y omnicanal de las operaciones de comercio electrónico y de comercio electrónico de Adobe Commerce en el mercado de la.

AEM En un entorno de/CIF/Adobe Commerce AEM, los visitantes del sitio de comercio electrónico llegarán inicialmente a la página de. AEM comprobará si tiene la página solicitada disponible en la caché de Dispatcher. Si existe la página, esta página en caché se proporcionará al visitante y no se requiere ningún procesamiento adicional. AEM Si el despachante no contiene la página solicitada o esta ha caducado, solicitará al editor que cree la página, y el editor llamará a Adobe Commerce para obtener datos de comercio electrónico y crear la página si es necesario. A continuación, la página creada se pasa al despachante para que se proporcione al visitante y, luego, se almacena en caché para evitar que sea necesario colocar una carga adicional en los servidores en solicitudes posteriores a la misma página de otros visitantes.

![Diagrama general de la arquitectura de Adobe de Experience Manager y Adobe Commerce](../assets/commerce-at-scale/overview.png)

AEM Se puede utilizar una combinación de procesamiento del lado del servidor y procesamiento del lado del cliente en el modelo de cliente/CIF/Adobe Commerce: Procesamiento del lado del servidor para ofrecer contenido estático y procesamiento del lado del cliente para ofrecer contenido dinámico personal o que cambia con frecuencia llamando directamente a Adobe Commerce para componentes específicos desde el explorador del usuario.

AEM En el siguiente ejemplo se muestra un ejemplo de los diferentes componentes de una página de detalles del producto en una tienda de comercio electrónico de ejemplo:

![Diagrama general de la arquitectura de Adobe de Experience Manager y Adobe Commerce](../assets/commerce-at-scale/product-details-page.svg)

## Renderización del lado del servidor

AEM Es poco probable que las páginas de comercio electrónico, como las páginas de detalles del producto (PDP) y las páginas de listas de productos (PLP), cambien con frecuencia y es adecuado que se almacenen en caché completamente después de procesarse en el lado del servidor mediante componentes principales de CIF de la. AEM AEM Las páginas deben representarse en el editor de la utilizando plantillas genéricas creadas en el documento de trabajo de la plantilla de. Estos componentes obtienen datos de Adobe Commerce mediante las API de GraphQL. AEM Estas páginas se crean de forma dinámica, se representan en el servidor, se almacenan en caché en el Dispatcher de y se entregan al explorador. En los cuadros morados del ejemplo anterior se muestran ejemplos de esto.

## Procesamiento del lado del cliente

Cuando se muestran atributos más dinámicos, como niveles de stock/disponibilidad o precio, por ejemplo, en las páginas de detalles del producto (PDP), se pueden utilizar componentes del lado del cliente. Aunque la página de plantilla se puede crear y almacenar en caché en Dispatcher mediante el método de procesamiento del lado del servidor anterior, dentro de la propia página estática puede haber componentes web dinámicos del lado del cliente. Estos componentes dinámicos pueden recuperar datos directamente en el explorador del cliente desde Adobe Commerce a través de las API de GraphQL para comprobar, por ejemplo, el precio actual o el nivel de stock en tiempo real en la PDP. Esto garantiza que el contenido que suele ser crítico para mostrarse en tiempo real se recupere siempre al cargar la página. En los cuadros rojos del ejemplo anterior se muestran ejemplos de esto.

AEM También se puede utilizar una combinación de plantillas de pago y procesamiento del lado del cliente durante el proceso de cierre de compra: los componentes del carro de compra del lado del cliente procesan el carro de compra, el formulario de cierre de compra y la integración con el proveedor de servicios de pago. Este enfoque híbrido también se puede utilizar para la funcionalidad de administración de cuentas de Adobe Commerce, como crear cuenta, iniciar sesión en la cuenta y eliminar la contraseña olvidada.
