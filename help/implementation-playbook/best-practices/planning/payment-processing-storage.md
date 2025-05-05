---
title: Prácticas recomendadas para el procesamiento y la almacenamiento de pagos
description: Aprenda a procesar y tienda de forma segura datos de pago
role: Developer
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Prácticas recomendadas para el procesamiento y almacenamiento de pagos

Uno de los principios clave para mantener [el cumplimiento](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html?lang=es) de PCI es tener una estrategia para procesar y tienda adecuadamente los pagos de tarjeta de crédito.

El almacenamiento de datos de titulares de tarjetas en Adobe Systems Commerce está **estrictamente prohibido** y hacerlo podría ser una violación de sus obligaciones como comerciante bajo el Estándar de Seguridad de Datos de la Industria de Tarjetas de Pago (PCI-DSS). Más información sobre el modelo de responsabilidad compartida y las pautas para comerciante obligaciones está disponible en la Guía[&#128279;](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) del modelo de responsabilidad compartida de Adobe Systems Comercio en el Centro de Confianza Adobe Systems.

Siga las prácticas recomendadas a continuación para asegurarse de que está procesando correctamente la información de pago en su sitio comercio electrónico. Para obtener instrucciones adicionales sobre prácticas recomendadas de seguridad, consulte [Proteger el sitio y la infraestructura](../launch/security-best-practices.md).

## Productos y versiones afectados

[Todas las versiones](../../../release/versions.md) compatibles de:

* Adobe Systems Commerce en infraestructura en la nube
* Adobe Systems Commerce local

## Protección de los datos de los titulares de tarjetas

Si es necesario almacenar los datos del titular de la tarjeta, entonces los datos del titular de la tarjeta deben almacenarse fuera de Adobe Systems Commerce con almacenamiento salvaguardas. Contar con almacenamiento medidas de seguridad para datos de pago, gustar los datos de los titulares de tarjetas de crédito, ayuda a prevenir el fraude y otros posibles problemas de seguridad. En línea con otros estándares PCI, tener protecciones implementadas es la primera línea de defensa. Algunos métodos preferidos para mejorar la protección de los datos almacenados incluyen cifrado, truncamiento, tokenización, hash unidireccional y enmascaramiento.

Las protecciones para las claves criptográficas son vitales para las estrategias de protección de datos. Es esencial tener custodios calificados y confiables que supervisen estas claves.

Por último, un número de cuenta primario (PAN) debe ser ilegible durante almacenamiento, por ejemplo, enmascarado con `XXX`. Esto incluye almacenamiento portátiles y copia de seguridad medios como unidades flash, USB y discos duros externos, y registros igualado de auditoría.

## Cifrar la transmisión de datos del titular de la tarjeta

Salvaguardar los datos durante la transmisión es clave para proteger la información de pago, gustar los datos del titular de la tarjeta. Cuando esta información se transmite a través de redes abiertas, puede volverse más vulnerable a los problemas de seguridad.

### Utilizar protocolos de transmisión seguros

Transmitir datos de titulares de tarjetas utilizando protocolos y prácticas de transmisión seguros, que incluyen:

* Claves y certificados de confianza
* Protocolos de transmisión seguros como TLS, SSH o VPN
* Algoritmos asimétricos en cifrado
* Pruebas de tokenización, enmascaramiento y penetración con transmisión y visualización de PAN
* Restringir el acceso a los datos del titular de la tarjeta
* El acceso a la información sensible debe restringirse según sea necesario y otorgarse solo al personal autorizado con un necesidad empresarial

El método recomendado para manejar los datos del titular de la tarjeta es tokenizar los datos en lugar de almacenarlos. Tokenice el tarjeta con un proveedor de procesamiento de pagos específico y tienda el token, el tipo de tarjeta y la fecha de vencimiento cifrada. Puede usar el token como credencial registrada para su uso futuro, ya que es único para cada comerciante únicamente. Dado que el token es único, si hay un problema de seguridad, se invalida el token, lo que ayuda a evitar actividad fraudulentas.

## Más información

Si está buscando soluciones de pago recomendadas por Adobe Systems, considere [Adobe Systems Servicios](https://experienceleague.adobe.com/docs/commerce/payment-services/overview.html?lang=es) de pago.
