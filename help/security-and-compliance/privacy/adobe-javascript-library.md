---
title: Biblioteca JavaScript de privacidad de Adobe
description: Aprenda a utilizar herramientas personalizadas para acceder y eliminar la información personal del cliente recopilada por Adobe Commerce y el Magento Open Source.
hide: true
hidefromtoc: true
source-git-commit: 495dfd515759e4df507479de57118586eac14fda
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# Biblioteca JavaScript de privacidad de Adobe

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

La variable [Biblioteca JavaScript de privacidad de Adobe](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) es un conjunto de herramientas que ayudan a crear un proceso para acceder a datos privados y eliminarlos.

Los servicios de seguimiento de datos de Adobe Commerce y Magento Open Source pueden almacenar información privada aplicable a regulaciones de privacidad como la [Reglamento general de protección de datos (RGPD)](gdpr.md) y [Ley de privacidad del consumidor de California (CCPA)](ccpa.md).

Esta biblioteca proporciona un conjunto unificado de funciones para crear solicitudes de datos de privacidad, enviarlas a las implementaciones de cada producto y recopilar las respuestas. Utilice esta biblioteca para recuperar y eliminar los datos almacenados en el explorador mediante estos servicios de seguimiento de datos.

## Instalación

Utilice uno de los siguientes métodos para descargar el archivo de biblioteca:

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

Una vez que tenga el archivo, deberá agregarlo a un módulo o tema personalizado instalado en la instancia de Adobe Commerce y Magento Open Source. Siga las instrucciones descritas en la sección [Usar JavaScript personalizado](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) para realizar esta tarea.

## Uso

La biblioteca de JS de Adobe Privacy proporciona varias funciones para administrar los datos de identidad almacenados en el explorador.

`retrieveIdentities()`
: Devuelve una matriz de identidades de un servicio junto con una matriz de identidades no encontradas en el servicio

`removeIdentities()`
: Quita las identidades del explorador y devuelve una matriz de objetos de identidad con un `isDeleteClientSide` propiedad booleana para indicar si se han eliminado los datos.

`retrieveThenRemoveIdentities()`
: Esta función es similar a `removeIdentities()` en que recupera una matriz de identidades y las elimina del explorador.

Para obtener más información y ejemplos sobre el uso de estas funciones, consulte la [documentación oficial de la biblioteca](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html).

### Inicialización

Cree una instancia de `AdobePrivacy` para usar la biblioteca de JS de Adobe Privacy en el código de implementación.

```js
var adobePrivacy = new AdobePrivacy({});
```

El constructor acepta un objeto de configuración con parámetros durante la creación de instancias.
Consulte la [documentación oficial de la biblioteca](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) para obtener una lista de estos parámetros de configuración.
