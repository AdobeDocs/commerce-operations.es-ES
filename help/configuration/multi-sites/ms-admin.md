---
title: Configure varios sitios web, tiendas y vistas de tienda en el administrador
description: Configure sitios web, tiendas y vistas de tiendas adicionales en el administrador de comercio.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 0%

---


# Configurar varias vistas en el Administrador

Esta tarea requiere que cree una categoría raíz (y categorías adicionales, si lo desea) para cada tienda. Las tareas que se tratan en este tema proporcionan una forma de configurar varias tiendas. Para obtener más información, consulte los siguientes recursos en la Guía del usuario de Commerce:

- [Categorías](https://docs.magento.com/user-guide/catalog/categories.html)
- [Adición de sitios web](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Almacenar direcciones URL](https://docs.magento.com/user-guide/stores/store-urls.html)
- [Contenido](https://docs.magento.com/user-guide/cms/content-menu.html)

>[!INFO]
>
>Por ejemplo, solo utilizamos un sitio web francés con código de sitio web `french` en este tema. Para ver tutoriales paso a paso, consulte [Tutorial: Configuración de varios sitios web con Apache](ms-apache.md) y [Tutorial: Configuración de varios sitios web con nginx](ms-nginx.md)

## Paso 1: Crear categorías raíz

La creación de una categoría raíz es opcional, pero se muestra cómo hacerlo en este tutorial en el caso de que desee que cada sitio web tenga una categoría raíz única. Si lo desea, puede crear categorías adicionales.

Para crear una categoría raíz:

1. Inicie sesión en Admin como usuario autorizado para crear categorías.
1. Haga clic en **Catálogo** > **Categorías**.
1. Haga clic en **Agregar categoría raíz**.
1. En el **Nombre de la categoría** , introduzca un nombre único para identificar esta categoría.
1. Asegúrese de que Habilitar categoría está establecido en **Sí**.

   Para obtener información sobre las otras opciones de esta página, consulte [Categorías raíz](https://docs.magento.com/user-guide/catalog/category-root.html).

   La siguiente figura muestra un ejemplo.

   ![Crear y habilitar una categoría raíz](../../assets/configuration/add-root-category.png)

1. Haga clic en **Guardar**.
1. Repita estas tareas tantas veces como sea necesario para crear categorías raíz para las tiendas.

## Paso 2: Creación de sitios web

Para crear un sitio web:

1. Inicie sesión en Admin como usuario autorizado para crear sitios web, tiendas y vistas de tiendas.
1. Haga clic en **Almacenes** > **Configuración** > **Todas las tiendas**.
1. En el _Almacenes_ página, haga clic en **Crear sitio web**.

   - **Nombre**: introduzca un nombre para identificar el sitio web.
   - **Código**—Introduzca un código único; por ejemplo, si tiene una tienda en francés, puede introducir `french`
   - **Orden**: introduzca un orden numérico opcional.

   La siguiente figura muestra un ejemplo.

   ![Agregar un sitio web](../../assets/configuration/multi-site-website.png)

1. Haga clic en **Guardar sitio web**.
1. Repita estas tareas tantas veces como sea necesario para crear sus sitios web.

## Paso 3: Crear tiendas

Para crear una tienda:

1. En el _Administrador_ panel, haga clic en **Almacenes** > **Configuración** > **Todas las tiendas**.
1. En el _Almacenes_ página, haga clic en **Crear tienda**.

   - **Sitio web**—Haga clic en el nombre del sitio web con el que desea asociar este almacén.
   - **Nombre**: introduzca un nombre para identificar el almacén.
   - **Código**: introduzca un código único para identificar el almacén.
   - **Categoría raíz**—Haga clic en el nombre de la categoría raíz de este almacén.

   La siguiente figura muestra un ejemplo.

   ![Añadir una tienda](../../assets/configuration/multi-site-store.png)

1. Haga clic en **Guardar tienda**.
1. Repita estas tareas tantas veces como sea necesario para crear sus tiendas.

## Paso 4: Crear vistas de tiendas

Para crear una vista de tienda:

1. En el _Administrador_ panel, haga clic en **Almacenes** > **Configuración** > **Todas las tiendas**.
1. En la página Tiendas, haga clic en **Crear vista de tienda**.

   - **Tienda**—Haga clic en el nombre del almacén con el que desea asociar esta vista de tienda.
   - **Nombre**: introduzca un nombre para identificar esta vista de tienda.
   - **Código**: introduzca un nombre único para identificar esta vista de tienda.
   - **Estado**—Select **Habilitado**.

   La siguiente figura muestra un ejemplo.

   ![Añadir una tienda](../../assets/configuration/multi-site-storeview.png)

1. Haga clic en **Guardar vista de tienda**.
1. Repita estas tareas tantas veces como sea necesario para crear las vistas de tienda.

## Paso 5: Cambiar la URL base del sitio web

Para acceder a un sitio web usando una dirección URL única como `http://french.magento.mg`, debe cambiar la dirección URL base de cada sitio en el Administrador.

Para cambiar la URL base del sitio web:

1. En el _Administrador_ panel, haga clic en **Almacenes** > **Configuración** > **Configuración** > **General** > **Web**.
1. En el **Vista de la tienda** en la parte superior de la página, haga clic en el nombre de uno de sus sitios web como se muestra en la siguiente figura.

   ![Seleccionar un ámbito](../../assets/configuration/multi-site-scope.png)

1. En el panel derecho, expanda **Direcciones URL base**.
1. En el _Direcciones URL base_ sección, borrar **Usar valor del sistema**.
1. Introduzca la variable `http://french.magento.mg` La URL de **Dirección URL base** y **URL del vínculo base** campos.

1. Repita el paso anterior en el _URL base (segura)_ para obtener más información.

   >[!INFO]
   >
   >Si está configurando una URL base para la implementación de Adobe Commerce en la infraestructura de nube, debe reemplazar el primer período por tres guiones. Por ejemplo, si la dirección URL base es `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, introduzca `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`. Si está configurando una URL base para pruebas locales, utilice un punto.

1. Haga clic en **Guardar configuración**.

1. Repita estas tareas para otros sitios web.

## Paso 6: Añadir el código de tienda a la URL base

Commerce le da la opción de agregar el código de tienda a la URL base del sitio, lo que simplifica el proceso de configurar varias tiendas. Con esta opción, no es necesario crear directorios en el sistema de archivos Commerce para almacenar `index.php` y `.htaccess`.

Esto evita que `index.php` y `.htaccess` de no estar sincronizado con el código de base de comercio en futuras actualizaciones.

Consulte la [Guía del usuario de Commerce](https://docs.magento.com/user-guide/stores/store-urls.html).

Para agregar el código de tienda a la URL base:

1. En el _Administrador_ panel, haga clic en **Almacenes** > **Configuración** > **Configuración** > **General** > **Web**.
1. En el **Vista de la tienda** en la parte superior de la página, haga clic en **Configuración predeterminada** como se muestra en la siguiente figura.

   ![Seleccione el ámbito de configuración predeterminado](../../assets/configuration/multi-site-default.png)

1. En el panel derecho, expanda **Opciones De Url**.
1. Borre la variable **Usar valor del sistema** casilla de verificación junto a _Agregar código de tienda a direcciones URL_.
1. En el _Agregar código de tienda a direcciones URL_ lista, haga clic en **Sí**.

   ![Añadir el código de tienda a la URL de base de la tienda](../../assets/configuration/multi-site-add-store-url.png)

1. Haga clic en **Guardar configuración**.
1. Si se le solicita, vacíe la caché. (**Sistema** > **Administración de caché**).

## Paso 7: Cambiar la URL base de vista de tienda predeterminada

Debe realizar este último paso porque perderá el acceso al administrador; el acceso vuelve después de configurar hosts virtuales, tal como se describe en los temas específicos del servidor web.

Para cambiar la URL base de vista de tienda predeterminada:

1. En el _Administrador_ panel, haga clic en **Almacenes** > **Configuración** > **Configuración** > **General** > **Web**.

1. En el _Vista de la tienda_ en la parte superior de la página, haga clic en **Configuración predeterminada**.

   ![Seleccione el ámbito de configuración predeterminado](../../assets/configuration/multi-site-default.png)

1. En el panel derecho, expanda **Direcciones URL base**.
1. En el _Direcciones URL base_ sección, borrar **Usar valor del sistema**.
1. Introduzca la variable `http://magento.mg` La URL de **Dirección URL base** y **URL del vínculo base** campos.

1. Repita el paso anterior en el **URL base (segura)** para obtener más información.

   >[!INFO]
   >
   >Si está configurando una URL base para Adobe Commerce en la infraestructura de la nube, debe reemplazar el primer período por tres guiones. Por ejemplo, si la dirección URL base es `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, introduzca `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`

1. Haga clic en **Guardar configuración**.
