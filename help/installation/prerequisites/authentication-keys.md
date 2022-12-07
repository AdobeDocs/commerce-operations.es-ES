---
title: Obtener las claves de autenticación
description: Siga estos pasos para recuperar las credenciales y acceder a los paquetes de Adobe Commerce y del Compositor de Magento Open Source en repo.magento.com.
source-git-commit: d209d3f7fde55f7495488f2cbeeebf21024875ed
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---


# Obtener las claves de autenticación

La variable `repo.magento.com` repositorio es donde se almacenan los paquetes de Adobe Commerce y Magento Open Source y del Compositor de terceros, y requiere autenticación. Utilice su cuenta de Commerce Marketplace para generar un par de 32 caracteres *claves de autenticación* para acceder al repositorio.

Para tener acceso a los paquetes Adobe Commerce y Magento Open Source, debe utilizar claves asociadas con un MAGEID al que se le haya concedido acceso a esos paquetes. El MAGEID suele ser el contacto principal de la cuenta de Adobe Commerce y es posible que no siempre sea el propietario del proyecto de Adobe Commerce en el proyecto de infraestructura de nube.

>[!TIP]
>
>Si encuentra [errors](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html), es posible que no tenga autorización para acceder al paquete o que el derecho de acceso haya caducado debido a una factura pendiente en su cuenta.
>
>* Si es la persona de contacto principal de la cuenta, asegúrese de que no haya ninguna factura pendiente enumerada en la cuenta.
>* Si las claves proporcionadas por el Contacto Principal no funcionan y no hay facturas pendientes en la cuenta, póngase en contacto con [Asistencia de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para obtener ayuda con el MAGEID del contacto principal.


Para crear claves de autenticación:

1. Inicie sesión en la [Commerce Marketplace](https://marketplace.magento.com). Si no tiene una cuenta, haga clic en **Registro**.
1. Haga clic en el nombre de su cuenta en la parte superior derecha de la página y seleccione **Mi perfil**.

1. Haga clic en **Teclas de acceso** en la pestaña Marketplace .

   ![Obtenga sus claves de acceso seguras en el Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Haga clic en **Crear una nueva clave de acceso**. Escriba un nombre específico para las claves (por ejemplo, el nombre del desarrollador que recibe las claves) y haga clic en **OK**.

1. Las nuevas claves públicas y privadas están ahora asociadas a su cuenta en la que puede hacer clic para copiar. Guarde esta información o mantenga la página abierta cuando trabaje con su proyecto. Utilice la variable **Clave pública** como nombre de usuario y **Clave privada** como su contraseña.

## Administrar las claves de autenticación

También puede deshabilitar o eliminar claves de autenticación. Por ejemplo, puede deshabilitar o eliminar claves por motivos de seguridad después de que alguien abandone la organización.

* Para desactivar claves: Haga clic en **Deshabilitar**. Puede hacerlo si desea suspender el uso de sus claves.
* Para habilitar una clave deshabilitada anteriormente: Haga clic en **Habilitar**.
* Para eliminar claves: Haga clic en **Eliminar**.

### Administrar token de acceso SSH

Para descargar versiones de Adobe Commerce mediante SSH, debe generar un token de acceso de descargas. Para generar un token:

1. Inicie sesión en su [cuenta de magento.com](https://account.magento.com/customer/account/login).
1. Haga clic en **Mi cuenta** en la parte superior de la página.
1. Haga clic en **Configuración de la cuenta** > **Descarga del token de acceso**.

   ![Acceda a sus claves](../../assets/installation/connect_keys1.png)

1. Haga clic en **Generar nuevo token** para reemplazar y deshabilitar un token existente.

Debe usar su MAGEID y su token para descargar una versión. El MAGEID se muestra en la parte superior izquierda de la página de la cuenta.

Por ejemplo:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Utilice sus claves de autenticación para:

* [Obtenga el metapackage (integradores, empaquetadores)](../composer.md)
* [Clonar el repositorio de GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (solo desarrolladores colaboradores)
* [Actualización y administración de módulos](../../upgrade/modules/upgrade.md)
