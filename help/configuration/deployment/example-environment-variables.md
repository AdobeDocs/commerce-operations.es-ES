---
title: Ejemplo con variables de entorno
description: Vea un ejemplo de cómo establecer valores compartidos, específicos del sistema y confidenciales en el sistema de desarrollo mediante variables de entorno.
exl-id: 98438674-e7f8-4143-9a76-3cc8bf0a73dc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 0%

---

# Ejemplo con variables de entorno

Este ejemplo muestra cómo establecer valores compartidos, específicos del sistema y confidenciales en el sistema de desarrollo y, a continuación, establecer todos los valores en el sistema de producción mediante una combinación de las variables de entorno shared configuration, `config.php` y PHP.

Estos ajustes de configuración se pueden compartir entre los sistemas de desarrollo y producción:

Número de IVA y nombre de tienda de **Tiendas** > Configuración > **Configuración** > General > **General**

Estas opciones de configuración son específicas del sistema o confidenciales, como se indica a continuación:

- Enviar correos electrónicos a (confidencial) desde **Tiendas** > Configuración > **Configuración** > General > **Contactos**
- Dominio de correo electrónico predeterminado (específico del sistema) de **Tiendas** > Configuración > **Configuración** > Clientes > **Configuración del cliente** > **Crear nuevas opciones de cuenta**

Puede utilizar el mismo procedimiento para configurar cualquier configuración en las siguientes referencias:

- [Referencia de rutas de configuración confidenciales y específicas del sistema](../reference/config-reference-sens.md)
- [Referencia de rutas de configuración de pago](../reference/config-reference-payment.md)
- [Referencia de rutas de configuración generales](../reference/config-reference-general.md)
- [Referencia de rutas de configuración de la extensión Commerce Enterprise B2B](../reference/config-reference-b2b.md)

## Antes de empezar

Antes de empezar, configure los permisos y la propiedad del sistema de archivos como se describe en [Requisito previo para los sistemas de desarrollo, compilación y producción](../deployment/prerequisites.md).

## Suposiciones

En este tema se proporciona un ejemplo de cómo modificar la configuración del sistema de producción. Si lo desea, puede elegir diferentes opciones de configuración.

Para los fines de este ejemplo, suponemos lo siguiente:

- Utilice el control de código fuente Git
- El sistema de desarrollo está disponible en un repositorio remoto Git denominado `mconfig`
- Su rama de trabajo de Git se llama `m2.2_deploy`

## Paso 1: Establezca la configuración en el sistema de desarrollo

Para establecer la configuración regional y las unidades de peso predeterminadas en el sistema de desarrollo:

1. Inicie sesión en Admin.
1. Haga clic en **Tiendas** > Configuración > **Configuración** > General > **General**.
1. Si tiene más de un sitio web disponible, use la lista **Vista de tienda** en la esquina superior izquierda para cambiar a otro sitio web, como se muestra en la siguiente ilustración.

   ![Cambiar de sitio web](../../assets/configuration/split-deploy-switch-website.png)

1. En el panel derecho, expanda **Información de almacén**.
1. Si es necesario, borre la casilla de verificación **Usar predeterminado** junto al campo **Número de IVA**.
1. Escriba un número en el campo (por ejemplo, `12345`).
1. En el campo **Nombre de tienda**, escriba un valor (como `My Store`).
1. Haga clic en **Guardar configuración**.
1. Use la lista **Vista de tienda** para seleccionar la **configuración predeterminada**, como se muestra en la siguiente ilustración.

   ![Cambiar a la configuración predeterminada](../../assets/configuration/split-deploy-default-config.png)

1. En el panel de navegación izquierdo, debajo de General, haga clic en **Contactos**.
1. Desactive la casilla de verificación **Usar predeterminado** junto al campo **Enviar correos electrónicos a**.
1. Introduzca una dirección de correo electrónico en el campo.
1. Haga clic en **Guardar configuración**.
1. En el panel izquierdo, haga clic en Clientes > **Configuración del cliente**.
1. En el panel derecho, expanda **Crear nuevas opciones de cuenta**.
1. Desactive la casilla de verificación **Usar valor del sistema** junto al campo **Dominio de correo electrónico predeterminado**.
1. Introduzca un nombre de dominio en el campo.
1. Haga clic en **Guardar configuración**.
1. Si se le solicita, vacíe la caché.

## Paso 2: Actualizar la configuración

Ahora que ha cambiado la configuración en el Administrador, escriba la configuración compartida en un archivo como se describe en esta sección.

{{$include /help/_includes/config-save-config.md}}

Tenga en cuenta que aunque `app/etc/env.php` (la configuración específica del sistema) se actualizó, no la proteja en el control de código fuente. Creará las mismas opciones de configuración en el sistema de producción más adelante en este procedimiento.

## Paso 3: Actualizar el sistema de compilación y generar archivos

Ahora que ha confirmado los cambios en la configuración compartida en el control de código fuente, puede extraer esos cambios en el sistema de generación, compilar código y generar archivos estáticos. El último paso es extraer esos cambios en el sistema de producción.

{{$include /help/_includes/config-update-build-system.md}}

## Paso 4: Actualizar el sistema de producción

El último paso del proceso es actualizar el sistema de producción. Debe hacerlo en dos partes:

- Actualice la configuración confidencial y específica del sistema
- Actualizar la configuración compartida

### Actualice la configuración confidencial y específica del sistema

Para establecer la configuración confidencial y específica del sistema mediante variables de entorno, debe saber lo siguiente:

- Ámbito de cada configuración

  Si ha seguido las instrucciones del paso 1, el ámbito de Envío de correos electrónicos a es global (es decir, el ámbito de Configuración predeterminada) y el ámbito de Dominio de correo electrónico predeterminado es sitio web.

  Debe conocer el código del sitio web para establecer el valor de configuración Predeterminado del dominio de correo electrónico. Consulte [Usar variables de entorno para anular las opciones de configuración](../reference/override-config-settings.md#environment-variables) para obtener más información sobre cómo encontrarlas.

- Ruta de configuración para cada configuración

  Las rutas de configuración utilizadas en este ejemplo son las siguientes:

  | Nombre de configuración | Ruta de configuración |
  |--------------|--------------|
  | Envío de correos electrónicos a | `contact/email/recipient_email` |
  | Dominio de correo electrónico predeterminado | `customer/create_account/email_domain` |

  Puede encontrar todas las rutas de configuración confidenciales y específicas del sistema en [Referencia de rutas de configuración confidenciales y específicas del sistema](../reference/config-reference-sens.md).

#### Convertir rutas de configuración en nombres de variables

Como se describe en [Usar variables de entorno para anular las opciones de configuración](../reference/override-config-settings.md#environment-variables), el formato de las variables es:

```text
<SCOPE>__<SYSTEM__VARIABLE__NAME>
```

El valor de `<SCOPE>` es `CONFIG__DEFAULT__` para el ámbito global o `CONFIG__WEBSITES__<WEBSITE CODE>` para el ámbito del sitio web.

Para encontrar el valor de `<SYSTEM__VARIABLE__NAME>`, reemplace cada carácter `/` en la ruta de configuración con dos guiones bajos.

Los nombres de las variables son:

| Nombre | Ruta de configuración | Nombre de variable |
|--------------|--------------|--------------|
| Envío de correos electrónicos a | `contact/email/recipient_email` | `CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL` |
| Dominio de correo electrónico predeterminado | `customer/create_account/email_domain` | `CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN` |

>[!INFO]
>
>La tabla anterior tiene un código de sitio web de ejemplo, `BASE`, para la configuración predeterminada del dominio de correo electrónico. Reemplace `BASE` por el código de sitio web apropiado para su tienda.

#### Configurar las variables mediante variables de entorno

Puede establecer los valores de las variables en `index.php` con el siguiente formato:

```php
$_ENV['VARIABLE'] = 'value';
```

**Para establecer valores de variables**:

1. Inicie sesión en el sistema de producción como propietario del sistema de archivos o cambie a.
1. Abra `<Commerce root dir>/pub/index.php` en un editor de texto.
1. En cualquier lugar de `index.php`, establezca valores para las variables similares a los siguientes:

   ```php
   $_ENV['CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL'] = 'myname@example.com';
   $_ENV['CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN'] = 'magento.com';
   ```

1. Guarde los cambios en `pub/index.php` y salga del editor de texto.
1. Continúe con la siguiente sección.

### Actualizar la configuración compartida

En esta sección se explica cómo extraer todos los cambios realizados en los sistemas de desarrollo y compilación, lo que actualiza la configuración compartida (nombre del almacén y número de IVA).

{{$include /help/_includes/config-update-prod-system.md}}

### Compruebe los ajustes de configuración en el Administrador

En esta sección se explica cómo puede comprobar los ajustes de configuración en el administrador del sistema de producción.

**Para comprobar las opciones de configuración**:

1. Inicie sesión en el administrador del sistema de producción.
1. Haga clic en **Tiendas** > Configuración > **Configuración** > General > **General**.
1. Use la lista **Vista de tienda** en la esquina superior izquierda para cambiar a otro sitio web.

   Las opciones de configuración compartida establecidas en el sistema de desarrollo se muestran de forma similar a la siguiente.

   ![Comprobar la configuración del sistema de producción](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >El campo **Store Name** se puede editar en el ámbito del sitio web, pero si cambia al ámbito de configuración predeterminado, no se puede editar. Este es el resultado de cómo se establecen las opciones en el sistema de desarrollo. El valor de **Número de IVA** no se puede editar en el ámbito del sitio web.

1. Si aún no lo ha hecho, cambie al ámbito de configuración predeterminada.
1. En el panel de navegación izquierdo, debajo de General, haga clic en **Contactos**.

   El campo **Enviar correos electrónicos a** no se puede editar, como se muestra en la siguiente ilustración. Esta es una configuración confidencial.

   ![Comprobar la configuración del sistema de producción](../../assets/configuration/split-deploy-verify-contacts.png)

1. En el panel izquierdo, haga clic en Clientes > **Configuración del cliente**.
1. En el panel derecho, expanda **Crear nuevas opciones de cuenta**.

   El valor del campo **Dominio de correo electrónico predeterminado** se muestra de la siguiente manera. Esta es una configuración específica del sistema.

   ![Comprobar la configuración del sistema de producción](../../assets/configuration/split-default-domain.png)
