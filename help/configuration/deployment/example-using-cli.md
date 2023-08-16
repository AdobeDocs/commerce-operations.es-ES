---
title: Ejemplo con comandos CLI
description: Vea un ejemplo de cómo establecer valores compartidos, específicos del sistema y confidenciales en el sistema de desarrollo mediante la línea de comandos.
exl-id: d0058e9f-a5a9-48a6-9c66-c61515666335
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---

# Ejemplo con comandos CLI

Este ejemplo muestra cómo establecer valores compartidos, específicos del sistema y confidenciales en el sistema de desarrollo y, a continuación, implementar esos valores en el sistema de producción.
Esto se realiza mediante una combinación de configuraciones compartidas, las `config.php` y el comando CLI de Commerce.

Este ejemplo utiliza las opciones de configuración siguientes:

- **Número de iva** y **Nombre del almacén** para los ajustes de configuración compartidos.

  Se encuentran en **Tiendas** > Configuración > **Configuración** > General > **General**.

- **Envío de correos electrónicos a** para el valor de configuración confidencial.

  Esto se encuentra en **Tiendas** > Configuración > **Configuración** > General > **Contactos**.

- **Dominio de correo electrónico predeterminado** para el valor de configuración específico del sistema.

  Esto se encuentra en **Tiendas** > Configuración > **Configuración** > Clientes > **Configuración del cliente** > **Crear nuevas opciones de cuenta**.

Puede utilizar el mismo procedimiento mostrado en este ejemplo para configurar cualquier configuración en las siguientes referencias:

- [Referencia de rutas de configuración confidenciales y específicas del sistema](../reference/config-reference-sens.md)
- [Referencia de rutas de configuración de pago](../reference/config-reference-payment.md)
- [Referencia de otras rutas de configuración](../reference/config-reference-general.md)
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
1. Clic **Tiendas** > Configuración > **Configuración** > General > **General**.
1. Si tiene más de un sitio web disponible, utilice el **Vista de tienda** en la esquina superior izquierda para cambiar a un sitio web diferente, como se muestra en la siguiente ilustración.

   ![Cambiar sitios web](../../assets/configuration/split-deploy-switch-website.png)

1. En el panel derecho, expanda **Información de tienda**.
1. Si es necesario, borre la **Usar valor predeterminado** junto a la casilla de verificación **Número de IVA** y **Nombre del almacén** campos.
1. Introduzca un número en el campo (por ejemplo, `12345`).
1. En el **Nombre del almacén** , introduzca un valor (como `My Store`).
1. Clic **Guardar configuración**.
1. En el panel de navegación izquierdo, en General, haga clic en **Contactos**.
1. En el panel derecho, expanda **Opciones de correo electrónico**.
1. Si es necesario, borre la **Usar valor predeterminado** junto a la casilla de verificación **Envío de correos electrónicos a** field.
1. Introduzca una dirección de correo electrónico en el campo.
1. Clic **Guardar configuración**.
1. Utilice el **Vista de tienda** para seleccionar el **Configuración predeterminada** como se muestra en la siguiente figura.

   ![Cambiar a la configuración predeterminada](../../assets/configuration/split-deploy-default-config.png)

1. En el panel izquierdo, haga clic en Clientes > **Configuración del cliente**.
1. En el panel derecho, expanda **Crear nuevas opciones de cuenta**.
1. Si es necesario, borre la **Usar valor del sistema** junto a la casilla de verificación **Dominio de correo electrónico predeterminado** field.
1. Introduzca un nombre de dominio en el campo.
1. Clic **Guardar configuración**.
1. Si se le solicita, vacíe la caché.

## Paso 2: Actualizar la configuración

Ahora que ha cambiado la configuración en el Administrador, escriba la configuración compartida en un archivo como siguiendo los pasos siguientes:

{{$include /help/_includes/config-save-config.md}}

Aunque `app/etc/env.php` (la configuración específica del sistema), no la proteja en el control de código fuente.
Creará las mismas opciones de configuración en el sistema de producción más adelante en este procedimiento.

## Paso 3: Actualizar el sistema de compilación y generar archivos

Ahora que ha confirmado los cambios en la configuración compartida en el control de código fuente, puede extraer esos cambios en el sistema de generación, compilar el código y generar archivos estáticos.

{{$include /help/_includes/config-update-build-system.md}}

## Paso 4: Actualizar el sistema de producción

El último paso del proceso es actualizar el sistema de producción. Debe hacerlo en dos partes:

- Actualice la configuración confidencial y específica del sistema
- Actualizar la configuración compartida

### Actualice la configuración confidencial y específica del sistema

Para establecer la configuración confidencial y específica del sistema mediante variables de entorno, debe saber lo siguiente:

- Ámbito de cada configuración

  Si ha seguido las instrucciones del paso 1, el ámbito de **Envío de correos electrónicos a** es un sitio web y el ámbito para **Dominio de correo electrónico predeterminado** es global (es decir, el ámbito de configuración predeterminado).

  Necesita el código del sitio web para establecer la variable **Envío de correos electrónicos a** valor de configuración.

  Para obtener más información sobre cómo encontrar este valor, consulte: [Utilice variables de entorno para anular los ajustes de configuración](../reference/override-config-settings.md#environment-variables).

- Rutas de configuración para las opciones utilizadas en este ejemplo:

  | Nombre de configuración | Ruta de configuración |
  | -------------------- | -------------------------------------- |
  | Envío de correos electrónicos a | `contact/email/recipient_email` |
  | Dominio de correo electrónico predeterminado | `customer/create_account/email_domain` |

  Para todas las rutas de configuración confidenciales y específicas del sistema, consulte: [Referencia de rutas de configuración confidenciales y específicas del sistema](../reference/config-reference-sens.md).

### Establecer las variables mediante comandos CLI

Utilice los siguientes comandos de CLI para establecer las opciones de configuración específicas del sistema y confidenciales:

- `magento config:set` para la configuración específica del sistema
- `magento config:sensitive:set` para configuración confidencial

Para establecer la configuración específica del sistema **Dominio de correo electrónico predeterminado**, que se encuentra en el ámbito predeterminado, utilice el siguiente comando:

```bash
bin/magento config:set customer/create_account/email_domain <email domain>
```

No es necesario utilizar el ámbito en el comando porque es el ámbito predeterminado.

Para establecer los valores de **Envío de correos electrónicos a**, sin embargo, debe conocer el tipo de ámbito (`website`) y el código de ámbito, que es probablemente diferente en cada sitio.

Ejemplo:

```unix
bin/magento config:sensitive:set contact/email/recipient_email --scope=website --scope-code=<website code> <email address>
```

### Actualizar la configuración compartida

En esta sección se explica cómo extraer todos los cambios realizados en los sistemas de desarrollo y compilación en un entorno de producción, lo que actualiza la configuración compartida (nombre del almacén y número de IVA).

{{$include /help/_includes/config-update-prod-system.md}}

### Compruebe los ajustes de configuración en el Administrador

Para comprobar las opciones de configuración:

1. Inicie sesión en el administrador del sistema de producción.
1. Clic **Tiendas** > Configuración > **Configuración** > General > **General**.
1. Utilice el **Vista de tienda** en la esquina superior izquierda para cambiar a un sitio web diferente.

   Las opciones de configuración compartida establecidas en el sistema de desarrollo se muestran de forma similar a la siguiente.

   ![Compruebe la configuración en el sistema de producción](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >El **Nombre del almacén** El campo es editable en el ámbito del sitio web, pero si cambia al ámbito de configuración predeterminado, no es editable. Este es el resultado de cómo se establecen las opciones en el sistema de desarrollo. El valor de **Número de IVA** no se puede editar en el ámbito del sitio web.

1. Si aún no lo ha hecho, cambie al ámbito de configuración predeterminada.
1. En el panel de navegación izquierdo, en General, haga clic en **Contactos**.

   El **Envío de correos electrónicos a** El campo no se puede editar, como se muestra en la figura siguiente. Esta es una configuración confidencial.

   ![Compruebe la configuración en el sistema de producción](../../assets/configuration/split-deploy-verify-contacts.png)

1. En el panel izquierdo, haga clic en Clientes > **Configuración del cliente**.
1. En el panel derecho, expanda **Crear nuevas opciones de cuenta**.

   El valor del **Dominio de correo electrónico predeterminado** El campo se muestra de la siguiente manera. Esta es una configuración específica del sistema.

   ![Compruebe la configuración en el sistema de producción](../../assets/configuration/split-default-domain.png)
