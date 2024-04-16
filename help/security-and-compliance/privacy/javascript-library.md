---
title: Biblioteca JavaScript de privacidad
description: Aprenda a utilizar herramientas personalizadas para acceder a información personal de los clientes y eliminarla, recopilada por Adobe Commerce.
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Biblioteca JavaScript de privacidad

La biblioteca JavaScript de privacidad es un conjunto de herramientas que le ayudarán a crear un proceso para acceder a datos privados recopilados por Adobe Commerce y eliminarlos.

Los servicios de seguimiento de datos de Commerce pueden almacenar información privada aplicable a las regulaciones de privacidad, como la [Reglamento General de Protección de Datos (RGPD)](gdpr.md) y [California Consumer Privacy Act (CCPA)](ccpa.md).

Esta biblioteca proporciona un conjunto de funciones para crear solicitudes de datos de privacidad y recopilar sus respuestas. Utilice esta biblioteca para recuperar y eliminar los datos almacenados en el explorador por los servicios de seguimiento de datos de Adobe Commerce.

>[!NOTE]
>
>If [Modo de restricción de cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) está activada, Commerce no recopila datos de comportamiento hasta que el comprador da su consentimiento. If [!UICONTROL **Modo de restricción de cookies**] está desactivada, Commerce recopila datos de comportamiento de forma predeterminada.

## Instalación

La biblioteca JavaScript de privacidad está disponible en la siguiente ubicación de CDN: `commerce.adobe.net/magentoprivacy.js`

Una vez que tenga el archivo, deberá agregarlo a un módulo o tema personalizado instalado en la instancia de Adobe Commerce o de Magento Open Source. Siga las instrucciones descritas en la [Usar JavaScript personalizado](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) tema para realizar esta tarea.

### Inicialización

Importar y crear una instancia de un nuevo `MagentoPrivacy` objeto o utilice el `window` para acceder a las funciones de privacidad de JavaScript.

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

La biblioteca JS de privacidad proporciona varias funciones para administrar los datos de identidad almacenados en el explorador.

`retrieveIdentity()`
: Devuelve una promesa de JavaScript para un objeto de identidad desde un servicio del explorador.

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
: elimina los datos de identidad de un servicio en el explorador.
Esta función devuelve una promesa de JavaScript para un objeto de identidad con una `isDeleted` propiedad booleana para indicar si se han eliminado los datos.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
