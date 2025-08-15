---
title: Datos que requieren una migración manual
description: Obtenga información sobre los datos que deben migrarse manualmente durante una migración de datos de Magento 1 a Magento 2 y cómo hacerlo.
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Datos que requieren una migración manual

Existen cuatro tipos de datos que deben migrarse manualmente:

* Medios

* Diseño de tienda

* Cuentas de usuario de administrador

* Listas de control de acceso (ACL)

## Medios

En esta sección se explica cómo migrar manualmente archivos multimedia.

### Archivos de medios almacenados en la base de datos

>[!WARNING]
>
>El método de almacenamiento de medios de la base de datos está obsoleto desde Magento 2.4.3.


Esta sección se aplica a usted *solamente* si almacena archivos multimedia en la base de datos de Magento. Este paso se debe realizar antes de la [migración de datos](data.md):

1. Inicie sesión en el Panel de administración de Magento 1 como administrador.

1. Haga clic en **Sistema** > **Configuración** > AVANZADA > **Sistema**.

1. En el panel derecho, desplácese hasta **Configuración de almacenamiento para medios**.

1. En la lista **Seleccionar base de datos de medios**, haga clic en el nombre de la base de datos de almacenamiento de medios.

1. Haga clic en **Sincronizar**.

A continuación, repita los mismos pasos en el panel de administración de Magento 2.

### Archivos multimedia en el sistema de archivos

Todos los archivos multimedia (imágenes para productos, categorías, el editor de WYSIWYG, etc.) se deben copiar manualmente de `<your Magento 1 install dir>/media` a `<your Magento 2 install dir>/pub/media`.

Sin embargo, *no* copia los archivos de `.htaccess` ubicados en la carpeta de Magento 1 `media`. Magento 2 tiene su propio `.htaccess` que se debe conservar.

## Diseño de tienda

* El diseño en archivos (CSS, JS, plantillas, diseños XML) ha cambiado su ubicación y formato

* Actualizaciones de diseño almacenadas en la base de datos. Realizado mediante el administrador de Magento 1 en páginas de CMS, widgets de CMS, páginas de categorías y páginas de productos

## Listas de control de acceso (ACL)

Debe volver a crear manualmente todos los elementos:

* credenciales para las API del servicio web (SOAP, XML-RPC y REST)

* cuentas de usuario administrativas y asociarlas a privilegios de acceso

>[!NOTE]
>
>Puede ajustar la zona horaria de una entidad de base de datos mediante el controlador `\Migration\Handler\Timezone`. Consulte la sección [seguimiento](follow-up.md) para obtener más información.
