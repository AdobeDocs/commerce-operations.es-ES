---
title: Verificación final
description: Compruebe que la configuración de Varnish esté correctamente configurada para funcionar con la aplicación Adobe Commerce.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---


# Verificación final de la configuración de Varnish

Ahora está utilizando la variable `default.vcl` generado por Commerce, puede realizar algunas verificaciones finales para asegurarse de que Varnish funciona.

## Verificar encabezados de respuesta HTTP

Uso `curl` u otra utilidad para ver los encabezados de respuesta HTTP cuando visita cualquier página de comercio en un explorador web.

En primer lugar, asegúrese de que está utilizando [modo de desarrollador](../cli/set-mode.md#change-to-developer-mode); de lo contrario, no verá los encabezados.

Por ejemplo,

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Encabezados importantes:

```terminal
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>Este valor también es aceptable: `X-Magento-Cache-Debug: HIT`.

## Comprobar los tiempos de carga de las páginas

Si Varnish está funcionando, cualquier página de comercio con bloques almacenables en caché debe cargarse en menos de 150 ms. Ejemplos de estas páginas son las páginas de categoría de puerta delantera y tienda.

Utilice un inspector del explorador para medir los tiempos de carga de las páginas.

Por ejemplo, para utilizar el inspector de Chrome:

1. Acceda a cualquier página de comercio almacenable en caché de Chrome.
1. Haga clic con el botón derecho en cualquier lugar de la página.
1. En el menú emergente, haga clic en **[!UICONTROL Inspect Element]**
1. En el panel del inspector, haga clic en el botón **[!UICONTROL Network]** pestaña .
1. Actualice la página.
1. Desplácese hasta la parte superior del panel del inspector para ver la dirección URL de la página que está viendo.

   La siguiente figura muestra un ejemplo de carga de la variable `magento2` índice .

   ![Haga clic en la página que está viendo](../../assets/configuration/varnish-inspector.png)

   El tiempo de carga de la página se muestra junto a la dirección URL de la página. En este caso, el tiempo de carga es de 5 ms. Esto ayuda a confirmar que Varnish almacenó en caché la página.

1. Para ver los encabezados de respuesta HTTP, haga clic en la dirección URL de la página (en la columna Nombre ).

   Puede ver los encabezados HTTP que se tratan con más detalle en la sección Verificar encabezados de respuesta HTTP .

## Compruebe la caché de comercio

Asegúrese de que la variable `<magento_root>/var/page_cache` El directorio está vacío:

1. Inicie sesión en el servidor de Commerce o cambie al propietario del sistema de archivos.
1. Introduzca el siguiente comando:

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. Acceda a una o más páginas de Comercio almacenables en caché.
1. Marque la `var/page_cache/` directorio.

   Si el directorio está vacío, ¡felicitaciones! Ha configurado correctamente Varnish y Commerce para trabajar juntos.

1. Si borró el `var/page_cache/` , reinicie Varnish.

>[!TIP]
>
>Si encuentra errores 503 (error de recuperación de backend), consulte [Solución de problemas de errores 503 (servicio no disponible)](https://support.magento.com/hc/en-us/articles/360034631211) en el _Centro de ayuda de Adobe Commerce_.
