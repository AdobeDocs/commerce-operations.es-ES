---
title: Configure varios sitios web, tiendas y vistas de tiendas en el Administrador de
description: Configure sitios web, tiendas y vistas de tiendas adicionales en el administrador de Commerce.
exl-id: e6b4d14d-7504-48f9-a2e1-7e9a1bc76ab9
source-git-commit: 5860f5327003372909c425c13c6d03166288d903
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 0%

---

# Configure varias vistas en el administrador

Esta tarea requiere que cree una categoría raíz (y categorías adicionales, si lo desea) para cada tienda. Las tareas que se tratan en este tema proporcionan una forma de configurar varias tiendas. Para obtener más información, consulte los siguientes recursos en la Guía del usuario de Commerce:

- [Categorías](https://docs.magento.com/user-guide/catalog/categories.html)
- [Adición de sitios web](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [URL de tienda](https://docs.magento.com/user-guide/stores/store-urls.html)
- [Contenido](https://docs.magento.com/user-guide/cms/content-menu.html)

>[!INFO]
>
>Por ejemplo, solo utilizamos un sitio web francés con código de sitio web `french` en este tema. Para ver tutoriales paso a paso, consulte [Tutorial: Configurar varios sitios web con Apache](ms-apache.md) y [Tutorial: Configurar varios sitios web con nginx](ms-nginx.md)

## Paso 1: Crear categorías raíz

La creación de una categoría raíz es opcional, pero se muestra cómo hacerlo en este tutorial en el caso de que desee que cada sitio web tenga una categoría raíz única. Si lo desea, puede crear categorías adicionales.

Para crear una categoría raíz:

1. Inicie sesión en Admin como usuario autorizado para crear categorías.
1. Clic **Catálogo** > **Categorías**.
1. Clic **Añadir categoría raíz**.
1. En el **Nombre de categoría** , introduzca un nombre único para identificar esta categoría.
1. Asegúrese de que Habilitar categoría está configurada en **Sí**.

   Para obtener más información sobre el resto de opciones de esta página, consulte [Categorías raíz](https://docs.magento.com/user-guide/catalog/category-root.html).

   La siguiente figura muestra un ejemplo.

   ![Creación y activación de una categoría raíz](../../assets/configuration/add-root-category.png)

1. Clic **Guardar**.
1. Repita estas tareas tantas veces como sea necesario para crear categorías raíz para las tiendas.

## Paso 2: Crear sitios web

Para crear un sitio web:

1. Inicie sesión en Admin como usuario autorizado para crear sitios web, tiendas y vistas de tiendas.
1. Clic **Tiendas** > **Configuración** > **Todas las tiendas**.
1. En el _Tiendas_ página, haga clic en **Crear sitio web**.

   - **Nombre**: introduzca un nombre para identificar el sitio Web.
   - **Código**: introduzca un código único; por ejemplo, si tiene un almacén francés, puede introducir `french`
   - **Orden de clasificación**: permite introducir un orden numérico opcional.

   La siguiente figura muestra un ejemplo.

   ![Agregar un sitio web](../../assets/configuration/multi-site-website.png)

1. Clic **Guardar sitio web**.
1. Repita estas tareas tantas veces como sea necesario para crear los sitios web.

## Paso 3: Crear tiendas

Para crear un almacén:

1. En el _Administrador_ , haga clic en **Tiendas** > **Configuración** > **Todas las tiendas**.
1. En el _Tiendas_ página, haga clic en **Crear tienda**.

   - **Sitio Web**: pulse en el nombre del sitio Web con el que se asociará este almacén.
   - **Nombre**: introduzca un nombre para identificar el almacén.
   - **Código**: introduzca un código único para identificar el almacén.
   - **Categoría raíz**: pulse en el nombre de la categoría raíz de este almacén.

   La siguiente figura muestra un ejemplo.

   ![Añadir una tienda](../../assets/configuration/multi-site-store.png)

1. Clic **Guardar tienda**.
1. Repita estas tareas tantas veces como sea necesario para crear sus tiendas.

## Paso 4: Crear vistas de tienda

Para crear una vista de tienda:

1. En el _Administrador_ , haga clic en **Tiendas** > **Configuración** > **Todas las tiendas**.
1. En la página Tiendas, haga clic en **Crear vista de tienda**.

   - **Almacenar**: pulse en el nombre del almacén con el que se asociará esta vista de almacén.
   - **Nombre**: introduzca un nombre para identificar esta vista de almacén.
   - **Código**: introduzca un nombre único para identificar esta vista de almacén.
   - **Estado**—Seleccionar **Habilitado**.

   La siguiente figura muestra un ejemplo.

   ![Añadir una tienda](../../assets/configuration/multi-site-storeview.png)

1. Clic **Guardar vista de tienda**.
1. Repita estas tareas tantas veces como sea necesario para crear las vistas de la tienda.

## Paso 5: cambiar la dirección URL base del sitio web

Para acceder a un sitio web mediante una dirección URL única como `http://french.magento.mg`, debe cambiar la dirección URL base para cada sitio en Admin.

Para cambiar la dirección URL base del sitio web:

1. En el _Administrador_ , haga clic en **Tiendas** > **Configuración** > **Configuración** > **General** > **Web**.
1. Desde el **Vista de tienda** en la parte superior de la página, haga clic en el nombre de uno de sus sitios web, como se muestra en la figura siguiente.

   ![Seleccionar un ámbito](../../assets/configuration/multi-site-scope.png)

1. En el panel derecho, expanda **Direcciones URL base**.
1. En el _Direcciones URL base_ sección, borrar **Usar valor del sistema**.
1. Introduzca el `http://french.magento.mg` URL en **URL básica** y **URL de vínculo base** campos.

1. Repita el paso anterior en la _URL básicas (seguras)_ sección.

   >[!INFO]
   >
   >Si está configurando una dirección URL base para la implementación de Adobe Commerce en una infraestructura en la nube, debe reemplazar el primer periodo con tres guiones. Por ejemplo, si la dirección URL base es `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, introduzca `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`. Si va a configurar una dirección URL base para pruebas locales, utilice un punto.

1. Clic **Guardar configuración**.

1. Repita estas tareas para otros sitios web.

## Paso 6: Añadir el código de tienda a la URL base

Commerce le da la opción de añadir el código de tienda a la dirección URL de base del sitio, lo que simplifica el proceso de configuración de varias tiendas. Con esta opción, no es necesario crear directorios en el sistema de archivos de Commerce para almacenar `index.php` y `.htaccess`.

Esto evita `index.php` y `.htaccess` de no sincronizarse con el código base de Commerce en futuras actualizaciones.

Consulte la [Guía del usuario de Commerce](https://docs.magento.com/user-guide/stores/store-urls.html).

Para agregar el código de tienda a la dirección URL base:

1. En el _Administrador_ , haga clic en **Tiendas** > **Configuración** > **Configuración** > **General** > **Web**.
1. Desde el **Vista de tienda** en la parte superior de la página, haga clic en **Configuración predeterminada** como se muestra en la siguiente figura.

   ![Seleccione el ámbito de configuración predeterminado](../../assets/configuration/multi-site-default.png)

1. En el panel derecho, expanda **Opciones De Url**.
1. Borre la **Usar valor del sistema** casilla de verificación junto a _Añadir código de tienda a las direcciones URL_.
1. Desde el _Añadir código de tienda a las direcciones URL_ , haga clic en **Sí**.

   ![Añadir el código de tienda a la URL de base de tienda](../../assets/configuration/multi-site-add-store-url.png)

1. Clic **Guardar configuración**.
1. Si se le solicita, vacíe la caché. (**Sistema** > **Administración de caché**).

## Paso 7: cambiar la URL de base de vista de tienda predeterminada

Debe realizar este paso en último lugar porque perderá el acceso al administrador; el acceso vuelve después de configurar los hosts virtuales, tal como se describe en los temas específicos del servidor web.

Para cambiar la URL de base de vista de tienda predeterminada:

1. En el _Administrador_ , haga clic en **Tiendas** > **Configuración** > **Configuración** > **General** > **Web**.

1. Desde el _Vista de tienda_ en la parte superior de la página, haga clic en **Configuración predeterminada**.

   ![Seleccione el ámbito de configuración predeterminado](../../assets/configuration/multi-site-default.png)

1. En el panel derecho, expanda **Direcciones URL base**.
1. En el _Direcciones URL base_ sección, borrar **Usar valor del sistema**.
1. Introduzca el `http://magento.mg` URL en **URL básica** y **URL de vínculo base** campos.

1. Repita el paso anterior en la **URL básicas (seguras)** sección.

   >[!INFO]
   >
   >Si está configurando una dirección URL base para Adobe Commerce en una infraestructura en la nube, debe reemplazar el primer periodo con tres guiones. Por ejemplo, si la dirección URL base es `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, introduzca `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`

1. Clic **Guardar configuración**.


>[!INFO]
>
>El sitio web, la tienda y el código de vista de tienda solo pueden incluir letras (a-z o A-Z), números (0-9) y guiones bajos (_). Además, el primer carácter debe ser una letra. Si se utilizan mayúsculas o minúsculas, internamente la coincidencia no distinguirá entre mayúsculas y minúsculas para dar cabida a la anulación de los ajustes de configuración mediante variables de entorno. Consulte [Utilice variables de entorno para anular los ajustes de configuración](../reference/override-config-settings.md#environment-variables).