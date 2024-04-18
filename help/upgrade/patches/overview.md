---
title: Cómo funcionan los parches
description: Obtenga información sobre los distintos tipos de parches para Adobe Commerce y cómo funcionan.
exl-id: d7072ed4-7d51-41fe-881a-aae3b2000b55
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Cómo funcionan los parches

>[!WARNING]
>
>Se recomienda encarecidamente probar todos los parches en un entorno de ensayo o desarrollo antes de implementarlos en producción. También recomendamos encarecidamente que realice una copia de seguridad de sus datos antes de aplicar un parche. Consulte [Realizar una copia de seguridad y revertir el sistema de archivos](../../installation/tutorials/backup.md).

Los archivos de parche (o diff) son archivos de texto que indican:

- Los archivos que se van a cambiar.
- El número de línea para comenzar el cambio y el número de líneas que se van a cambiar.
- El nuevo código que se va a intercambiar.

Cuando se ejecuta el programa de revisión, este archivo se lee en y se realizan los cambios especificados en los archivos.

Existen tres tipos de parches:

- **Revisiones**: parches que el Adobe publica en el [Centro de seguridad](https://magento.com/security/patches).
- **Parches individuales**: parches que el Soporte de Adobe Commerce crea y distribuye de forma individual.
- **Parches personalizados**: parches no oficiales que se pueden crear a partir de una confirmación de Git.

## Revisiones

Las revisiones son parches que contienen correcciones de alta calidad o seguridad de impacto que afectan a muchos comerciantes. Estas correcciones se aplican a la próxima versión del parche para la versión secundaria aplicable. El Adobe publica revisiones según sea necesario.

Puede encontrar revisiones en la [Centro de seguridad](https://magento.com/security/patches). Siga las instrucciones de la página para descargar el archivo de parche, según la versión y el tipo de instalación. Utilice el [línea de comandos](../patches/apply.md#) o [Compositor](../patches/apply.md) para aplicar parches de revisión.

>[!NOTE]
>
>Las correcciones rápidas pueden contener cambios incompatibles con versiones anteriores.

## Parches individuales

Los parches individuales contienen correcciones de calidad de bajo impacto para un problema específico. Estas correcciones se aplican a la versión menor admitida más recientemente (por ejemplo, 2.4.x), pero podrían no estar presentes en la versión menor admitida anteriormente (por ejemplo, 2.3.x). El Adobe libera los parches individuales según sea necesario.

Utilice el [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"} para aplicar parches individuales.

>[!NOTE]
>
>Los parches individuales no contienen cambios incompatibles con versiones anteriores.

## Parches personalizados

A veces, el equipo de ingeniería de Adobe tarda un tiempo en incluir una corrección de errores realizada en GitHub en una versión del Compositor de Adobe Commerce. Mientras tanto, puede crear un parche desde GitHub y utilizar el [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) para aplicarlo a su instalación basada en Composer.

Utilice el [línea de comandos](apply.md#command-line) o [Compositor](apply.md#composer) para aplicar parches personalizados.

Existen muchas maneras de crear archivos de parche personalizados. El siguiente ejemplo se centra en la creación de un parche a partir de una confirmación de Git conocida.

Para crear un parche personalizado:

1. Crear un `patches/composer` en el proyecto local.
1. Identifique la solicitud de confirmación o extracción de GitHub que se utilizará para el parche. Este ejemplo utiliza el [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede) compromiso, vinculado a un problema de GitHub [#6474](https://github.com/magento/magento2/issues/6474).
1. Adjuntar el `.patch` o el `.diff` extensiones a la URL de confirmación. Uso `.diff` para un tamaño de archivo más pequeño. Por ejemplo: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. Guarde la página como archivo en `patches/composer` directorio. Por ejemplo, `github-issue-6474.diff`.
1. Edite el archivo y elimine `app/code/<VENDOR>/<PACKAGE>` de todas las rutas, de modo que sean relativas a la variable `vendor/<VENDOR>/<PACKAGE>` directorio.

   >[!NOTE]
   >
   >Los editores de texto que eliminan automáticamente los espacios en blanco finales o agregan nuevas líneas pueden romper el parche. Utilice un editor de texto sencillo para realizar estos cambios.

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
+                this.fail();

                 return this;
             },
```

## Aplicación de parches

Puede aplicar parches utilizando cualquiera de los siguientes métodos:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [Línea de comandos](/help/upgrade/patches/apply.md#command-line)
- [Compositor](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>Para aplicar un parche a un proyecto de Adobe Commerce en la nube, consulte [Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en el _Guía de Commerce en la nube_.
