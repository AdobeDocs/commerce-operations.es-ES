---
title: Prácticas recomendadas para el procesamiento y almacenamiento de pagos
description: Aprenda a procesar y almacenar datos de pago de forma segura
role: Developer
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Prácticas recomendadas para el procesamiento y almacenamiento de pagos

Uno de los principios clave para mantener el [cumplimiento de PCI](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) es contar con una estrategia para procesar y almacenar correctamente los pagos con tarjeta de crédito.

Almacenar datos del titular de la tarjeta en Adobe Commerce está **estrictamente prohibido** y hacerlo podría ser una violación de sus obligaciones como comerciante según el Estándar de seguridad de datos de la industria de tarjetas de pago (PCI-DSS). Encontrará más información sobre el modelo de responsabilidad compartida y las directrices para las obligaciones de comerciantes en la [Guía del modelo de responsabilidad compartida de Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) en el Centro de confianza de Adobe.

Siga las prácticas recomendadas a continuación para asegurarse de que está procesando correctamente la información de pago en su sitio de comercio electrónico. Para obtener instrucciones adicionales sobre las prácticas recomendadas de seguridad, consulte [Proteger el sitio y la infraestructura](../launch/security-best-practices.md).

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

* Adobe Commerce en la infraestructura en la nube
* Adobe Commerce local

## Protección de datos del titular de tarjeta

Si es necesario almacenar los datos del titular de la tarjeta, estos deben almacenarse fuera de Adobe Commerce con medidas de seguridad. Disponer de garantías de almacenamiento para los datos de pago, como los datos del titular de la tarjeta de crédito, ayuda a prevenir el fraude y otros posibles problemas de seguridad. En línea con otras normas PCI, disponer de protecciones es la primera línea de defensa. Algunos métodos preferidos para mejorar la protección de los datos almacenados son el cifrado, el truncamiento, la tokenización, el hashing unidireccional y el enmascaramiento.

Las protecciones para claves criptográficas son vitales para las estrategias de protección de datos. Es fundamental contar con custodios cualificados y fiables que supervisen estas claves.

Por último, un número de cuenta principal (PAN) debe ser ilegible durante el almacenamiento, por ejemplo, enmascarado con `XXX`. Esto incluye almacenamiento portátil y medios de copia de seguridad, como unidades flash, USB y discos duros externos, e incluso registros de auditoría.

## Cifrar la transmisión de datos del titular de la tarjeta

La protección de los datos durante la transmisión es fundamental para proteger la información de pago, como los datos del titular de la tarjeta. Cuando esta información se transmite a través de redes abiertas, puede volverse más vulnerable a los problemas de seguridad.

### Uso de protocolos de transmisión seguros

Transmitir los datos del titular de la tarjeta mediante protocolos y prácticas de transmisión seguros, que incluyen:

* Claves y certificados de confianza
* Protocolos de transmisión segura, como TLS, SSH o VPN
* Algoritmos asimétricos en el cifrado
* Tokenización, enmascaramiento y pruebas de penetración con PAN de transmisión y visualización
* Restringir el acceso a los datos del titular de tarjeta
* El acceso a la información sensible debe restringirse según la necesidad de conocer y darse únicamente a aquellos miembros del personal autorizado que tengan una necesidad empresarial

El método recomendado para gestionar los datos del titular de la tarjeta es tokenizar los datos en lugar de almacenarlos. Tokenize la tarjeta con un proveedor de procesamiento de pagos específico y almacenar el token, el tipo de tarjeta y la fecha de caducidad cifrada. Puede utilizar el token como credencial registrada para uso futuro, ya que solo es único para cada comerciante. Dado que el token es único, si hay un problema de seguridad, el token se invalida, lo que ayuda a evitar actividades fraudulentas.

## Más información

Si estás buscando soluciones de pago recomendadas por Adobe, considera [Servicios de pago de Adobe](https://experienceleague.adobe.com/docs/commerce/payment-services/overview.html).
