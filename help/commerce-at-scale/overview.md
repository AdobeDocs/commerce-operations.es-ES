---
title: Ofrecer Experiencias A Escala
description: Aprenda a ofrecer experiencias a escala con Adobe Commerce y Adobe Experience Manager.
source-git-commit: 6ad72d5110ae3e3a7cf341282f2af9b700874f09
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Ofrezca experiencias a escala con Adobe Commerce, Commerce Integration Framework y Adobe Experience Manager

Un patrón de integración recomendado entre AEM y Adobe Commerce usando CIF como conector es para AEM que sea propietario de la capa de presentación (el &quot;vidrio&quot;) y Adobe Commerce para impulsar el back-end de comercio como un back-end &quot;sin periféricos&quot;. Este enfoque de integración aprovecha las ventajas de cada aplicación: las funciones de creación, personalización y omnicanal de las operaciones de AEM y comercio electrónico de Adobe Commerce.

En un entorno de comercio de AEM/CIF/Adobe, los visitantes del sitio de comercio electrónico llegarán inicialmente a AEM. AEM comprobará si tiene la página solicitada disponible en su caché de Dispatcher. Si la página existe, esta página en caché se suministra al visitante y no se requiere ningún procesamiento adicional. Si el despachante no contiene la página solicitada o ha caducado, el despachante solicita al publicador AEM que cree la página, y el publicador llama a Adobe Commerce para obtener datos de comercio electrónico para crear la página si es necesario. A continuación, la página creada se transfiere al despachante para que se muestre al visitante y luego se almacena en caché, lo que evita la necesidad de que la carga adicional se coloque en los servidores en solicitudes posteriores de otros visitantes a la misma página.

![Diagrama general de la arquitectura de Adobe Experience Manager y Adobe Commerce](../assets/commerce-at-scale/overview.png)

En el modelo de comercio de AEM/CIF/Adobe se puede utilizar una combinación de renderización del lado del servidor y del lado del cliente: Renderización del lado del servidor para ofrecer contenido estático y renderización del lado del cliente para ofrecer contenido dinámico personal o cambiante con frecuencia llamando directamente a Adobe Commerce para componentes específicos
desde el navegador del usuario.

En el ejemplo siguiente se puede ver un ejemplo de los diferentes componentes de una página de detalles del producto AEM un ejemplo de tienda de comercio electrónico:

![Diagrama general de la arquitectura de Adobe Experience Manager y Adobe Commerce](../assets/commerce-at-scale/product-details-page.svg)

## Renderización del lado del servidor

Es poco probable que las páginas de comercio electrónico, como las páginas de detalles de productos (PDP) y las páginas de listas de productos (PLP), cambien con frecuencia y se adapten a la caché completa después de procesarse en el servidor mediante AEM componentes principales del CIF. Las páginas deben representarse en el editor de AEM mediante plantillas genéricas creadas en AEM. Estos componentes obtienen datos de Adobe Commerce a través de las API de GraphQL. Estas páginas se crean de forma dinámica, se representan en el servidor, se almacenan en caché en el AEM Dispatcher y se entregan al explorador. Algunos ejemplos de esto se muestran en los cuadros morados del ejemplo anterior.

## Renderización del lado del cliente

Cuando se muestran atributos más dinámicos, como niveles de existencias, disponibilidad o precio, por ejemplo en las páginas de detalles del producto (PDP), se pueden utilizar componentes del lado del cliente. Aunque la página de plantilla se puede crear y almacenar en caché en el despachante utilizando el método de renderización del lado del servidor descrito anteriormente, dentro de la propia página estática puede haber componentes web dinámicos del lado del cliente. Estos componentes dinámicos pueden recuperar datos directamente en el explorador del cliente desde Adobe Commerce a través de las API de GraphQL para comprobar, por ejemplo, el precio actual o el nivel de existencias en tiempo real en el PDP. Esto garantiza que el contenido que suele ser crítico para mostrarse en tiempo real siempre se obtenga al cargar la página. Algunos ejemplos de esto se muestran en los cuadros rojos del ejemplo anterior.

Durante el proceso de cierre de compra también se puede utilizar una combinación de plantillas de AEM y renderización del lado del cliente: los componentes del carro de compras del lado del cliente representan el carro de compras, el formulario de cierre de compra y la integración con el proveedor de servicios de pago. Este método híbrido también se puede utilizar para la funcionalidad de administración de cuentas de Adobe Commerce, como crear cuenta, iniciar sesión en la cuenta y contraseña olvidada.
