---
title: Ejemplo de uso de una configuración compartida
description: Consulte un ejemplo de cómo cambiar la configuración en un sistema de desarrollo con un archivo de configuración compartido.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---


# Ejemplo de uso de una configuración compartida

Este ejemplo muestra cómo cambiar las siguientes opciones de configuración en el sistema de desarrollo, actualizar el archivo de configuración compartido, `config.php`, en el sistema de compilación e implemente la misma configuración en el sistema de producción:

- Zona horaria
- Unidad de peso

Estas opciones de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > General > **General**.

Puede utilizar el mismo procedimiento para configurar cualquier configuración no sensible y no específica del sistema en las siguientes referencias:

- [Otras referencias de rutas de configuración](../reference/config-reference-general.md)
- [Referencia de rutas de configuración de pago](../reference/config-reference-payment.md)
- [Referencia de rutas de configuración de la extensión B2B de Commerce Enterprise](../reference/config-reference-b2b.md)

## Antes de empezar

Antes de empezar, configure los permisos y la propiedad del sistema de archivos como se explica en [Requisitos previos para los sistemas de desarrollo, construcción y producción](../deployment/prerequisites.md).

## Suposiciones

Este tema proporciona un ejemplo de modificación de la configuración del sistema de producción. Si lo desea, puede elegir diferentes opciones de configuración.

A los efectos de este ejemplo, suponemos lo siguiente:

- Se utiliza el control de origen Git
- El sistema de desarrollo está disponible en un repositorio remoto de Git llamado `mconfig`
- Su rama de trabajo de Git tiene el nombre `m2.2_deploy`

## Paso 1: Establezca la configuración en el sistema de desarrollo

Para establecer la zona horaria y las unidades de peso en el sistema de desarrollo:

1. Inicie sesión en el administrador.
1. Haga clic en **Almacenes** > Configuración > **Configuración** > General > **General**.
1. En el panel derecho, expanda **Opciones de configuración regional**.

   La siguiente figura muestra un ejemplo.

   ![Establecer opciones de configuración regional en el sistema de desarrollo](../../assets/configuration/split-deploy-set-locale.png)

1. En el **Zona horaria** lista, haga clic en **GMT+00:00 (UTC)**.
1. Borre la variable **Usar valor del sistema** junto a la **Unidad de peso** campo .
1. En el **Unidad de peso** lista, haga clic en **kgs**.
1. Haga clic en **Guardar configuración**.
1. Si se le solicita, vacíe la caché.

## Paso 2: Actualizar la configuración compartida

Genere el archivo de configuración compartido, `app/etc/config.php`, en su sistema de desarrollo y transfiéralo mediante el control de código fuente a su sistema de compilación, tal como se explica en esta sección.

{{$include /help/_includes/config-save-config.md}}

## Paso 3: Actualice el sistema de compilación y genere archivos

Ahora que ha confirmado los cambios en la configuración compartida al control de código fuente, puede extraer esos cambios en el sistema de compilación, compilar código y generar archivos estáticos. El último paso es extraer esos cambios en el sistema de producción. Como resultado, la configuración de su sistema de producción coincidirá con su sistema de desarrollo.

{{$include /help/_includes/config-update-build-system.md}}

## Paso 4: Actualización del sistema de producción

El último paso en el proceso es actualizar el sistema de producción desde el control de código fuente. Esto extrae todos los cambios realizados en sus sistemas de desarrollo y construcción, lo que significa que su sistema de producción está completamente actualizado.

{{$include /help/_includes/config-update-prod-system.md}}

### Verificar los cambios en el Administrador

**Para verificar que esta configuración no se puede editar en el administrador**:

1. Inicie sesión en el administrador.
1. Haga clic en **Almacenes** > Configuración > **Configuración** > General > **General**.
1. En el panel derecho, expanda **Opciones de configuración regional**.

   Las opciones que acaba de configurar se muestran de la siguiente manera:

   ![Opciones de configuración no editables en el Administrador](../../assets/configuration/split-deploy-not-editable.png)

>[!INFO]
>
>Para cambiar una configuración que esté bloqueada en el Administrador, use el [`magento config:set --lock` command](../cli/set-configuration-values.md).
