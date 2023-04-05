---
title: Datos que requieren migración manual
description: Obtenga información sobre los datos que se deben migrar manualmente durante la migración de datos de Magento 1 a Magento 2 y cómo hacerlo.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---


# Datos que requieren migración manual

Hay cuatro tipos de datos que deben migrarse manualmente:

* Medios

* Diseño de tienda

* Cuentas de usuario de administrador

* Listas de control de acceso (ACL)

## Medios

En esta sección se explica cómo migrar manualmente los archivos multimedia.

### Archivos multimedia almacenados en la base de datos

>[!WARNING]
>
>El método de almacenamiento de medios de la base de datos está en desuso a partir del Magento 2.4.3.


Esta sección se aplica a usted *only* si almacena archivos multimedia en la base de datos de Magento. Este paso debe realizarse antes de [migración de datos](data.md):

1. Inicie sesión en el Panel de administración de Magento 1 como administrador.

1. Haga clic en **Sistema** > **Configuración** > AVANZADO > **Sistema**.

1. En el panel derecho, desplácese hasta **Configuración de almacenamiento para medios**.

1. En el **Seleccionar base de datos de medios** , haga clic en el nombre de la base de datos de almacenamiento de medios.

1. Haga clic en **Sincronizar**.

A continuación, repita los mismos pasos en el panel de administración de Magento 2.

### Archivos multimedia del sistema de archivos

Todos los archivos multimedia (imágenes para productos, categorías, el editor WYSIWYG, etc.) deben copiarse manualmente desde `<your Magento 1 install dir>/media` a `<your Magento 2 install dir>/pub/media`.

Sin embargo, sí *not* copie el `.htaccess` archivos ubicados en el Magento 1 `media` carpeta. El Magento 2 tiene su propio `.htaccess` que debe preservarse.

## Diseño de tienda

* El diseño de los archivos (CSS, JS, plantillas, diseños XML) ha cambiado su ubicación y formato

* Actualizaciones de diseño almacenadas en la base de datos. Se coloca a través del administrador de Magento 1 en páginas de CMS, utilidades de CMS, páginas de categorías y páginas de productos

## Listas de control de acceso (ACL)

Debe volver a crear todo manualmente:

* credenciales para API de servicio web (SOAP, XML-RPC y REST)

* cuentas de usuario administrativas y asociarlas con privilegios de acceso

>[!NOTE]
>
>Puede ajustar la zona horaria de una entidad de base de datos mediante la variable `\Migration\Handler\Timezone` controlador. Consulte la [seguimiento](follow-up.md) para obtener más información.
