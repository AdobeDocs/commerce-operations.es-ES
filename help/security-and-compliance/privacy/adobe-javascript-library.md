---
title: Adobe Privacidad Biblioteca de JavaScript
description: Aprenda a utilizar herramientas personalizadas para acceder a información personal de los clientes y eliminarla, recopilada por Adobe Commerce.
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Adobe Privacidad Biblioteca de JavaScript

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

La [Biblioteca JavaScript de privacidad de Adobe](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html) es un conjunto de herramientas que ayudan a crear un proceso para obtener acceso a datos privados y eliminarlos.

Los servicios de seguimiento de datos de Adobe Commerce pueden almacenar información privada que sea aplicable a ciertas normas de privacidad, tales como el [Reglamento General de Protección de Datos (RGPD)](gdpr.md) y la [Ley de Privacidad del Consumidor de California (CCPA)](ccpa.md).

Esta biblioteca proporciona un conjunto unificado de funciones para crear solicitudes de datos de privacidad, enviarlas a las implementaciones de cada producto y recopilar las respuestas. Utilice esta biblioteca para recuperar y eliminar los datos almacenados en el explorador por estos servicios de seguimiento de datos.

## Instalación

Utilice uno de los siguientes métodos para descargar el archivo de biblioteca:

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

Una vez que tenga el archivo, deberá agregarlo a un módulo o tema personalizado instalado en la instancia de Adobe Commerce. Siga las instrucciones descritas en el tema [Usar JavaScript personalizado](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) para realizar esta tarea.

## Uso

La biblioteca JS de privacidad de Adobe proporciona varias funciones para administrar los datos de identidad almacenados en el explorador.

`retrieveIdentities()`
: Devuelve una matriz de identidades de un servicio junto con una matriz de identidades que no se encuentran en el servicio

`removeIdentities()`
: quita las identidades del explorador y devuelve una matriz de objetos de identidad con una propiedad booleana `isDeleteClientSide` para indicar si los datos se han eliminado.

`retrieveThenRemoveIdentities()`
: Esta función es similar a `removeIdentities()` en el sentido de que recupera una matriz de identidades y las elimina del explorador.

Para obtener más información y ejemplos sobre el uso de estas funciones, consulte la [documentación oficial de la biblioteca](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html).

### Inicialización

Cree una instancia de un nuevo objeto `AdobePrivacy` para usar la biblioteca JS de privacidad de Adobe en el código de implementación.

```js
var adobePrivacy = new AdobePrivacy({});
```

El constructor acepta un objeto de configuración con parámetros durante la creación de instancias.
Consulte la [documentación oficial de la biblioteca](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html) para obtener una lista de estos parámetros de configuración.
