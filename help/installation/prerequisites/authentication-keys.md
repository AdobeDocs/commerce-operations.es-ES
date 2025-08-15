---
title: Obtener las claves de autenticación
description: Siga estos pasos para recuperar las credenciales y poder acceder a los paquetes de Adobe Commerce Composer en repo.magento.com.
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: fc63ca58cd2ff7c5ec597751980a39bfbe68aa5f
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Obtener las claves de autenticación

El repositorio `repo.magento.com` es donde se almacenan los paquetes de Adobe Commerce y de terceros Composer, los cuales requieren autenticación. Use su cuenta de Commerce Marketplace para generar un par de *claves de autenticación* de 32 caracteres con el fin de obtener acceso al repositorio.

Para tener acceso a los paquetes de Adobe Commerce, debe utilizar las claves asociadas con un MAGEID al que se haya concedido acceso a esos paquetes. El MAGEID suele ser el contacto principal de la cuenta de Adobe Commerce y es posible que no siempre sea el propietario del proyecto de Adobe Commerce en la nube.

>[!TIP]
>
>Si encuentra [errores](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html), es posible que no tenga autorización para acceder al paquete o que el derecho de acceso haya caducado debido a una factura pendiente en su cuenta.
>
>* Si es la persona de contacto principal de la cuenta, asegúrese de que no haya ninguna factura pendiente en la cuenta.
>* Si las claves proporcionadas por el contacto principal no funcionan y no hay facturas pendientes en la cuenta, el contacto principal debe ponerse en contacto con el [Soporte técnico de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para obtener ayuda.

Para crear claves de autenticación:

1. Inicie sesión en [Commerce Marketplace](https://commercemarketplace.adobe.com/). Si no tiene una cuenta, haga clic en **Registrar**.

1. Haz clic en el nombre de tu cuenta en la parte superior derecha de la página y selecciona **Mi perfil**.

1. Haga clic en **Claves de acceso** en la ficha Marketplace.

   ![Obtenga sus claves de acceso seguras en Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Haga clic en **Crear una nueva clave de acceso**. Escriba un nombre específico para las claves (por ejemplo, el nombre del desarrollador que las recibe) y haga clic en **Aceptar**.

1. Las nuevas claves públicas y privadas ahora están asociadas a su cuenta, en la que puede hacer clic para copiarlas. Guarde esta información o mantenga la página abierta cuando trabaje con el proyecto. Use la **clave pública** como nombre de usuario y la **clave privada** como contraseña.

## Administrar las claves de autenticación

También puede deshabilitar o eliminar las claves de autenticación. Por ejemplo, puede deshabilitar o eliminar claves por motivos de seguridad una vez que alguien abandone su organización.

* Para deshabilitar las claves: haga clic en **Deshabilitar**. Puede hacerlo si desea suspender el uso de las claves.
* Para habilitar una clave deshabilitada anteriormente: haga clic en **Habilitar**.
* Para eliminar claves: Haz clic en **Eliminar**.

### Administrar token de acceso SSH

Para descargar versiones de Adobe Commerce mediante SSH, debe generar un token de acceso de descargas. Para generar un token:

1. Inicie sesión en su [cuenta de magento.com](https://account.magento.com/customer/account/login).
1. Haz clic en **Mi cuenta** en la parte superior de la página.
1. Haga clic en **Configuración de la cuenta** > **Descargas del token de acceso**.

   ![Acceda a sus claves](../../assets/installation/connect_keys1.png)

1. Haga clic en **Generar nuevo token** para reemplazar y deshabilitar un token existente.

Debe usar su MAGEID más su token para descargar una versión. Su MAGEID se muestra en la parte superior izquierda de la página de su cuenta.

Por ejemplo:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Utilice sus claves de autenticación para:

* [Obtención del metapaquete (integradores, empaquetadores)](../composer.md)
* [Clonar el repositorio de GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (solo desarrolladores colaboradores)
* [Actualización y administración de módulos](../../upgrade/modules/upgrade.md)
