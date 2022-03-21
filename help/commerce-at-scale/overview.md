---
title: Ofrecer Experiencias A Escala
description: Aprenda a ofrecer experiencias a escala con Adobe Commerce y Adobe Experience Manager.
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
debug: true
source-git-commit: 442bb3f2c448de2ed70a3033d399025cc39e8744
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Ofrezca experiencias a escala con Adobe Commerce, Commerce Integration Framework y Adobe Experience Manager

Un patrón de integración recomendado entre AEM y Adobe Commerce que utilizan CIF como conector es que AEM es el propietario de la capa de presentación (el &quot;vidrio&quot;) y Adobe Commerce para impulsar el back-end de comercio como un back-end &quot;sin periféricos&quot;. Este enfoque de integración aprovecha las ventajas de cada aplicación: las capacidades de creación, personalización y omnicanal de las operaciones de AEM y comercio electrónico de Adobe Commerce.

En un entorno AEM/CIF/Adobe Commerce, los visitantes del sitio de comercio electrónico llegarán inicialmente a AEM. AEM comprobará si tiene la página solicitada disponible en su caché de Dispatcher. Si la página existe, esta página en caché se suministra al visitante y no se requiere ningún procesamiento adicional. Si el despachante no contiene la página solicitada o ha caducado, el despachante solicita al publicador AEM que cree la página, y el publicador llama a Adobe Commerce para que especifique los datos de comercio electrónico necesarios para crear la página. A continuación, la página creada se transfiere al despachante para que se muestre al visitante y luego se almacena en caché, lo que evita la necesidad de que la carga adicional se coloque en los servidores en solicitudes posteriores de otros visitantes a la misma página.

![Diagrama general de la arquitectura de Adobe Experience Manager y Adobe Commerce](../assets/commerce-at-scale/overview.png)

En el modelo AEM/CIF/Adobe Commerce se puede utilizar una combinación de renderización del lado del servidor y del lado del cliente: Renderización del lado del servidor para ofrecer contenido estático y renderización del lado del cliente para ofrecer contenido dinámico personal o que cambia con frecuencia llamando directamente a Adobe Commerce para componentes específicos desde el navegador del usuario.

En el ejemplo siguiente se puede ver un ejemplo de los diferentes componentes de una página de detalles del producto AEM un ejemplo de tienda de comercio electrónico:

![Diagrama general de la arquitectura de Adobe Experience Manager y Adobe Commerce](../assets/commerce-at-scale/product-details-page.svg)

## Renderización del lado del servidor

Es poco probable que las páginas de comercio electrónico, como las páginas de detalles de productos (PDP) y las páginas de listas de productos (PLP), cambien con frecuencia y se adapten a la caché completa después de procesarse en el servidor mediante AEM componentes principales del CIF. Las páginas deben representarse en el editor de AEM mediante plantillas genéricas creadas en AEM. Estos componentes obtienen datos de Adobe Commerce a través de las API de GraphQL. Estas páginas se crean de forma dinámica, se representan en el servidor, se almacenan en caché en el AEM Dispatcher y se entregan al explorador. Algunos ejemplos de esto se muestran en los cuadros morados del ejemplo anterior.

## Renderización del lado del cliente

Cuando se muestran atributos más dinámicos, como niveles de existencias, disponibilidad o precio, por ejemplo en las páginas de detalles del producto (PDP), se pueden utilizar componentes del lado del cliente. Aunque la página de plantilla se puede crear y almacenar en caché en el despachante utilizando el método de renderización del lado del servidor descrito anteriormente, dentro de la propia página estática puede haber componentes web dinámicos del lado del cliente. Estos componentes dinámicos pueden recuperar datos directamente en el explorador del cliente desde Adobe Commerce a través de las API de GraphQL para comprobar, por ejemplo, el precio actual o el nivel de existencias en tiempo real en el PDP. Esto garantiza que el contenido que suele ser crítico para mostrarse en tiempo real siempre se obtenga al cargar la página. Algunos ejemplos de esto se muestran en los cuadros rojos del ejemplo anterior.

Durante el proceso de cierre de compra también se puede utilizar una combinación de plantillas de AEM y renderización del lado del cliente: los componentes del carro de compras del lado del cliente representan el carro de compras, el formulario de cierre de compra y la integración con el proveedor de servicios de pago. Este método híbrido también se puede usar para la funcionalidad de administración de cuentas de Adobe Commerce, como crear cuenta, iniciar sesión en la cuenta y olvidar la contraseña.
