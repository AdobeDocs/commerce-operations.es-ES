---
title: Ejemplo de uso de comandos CLI
description: Consulte un ejemplo de cómo configurar valores compartidos, específicos del sistema y confidenciales en el sistema de desarrollo mediante la línea de comandos.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---


# Ejemplo de uso de comandos CLI

En este ejemplo se muestra cómo configurar valores compartidos, específicos del sistema y confidenciales en el sistema de desarrollo y, a continuación, implementarlos en el sistema de producción.
Esto se hace mediante una combinación de configuraciones compartidas, la variable `config.php` y Commerce CLI.

Este ejemplo utiliza los siguientes ajustes de configuración:

- **Número Vat** y **Nombre de la tienda** para los ajustes de configuración compartidos.

   Estos se encuentran en **Almacenes** > Configuración > **Configuración** > General > **General**.

- **Enviar correos electrónicos a** para el valor de configuración confidencial.

   Esto se encuentra en **Almacenes** > Configuración > **Configuración** > General > **Contactos**.

- **Dominio de correo electrónico predeterminado** para el valor de configuración específico del sistema.

   Esto se encuentra en **Almacenes** > Configuración > **Configuración** > Clientes > **Configuración del cliente** > **Crear nuevas opciones de cuenta**.

Puede utilizar el mismo procedimiento mostrado en este ejemplo para configurar cualquier configuración en las siguientes referencias:

- [Referencia de rutas de configuración confidenciales y específicas del sistema](../reference/config-reference-sens.md)
- [Referencia de rutas de configuración de pago](../reference/config-reference-payment.md)
- [Otras referencias de rutas de configuración](../reference/config-reference-general.md)
- [Referencia de rutas de configuración de la extensión B2B de Commerce Enterprise](../reference/config-reference-b2b.md)

## Antes de empezar

Antes de empezar, configure los permisos y la propiedad del sistema de archivos como se explica en [Requisito previo para los sistemas de desarrollo, construcción y producción](../deployment/prerequisites.md).

## Suposiciones

Este tema proporciona un ejemplo de modificación de la configuración del sistema de producción. Si lo desea, puede elegir diferentes opciones de configuración.

A los efectos de este ejemplo, suponemos lo siguiente:

- Se utiliza el control de origen Git
- El sistema de desarrollo está disponible en un repositorio remoto de Git llamado `mconfig`
- Su rama de trabajo de Git tiene el nombre `m2.2_deploy`

## Paso 1: Establezca la configuración en el sistema de desarrollo

Para configurar la configuración regional y las unidades de peso predeterminadas en el sistema de desarrollo:

1. Inicie sesión en el administrador.
1. Haga clic en **Almacenes** > Configuración > **Configuración** > General > **General**.
1. Si tiene más de un sitio web disponible, use el **Vista de la tienda** en la esquina superior izquierda para cambiar a un sitio web diferente, como se muestra en la siguiente ilustración.

   ![Cambiar sitios web](../../assets/configuration/split-deploy-switch-website.png)

1. En el panel derecho, expanda **Información del almacén**.
1. Si es necesario, borre la **Utilizar predeterminado** junto a la **Número de IVA** y **Nombre de la tienda** campos.
1. Introduzca un número en el campo (por ejemplo, `12345`).
1. En el **Nombre de la tienda** , introduzca un valor (como `My Store`).
1. Haga clic en **Guardar configuración**.
1. En la navegación izquierda, en General, haga clic en **Contactos**.
1. En el panel derecho, expanda **Opciones de correo electrónico**.
1. Si es necesario, borre la **Utilizar predeterminado** junto a la **Enviar correos electrónicos a** campo .
1. Introduzca una dirección de correo electrónico en el campo .
1. Haga clic en **Guardar configuración**.
1. Utilice la variable **Vista de la tienda** para seleccionar la **Configuración predeterminada** como se muestra en la siguiente figura.

   ![Cambiar a la configuración predeterminada](../../assets/configuration/split-deploy-default-config.png)

1. En el panel izquierdo, haga clic en Clientes > **Configuración del cliente**.
1. En el panel derecho, expanda **Crear nuevas opciones de cuenta**.
1. Si es necesario, borre la **Usar valor del sistema** junto a la **Dominio de correo electrónico predeterminado** campo .
1. Introduzca un nombre de dominio en el campo .
1. Haga clic en **Guardar configuración**.
1. Si se le solicita, vacíe la caché.

## Paso 2: Actualizar la configuración

Ahora que ha cambiado la configuración en Administración, escriba la configuración compartida en un archivo siguiendo los pasos siguientes:

{{$include /help/_includes/config-save-config.md}}

Aunque `app/etc/env.php` (la configuración específica del sistema) se ha actualizado, no la proteja en el control de código fuente.
Más adelante en este procedimiento, creará los mismos ajustes de configuración en su sistema de producción.

## Paso 3: Actualice el sistema de compilación y genere archivos

Ahora que ha confirmado los cambios en la configuración compartida al control de código fuente, puede extraer esos cambios en el sistema de compilación, compilar el código y generar archivos estáticos.

{{$include /help/_includes/config-update-build-system.md}}

## Paso 4: Actualización del sistema de producción

El último paso del proceso es actualizar el sistema de producción. Debe hacerlo en dos partes:

- Actualizar la configuración confidencial y específica del sistema
- Actualizar la configuración compartida

### Actualizar la configuración confidencial y específica del sistema

Para establecer la configuración confidencial y específica del sistema mediante variables de entorno, debe saber lo siguiente:

- Ámbito de cada configuración

   Si sigue las instrucciones del paso 1, el ámbito de aplicación de **Enviar correos electrónicos a** su sitio web y el ámbito de aplicación **Dominio de correo electrónico predeterminado** es global (es decir, el ámbito de configuración predeterminada).

   Necesita el código de sitio web para establecer la variable **Enviar correos electrónicos a** valor de configuración.

   Para obtener más información sobre cómo encontrar este valor, consulte: [Usar variables de entorno para anular los ajustes de configuración](../reference/override-config-settings.md#environment-variables).

- Rutas de configuración para los ajustes utilizados en este ejemplo:

   | Nombre de configuración | Ruta de configuración |
   | -------------------- | -------------------------------------- |
   | Enviar correos electrónicos a | `contact/email/recipient_email` |
   | Dominio de correo electrónico predeterminado | `customer/create_account/email_domain` |

   Para todas las rutas de configuración sensibles y específicas del sistema, consulte: [Referencia de rutas de configuración confidenciales y específicas del sistema](../reference/config-reference-sens.md).

### Configure las variables mediante comandos CLI

Utilice los siguientes comandos CLI para establecer los ajustes de configuración sensibles y específicos del sistema:

- `magento config:set` para la configuración específica del sistema
- `magento config:sensitive:set` para la configuración confidencial

Para establecer la configuración específica del sistema **Dominio de correo electrónico predeterminado**, que se encuentra en el ámbito predeterminado, utilice el siguiente comando:

```bash
bin/magento config:set customer/create_account/email_domain <email domain>
```

No es necesario utilizar el ámbito en el comando porque es el ámbito predeterminado.

Para establecer los valores de **Enviar correos electrónicos a**, sin embargo, debe conocer el tipo de ámbito (`website`) y el código de ámbito, que es probablemente diferente en cada sitio.

Ejemplo:

```unix
bin/magento config:sensitive:set contact/email/recipient_email --scope=website --scope-code=<website code> <email address>
```

### Actualizar la configuración compartida

En esta sección se explica cómo extraer todos los cambios realizados en los sistemas de desarrollo y compilación a un entorno de producción, que actualiza los ajustes de configuración compartidos (Nombre del almacén y Número de IVA).

{{$include /help/_includes/config-update-prod-system.md}}

### Verificar los ajustes de configuración en el Administrador

Para verificar los ajustes de configuración:

1. Inicie sesión en el administrador del sistema de producción.
1. Haga clic en **Almacenes** > Configuración > **Configuración** > General > **General**.
1. Utilice la variable **Vista de la tienda** en la esquina superior izquierda para cambiar a un sitio web diferente.

   Las opciones de configuración compartida que configuró en el sistema de desarrollo se muestran de forma similar a la siguiente.

   ![Comprobar la configuración en el sistema de producción](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >La variable **Nombre de la tienda** El campo es editable en el ámbito del sitio web, pero si cambia al ámbito Configuración predeterminada , no se puede editar. Este es el resultado de cómo se configuran las opciones en el sistema de desarrollo. El valor de **Número de IVA** no se puede editar en el ámbito del sitio web.

1. Si aún no lo ha hecho, cambie al ámbito de configuración predeterminada.
1. En la navegación izquierda, en General, haga clic en **Contactos**.

   La variable **Enviar correos electrónicos a** no se puede editar, como se muestra en la siguiente figura. Se trata de un ajuste delicado.

   ![Comprobar la configuración en el sistema de producción](../../assets/configuration/split-deploy-verify-contacts.png)

1. En el panel izquierdo, haga clic en Clientes > **Configuración del cliente**.
1. En el panel derecho, expanda **Crear nuevas opciones de cuenta**.

   El valor de la variable **Dominio de correo electrónico predeterminado** se muestra de la siguiente manera. Es una configuración específica del sistema.

   ![Comprobar la configuración en el sistema de producción](../../assets/configuration/split-default-domain.png)
