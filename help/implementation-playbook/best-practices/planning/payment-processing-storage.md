---
title: Prácticas recomendadas para procesamiento y almacenamiento de pagos
description: Aprenda a procesar y almacenar de forma segura los detalles de pago
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 124eaf6e7b465b320d3d7e6a3694130edb93f187
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---


# Prácticas recomendadas para procesamiento y almacenamiento de pagos

Uno de los principios fundamentales para mantener [Cumplimiento de PCI](https://nam04.safelinks.protection.outlook.com/GetUrlReputation) tiene una estrategia para procesar y almacenar correctamente los pagos con tarjeta de crédito.

El almacenamiento de datos de titulares de tarjetas en Adobe Commerce es **estrictamente prohibido** y hacerlo podría ser una violación de sus obligaciones como comerciante bajo el estándar de seguridad de datos del sector de tarjetas de pago (PCI-DSS). Encontrará más información sobre nuestro modelo de responsabilidad compartida y las directrices para las obligaciones de los comerciantes en nuestra [guía de responsabilidad compartida de Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) en el Centro Fiduciario de Adobe.

Recomendamos seguir las prácticas recomendadas a continuación para garantizar que está procesando correctamente la información de pago en su sitio de comercio electrónico. Encontrará más sugerencias sobre las prácticas recomendadas de seguridad en nuestro [guía de prácticas recomendadas de seguridad para Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-best-practices-guide.pdf) sobre el Centro Fiduciario de Adobe

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

* Adobe Commerce en infraestructura en la nube
* Adobe Commerce local

## Protección de los datos del titular de la tarjeta

Si es necesario almacenar los datos del titular de la tarjeta, estos deben almacenarse fuera de Adobe Commerce con salvaguardas de almacenamiento. Disponer de salvaguardias de almacenamiento para los detalles de pago, como los datos de titulares de tarjetas de crédito, ayuda a prevenir el fraude y otros problemas de seguridad potenciales. En línea con otros estándares PCI, tener protecciones implementadas es la primera línea de defensa. Algunos métodos preferidos para mejorar la protección de los datos almacenados son el cifrado, el truncamiento, la tokenización, el hash unidireccional y el enmascaramiento.

La protección de las claves criptográficas es vital para las estrategias de protección de datos. Es fundamental contar con custodios cualificados y fiables que supervisen estas claves.

Por último, un número de cuenta principal (PAN) debe ser ilegible durante el almacenamiento (por ejemplo, enmascarado como XXX). Esto incluye almacenamiento portátil y medios de backup, como unidades flash, USB y discos duros externos, e incluso registros de auditoría.

## Codificar la transmisión de datos del titular de la tarjeta

Proteger los datos durante la transmisión es clave para proteger la información de pago, como los datos de los titulares de tarjetas. Cuando esta información se transmite a través de redes abiertas, puede volverse más vulnerable a problemas de seguridad.

### Utilizar protocolos de transmisión seguros

Transmita los datos del titular de la tarjeta utilizando protocolos y prácticas de transmisión seguros, incluidos:

* Claves de confianza y certificados
* Protocolos de transmisión segura, como TLS, SSH o VPN
* Algoritmos asimétricos en cifrado
* Pruebas de tokens, máscaras y penetración con transmisión y visualización de PAN
* Restringir el acceso a los datos del titular de la tarjeta
* El acceso a la información confidencial debe restringirse por necesidad de conocer y sólo debe darse a los funcionarios autorizados que tengan una necesidad empresarial

El método recomendado para gestionar los datos del titular de la tarjeta es no almacenar el número de cuenta principal (PAN), sino tokenizar la tarjeta con un proveedor de procesamiento de pagos específico y almacenar el token, el tipo de tarjeta y la fecha de caducidad cifrada. Puede utilizar el token como credencial en el archivo para uso futuro, ya que es único solo para cada comerciante. Dado que el token es único, si hay un problema de seguridad, el token en invalidado ayuda a evitar actividades fraudulentas

## Información adicional

Si está buscando soluciones de pago recomendadas por Adobe, considere [Servicios de pago de Adobe](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
