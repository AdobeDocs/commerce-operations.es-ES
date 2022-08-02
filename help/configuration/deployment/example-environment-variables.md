---
title: Ejemplo de uso de variables de entorno
description: Consulte un ejemplo de cómo configurar valores compartidos, específicos del sistema y confidenciales en el sistema de desarrollo mediante variables de entorno.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1085'
ht-degree: 0%

---


# Ejemplo de uso de variables de entorno

Este ejemplo muestra cómo configurar valores compartidos, específicos del sistema y confidenciales en el sistema de desarrollo y, a continuación, configurar todos los valores en el sistema de producción mediante una combinación de la configuración compartida. `config.php`y variables de entorno PHP.

Estos ajustes de configuración se pueden compartir entre los sistemas de desarrollo y producción:

Número de IVA y nombre de almacén desde **Almacenes** > Configuración > **Configuración** > General > **General**

Estos ajustes de configuración son específicos del sistema o confidenciales, como se indica:

- Enviar correos electrónicos a (confidenciales) desde **Almacenes** > Configuración > **Configuración** > General > **Contactos**
- Dominio de correo electrónico predeterminado (específico del sistema) de **Almacenes** > Configuración > **Configuración** > Clientes > **Configuración del cliente** > **Crear nuevas opciones de cuenta**

Puede utilizar el mismo procedimiento para configurar cualquier configuración en las siguientes referencias:

- [Referencia de rutas de configuración confidenciales y específicas del sistema](../reference/config-reference-sens.md)
- [Referencia de rutas de configuración de pago](../reference/config-reference-payment.md)
- [Referencia de rutas de configuración generales](../reference/config-reference-general.md)
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
1. Si es necesario, borre la **Utilizar predeterminado** junto a la **Número de IVA** campo .
1. Introduzca un número en el campo (por ejemplo, `12345`).
1. En el **Nombre de la tienda** , introduzca un valor (como `My Store`).
1. Haga clic en **Guardar configuración**.
1. Utilice la variable **Vista de la tienda** para seleccionar la **Configuración predeterminada** como se muestra en la siguiente figura.

   ![Cambiar a la configuración predeterminada](../../assets/configuration/split-deploy-default-config.png)

1. En la navegación izquierda, en General, haga clic en **Contactos**.
1. Borre la variable **Utilizar predeterminado** junto a la **Enviar correos electrónicos a** campo .
1. Introduzca una dirección de correo electrónico en el campo .
1. Haga clic en **Guardar configuración**.
1. En el panel izquierdo, haga clic en Clientes > **Configuración del cliente**.
1. En el panel derecho, expanda **Crear nuevas opciones de cuenta**.
1. Borre la variable **Usar valor del sistema** junto a la **Dominio de correo electrónico predeterminado** campo .
1. Introduzca un nombre de dominio en el campo .
1. Haga clic en **Guardar configuración**.
1. Si se le solicita, vacíe la caché.

## Paso 2: Actualizar la configuración

Ahora que ha cambiado la configuración en Administración, escriba la configuración compartida en un archivo como se explica en esta sección.

{{$include /help/_includes/config-save-config.md}}

Tenga en cuenta que, aunque `app/etc/env.php` (la configuración específica del sistema) se ha actualizado, no la proteja en el control de código fuente. Más adelante en este procedimiento, creará los mismos ajustes de configuración en su sistema de producción.

## Paso 3: Actualice el sistema de compilación y genere archivos

Ahora que ha confirmado los cambios en la configuración compartida al control de código fuente, puede extraer esos cambios en el sistema de compilación, compilar código y generar archivos estáticos. El último paso es extraer esos cambios en el sistema de producción.

{{$include /help/_includes/config-update-build-system.md}}

## Paso 4: Actualización del sistema de producción

El último paso del proceso es actualizar el sistema de producción. Debe hacerlo en dos partes:

- Actualizar la configuración confidencial y específica del sistema
- Actualizar la configuración compartida

### Actualizar la configuración confidencial y específica del sistema

Para establecer la configuración confidencial y específica del sistema mediante variables de entorno, debe saber lo siguiente:

- Ámbito de cada configuración

   Si ha seguido las instrucciones del paso 1, el ámbito de Envío de correos electrónicos a es global (es decir, el ámbito de Configuración predeterminada) y el ámbito de Dominio de correo electrónico predeterminado es el sitio web.

   Debe conocer el código del sitio web para establecer el valor de configuración Dominio de correo electrónico predeterminado . Consulte [Usar variables de entorno para anular los ajustes de configuración](../reference/override-config-settings.md#environment-variables) para obtener más información sobre cómo encontrarlo.

- Ruta de configuración para cada configuración

   Las rutas de configuración utilizadas en este ejemplo son las siguientes:

   | Nombre de configuración | Ruta de configuración |
   |--------------|--------------|
   | Enviar correos electrónicos a | `contact/email/recipient_email` |
   | Dominio de correo electrónico predeterminado | `customer/create_account/email_domain` |

   Puede encontrar todas las rutas de configuración sensibles y específicas del sistema en [Referencia de rutas de configuración confidenciales y específicas del sistema](../reference/config-reference-sens.md).

#### Conversión de rutas de configuración en nombres de variables

Como se explica en [Usar variables de entorno para anular los ajustes de configuración](../reference/override-config-settings.md#environment-variables), el formato de las variables es:

```text
<SCOPE>__<SYSTEM__VARIABLE__NAME>
```

El valor de `<SCOPE>` es `CONFIG__DEFAULT__` para el ámbito global o `CONFIG__WEBSITES__<WEBSITE CODE>` para el ámbito del sitio web.

Para buscar el valor de `<SYSTEM__VARIABLE__NAME>`, reemplace cada `/` en la ruta de configuración con dos guiones bajos.

Los nombres de las variables son los siguientes:

| Nombre | Ruta de configuración | Nombre de variable |
|--------------|--------------|--------------|
| Enviar correos electrónicos a | `contact/email/recipient_email` | `CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL` |
| Dominio de correo electrónico predeterminado | `customer/create_account/email_domain` | `CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN` |

>[!INFO]
>
>La tabla anterior tiene un código de sitio web de ejemplo, `BASE`, para el ajuste de configuración Dominio de correo electrónico predeterminado . Reemplazar `BASE` con el código de sitio web apropiado para su tienda.

#### Configure las variables mediante variables de entorno

Puede establecer los valores de las variables en la variable `index.php` con el siguiente formato:

```php
$_ENV['VARIABLE'] = 'value';
```

**Para establecer los valores de las variables**:

1. Inicie sesión en su sistema de producción como propietario del sistema de archivos o cambie a él.
1. Apertura `<Commerce root dir>/pub/index.php` en un editor de texto.
1. En cualquier sitio de `index.php`, establezca valores para las variables similares a los siguientes:

   ```php
   $_ENV['CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL'] = 'myname@example.com';
   $_ENV['CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN'] = 'magento.com';
   ```

1. Guarde los cambios en `pub/index.php` y salga del editor de texto.
1. Continúe con la siguiente sección.

### Actualizar la configuración compartida

En esta sección se explica cómo extraer todos los cambios realizados en los sistemas de desarrollo y compilación, que actualizan los ajustes de configuración compartidos (Nombre de almacén y Número de IVA).

{{$include /help/_includes/config-update-prod-system.md}}

### Verificar los ajustes de configuración en el Administrador

En esta sección se explica cómo puede verificar los ajustes de configuración en el administrador del sistema de producción.

**Para verificar los ajustes de configuración**:

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
