---
title: Verificación final
description: Compruebe que la configuración de Barnish está configurada correctamente para funcionar con la aplicación de Adobe Commerce.
feature: Configuration, Cache
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Verificación final de la configuración del barniz

Ahora que está utilizando el `default.vcl` generado por usted por Commerce, puede realizar algunas verificaciones finales para asegurarse de que Varnish funciona.

## Verificar encabezados de respuesta HTTP

Uso `curl` u otra utilidad para ver los encabezados de respuesta HTTP cuando visita cualquier página de Commerce en un navegador web.

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

## Comprobar tiempos de carga de página

Si Varnish funciona, cualquier página de Commerce con bloques almacenables en caché debe cargarse en menos de 150 ms. Algunos ejemplos de estas páginas son las páginas de categorías de puerta principal y tienda.

Utilice un inspector del explorador para medir los tiempos de carga de las páginas.

Por ejemplo, para utilizar el inspector de Chrome:

1. Acceda a cualquier página de Commerce almacenable en la caché en Chrome.
1. Haga clic con el botón derecho en cualquier parte de la página.
1. En el menú emergente, haga clic en **[!UICONTROL Inspect Element]**
1. En el panel del inspector, haga clic en **[!UICONTROL Network]** pestaña.
1. Actualice la página.
1. Desplácese hasta la parte superior del panel del inspector para ver la dirección URL de la página que está viendo.

   La siguiente figura muestra un ejemplo de carga de la variable `magento2` página de índice.

   ![Haga clic en la página que está viendo](../../assets/configuration/varnish-inspector.png)

   El tiempo de carga de la página se muestra junto a la dirección URL de la página. En este caso, el tiempo de carga es de 5 ms. Esto ayuda a confirmar que Varnish almacenó la página en caché.

1. Para ver los encabezados de respuesta HTTP, haga clic en la dirección URL de la página (en la columna Nombre ).

   Puede ver los encabezados HTTP que se describen con más detalle en la sección Verificar encabezados de respuesta HTTP.

## Verificar la caché de Commerce

Asegúrese de que la `<magento_root>/var/page_cache` el directorio está vacío:

1. Inicie sesión en el servidor de Commerce o cambie a, el propietario del sistema de archivos.
1. Introduzca el siguiente comando:

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. Acceda a una o más páginas de Commerce almacenables en caché.
1. Compruebe la `var/page_cache/` directorio.

   Si el directorio está vacío, ¡enhorabuena! Ha configurado correctamente Varnish y Commerce para que trabajen juntos.

1. Si ha borrado la `var/page_cache/` directorio, reinicie Varnish.

>[!TIP]
>
>Si encuentra errores 503 (Fallo en la recuperación del servidor), consulte [Solución de problemas con errores 503 (servicio no disponible)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshooting-503-errors.html) en el _Centro de ayuda de Adobe Commerce_.
