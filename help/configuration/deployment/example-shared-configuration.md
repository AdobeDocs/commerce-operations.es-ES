---
title: Ejemplo de uso de una configuración compartida
description: Vea un ejemplo de cómo cambiar la configuración en un sistema de desarrollo con un archivo de configuración compartido.
exl-id: c980ec01-ca2d-43db-b68d-8e9435e07e6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Ejemplo de uso de una configuración compartida

Este ejemplo muestra cómo cambiar la siguiente configuración en el sistema de desarrollo, actualizar el archivo de configuración compartida `config.php` en el sistema de compilación e implementar la misma configuración en el sistema de producción:

- Zona horaria
- Unidad de peso

Esta configuración está disponible en el Administrador en **Tiendas** > Configuración > **Configuración** > General > **General**.

Puede utilizar el mismo procedimiento para configurar cualquier configuración no sensible y no específica del sistema en las siguientes referencias:

- [Referencia de otras rutas de configuración](../reference/config-reference-general.md)
- [Referencia de rutas de configuración de pago](../reference/config-reference-payment.md)
- [Referencia de rutas de configuración de la extensión Commerce Enterprise B2B](../reference/config-reference-b2b.md)

## Antes de empezar

Antes de empezar, configure los permisos y la propiedad del sistema de archivos como se describe en [Requisitos previos para los sistemas de desarrollo, compilación y producción](../deployment/prerequisites.md).

## Suposiciones

En este tema se proporciona un ejemplo de cómo modificar la configuración del sistema de producción. Si lo desea, puede elegir diferentes opciones de configuración.

Para los fines de este ejemplo, suponemos lo siguiente:

- Utilice el control de código fuente Git
- El sistema de desarrollo está disponible en un repositorio remoto Git denominado `mconfig`
- Su rama de trabajo de Git se llama `m2.2_deploy`

## Paso 1: Establezca la configuración en el sistema de desarrollo

Para establecer la zona horaria y las unidades de peso en el sistema de desarrollo:

1. Inicie sesión en Admin.
1. Haga clic en **Tiendas** > Configuración > **Configuración** > General > **General**.
1. En el panel derecho, expanda **Opciones locales**.

   La siguiente figura muestra un ejemplo.

   ![Establecer opciones de configuración regional en el sistema de desarrollo](../../assets/configuration/split-deploy-set-locale.png)

1. En la lista **Zona horaria**, haga clic en **GMT+00:00 (UTC)**.
1. Desactive la casilla de verificación **Usar valor del sistema** junto al campo **Unidad de peso**.
1. En la lista **Unidad de peso**, haga clic en **kgs**.
1. Haga clic en **Guardar configuración**.
1. Si se le solicita, vacíe la caché.

## Paso 2: Actualizar la configuración compartida

Genere el archivo de configuración compartida `app/etc/config.php` en el sistema de desarrollo y transfiéralo mediante el control de código fuente al sistema de compilación, tal como se describe en esta sección.

{{$include /help/_includes/config-save-config.md}}

## Paso 3: Actualizar el sistema de compilación y generar archivos

Ahora que ha confirmado los cambios en la configuración compartida en el control de código fuente, puede extraer esos cambios en el sistema de generación, compilar código y generar archivos estáticos. El último paso es extraer esos cambios en el sistema de producción. Como resultado, la configuración del sistema de producción coincidirá con el sistema de desarrollo.

{{$include /help/_includes/config-update-build-system.md}}

## Paso 4: Actualizar el sistema de producción

El último paso del proceso es actualizar el sistema de producción desde el control de código fuente. Esto extrae todos los cambios realizados en los sistemas de desarrollo y compilación, lo que significa que el sistema de producción está completamente actualizado.

{{$include /help/_includes/config-update-prod-system.md}}

### Verifique los cambios en el Administrador

**Para comprobar que esta configuración no se puede editar en el administrador**:

1. Inicie sesión en Admin.
1. Haga clic en **Tiendas** > Configuración > **Configuración** > General > **General**.
1. En el panel derecho, expanda **Opciones locales**.

   Las opciones que acaba de definir se muestran de la siguiente manera:

   ![Opciones de configuración no editables en el administrador](../../assets/configuration/split-deploy-not-editable.png)

>[!INFO]
>
>Para cambiar una configuración bloqueada en el administrador, use el comando [`magento config:set --lock` ](../cli/set-configuration-values.md).
