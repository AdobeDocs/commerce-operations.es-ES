---
title: Biblioteca JavaScript de privacidad
description: Aprenda a utilizar herramientas personalizadas para acceder y eliminar la información personal del cliente recopilada por Adobe Commerce y el Magento Open Source.
source-git-commit: 1a608e8a5986026d5a187dc8cbd358fed2db5d9e
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---


<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Biblioteca JavaScript de privacidad

La biblioteca JavaScript de privacidad es un conjunto de herramientas que ayudan a crear un proceso para acceder y eliminar datos privados recopilados por Adobe Commerce y Magento Open Source.

Los servicios de seguimiento de datos de comercio pueden almacenar información privada aplicable a regulaciones de privacidad como la [Reglamento general de protección de datos (RGPD)](gdpr.md) y [Ley de privacidad del consumidor de California (CCPA)](ccpa.md).

Esta biblioteca proporciona un conjunto de funciones para crear solicitudes de datos de privacidad y recopilar sus respuestas. Utilice esta biblioteca para recuperar y eliminar los datos almacenados en el explorador mediante Adobe Commerce y los servicios de seguimiento de datos del Magento Open Source.

>[!NOTE]
>
>If [Modo de restricción de cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) está activada, Commerce no recopila datos de comportamiento hasta que el comprador consienta. If [!UICONTROL **Modo de restricción de cookies**] está desactivado, Commerce recopila datos de comportamiento de forma predeterminada.

## Instalación

La biblioteca JavaScript de privacidad está disponible en la siguiente ubicación de CDN: `commerce.adobe.net/magentoprivacy.js`

Una vez que tenga el archivo, deberá agregarlo a un módulo o tema personalizado instalado en la instancia de Adobe Commerce o Magento Open Source. Siga las instrucciones descritas en la sección [Usar JavaScript personalizado](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) para realizar esta tarea.

### Inicialización

Importe e instancie una nueva `MagentoPrivacy` o use el `window` para acceder a las funciones de JavaScript de privacidad.

Ejemplo con `import`:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

Ejemplo con `window`:

```js
const magePriv = new window.MagentoPrivacy()
```

## Uso

La Biblioteca de JS de privacidad proporciona varias funciones para administrar los datos de identidad almacenados en el explorador.

`retrieveIdentity()`
: Devuelve una promesa de JavaScript para un objeto de identidad de un servicio del explorador.

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
: Elimina los datos de identidad de un servicio en el explorador.
Esta función devuelve una promesa de JavaScript para un objeto de identidad con un `isDeleted` propiedad booleana para indicar si se han eliminado los datos.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
