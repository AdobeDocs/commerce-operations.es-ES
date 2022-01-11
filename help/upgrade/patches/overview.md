---
title: Cómo funcionan los parches
description: Obtenga información sobre los distintos tipos de parches para Adobe Commerce y Magento Open Source y cómo funcionan.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 0%

---


# Funcionamiento de los parches

>[!WARNING]
>
>Recomendamos encarecidamente que pruebe todos los parches en un entorno de ensayo o desarrollo antes de implementarlos en producción. También recomendamos encarecidamente que realice una copia de seguridad de sus datos antes de aplicar un parche. Consulte [Hacer una copia de seguridad y revertir el sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

Los archivos de parches (o diferencias) son archivos de texto que señalan:

- Los archivos que se van a cambiar.
- El número de línea para comenzar el cambio y el número de líneas que desea cambiar.
- El nuevo código que se va a intercambiar.

Cuando la variable [parche](https://en.wikipedia.org/wiki/Patch_(Unix)) se ejecuta, este archivo se lee en y los cambios especificados se realizan en los archivos.

Existen tres tipos de parches:

- **Revisiones**: parches que el Adobe publica en el [Centro de seguridad](https://magento.com/security/patches).
- **Revisiones individuales**: parches que Adobe Commerce Support crea y distribuye de forma individual.
- **Revisiones personalizadas**: parches no oficiales que se pueden crear a partir de una confirmación git.

## Revisiones

Las revisiones son parches que contienen correcciones de calidad o seguridad de alto impacto que afectan a muchos comerciantes. Estas correcciones se aplican a la siguiente versión del parche para la versión menor correspondiente. Adobe libera revisiones según sea necesario.

Puede encontrar revisiones en la [Centro de seguridad](https://magento.com/security/patches). Siga las instrucciones de la página para descargar el archivo del parche, según su versión y el tipo de instalación. Utilice la variable [línea de comandos](../patches/apply.md#) o [Compositor](../patches/apply.md) para aplicar parches de corrección.

>[!NOTE]
>
>Las correcciones rápidas pueden contener cambios incompatibles con versiones anteriores.

## Revisiones individuales

Los parches individuales contienen correcciones de calidad de bajo impacto para un problema específico. Estas correcciones se aplican a la versión menor admitida más recientemente (por ejemplo, 2.4.x), pero podría no encontrarse en la versión secundaria compatible anterior (por ejemplo, 2.3.x). Adobe libera parches individuales según sea necesario.

Utilice la variable [Herramienta Parches de calidad](https://devdocs.magento.com/quality-patches/tool.html) para aplicar parches individuales.

>[!NOTE]
>
>Los parches individuales no contienen cambios incompatibles con versiones anteriores.

## Revisiones personalizadas

A veces, el equipo de ingeniería de Adobe tarda un tiempo en incluir una corrección de errores realizada en GitHub en una versión de Adobe Commerce o del Compositor de Magento Open Source. Mientras tanto, puede crear un parche desde GitHub y usar la variable [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) para aplicarlo a su instalación basada en Composer.

Utilice la variable [línea de comandos] o [Compositor] para aplicar parches personalizados.

Existen muchas maneras de crear archivos de parches personalizados. El siguiente ejemplo se centra en la creación de un parche a partir de una confirmación git conocida.

Para crear un parche personalizado:

1. Cree un `patches/composer` en el proyecto local.
1. Identifique la confirmación o la solicitud de extracción de GitHub que se utilizará para el parche. Este ejemplo utiliza la variable [`2d31571`](https://github.com/magento/magento2/commit/) confirmar, vinculado a un problema de GitHub [#6474](https://github.com/magento/magento2/issues/6474).
1. Anexe la variable `.patch` o `.diff` extensiones a la URL de confirmación. Uso `.diff` para un tamaño de archivo más pequeño. Por ejemplo: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. Guarde la página como un archivo en el `patches/composer` directorio. Por ejemplo, `github-issue-6474.diff`.
1. Edite el archivo y elimine `app/code/<VENDOR>/<PACKAGE>` desde todas las rutas para que sean relativas a la variable `vendor/<VENDOR>/<PACKAGE>` directorio.

   >[!NOTE]
   >
   >Los editores de texto que quitan automáticamente los espacios en blanco finales o agregan nuevas líneas pueden romper el parche. Utilice un editor de texto simple para realizar estos cambios.

El siguiente ejemplo muestra el archivo DIFF mencionado anteriormente después de eliminar todas las instancias de `app/code/Magento/Payment`:

```diff
diff --git a/view/frontend/web/js/view/payment/iframe.js b/view/frontend/web/js/view/payment/iframe.js
index c8a6fef58d31..7d01c195791e 100644
--- a/view/frontend/web/js/view/payment/iframe.js
+++ b/view/frontend/web/js/view/payment/iframe.js
@@ -154,6 +154,7 @@ define(
              */
              clearTimeout: function () {
                  clearTimeout(this.timeoutId);
                  this.fail();
                  return this;
            },
```

## Aplicación de parches

Puede aplicar parches mediante cualquiera de los siguientes métodos:

- [Herramienta Parches de calidad](https://devdocs.magento.com/quality-patches/tool.html)
- [Línea de comandos](../patches/apply.md#command-line)
- [Compositor](../patches/apply.md#composer)

>[!NOTE]
>
>Para aplicar un parche a un proyecto de infraestructura de nube de Adobe Commerce, consulte [Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en el _Guía de Cloud_.
