---
title: Verificar configuración de barniz
description: Aprenda a realizar la verificación final de la configuración de Barniz con Adobe Commerce. Descubra los pasos de prueba y las técnicas de solución de problemas.
feature: Configuration, Cache
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
badgePaas: label="En las instalaciones" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 379
ht-degree: 0%

---

# Verificar configuración de barniz {#final-verification}

Ahora que está usando el `default.vcl` generado por Commerce, puede realizar algunas comprobaciones finales para asegurarse de que Varnish funciona.

{{varnish-config-cloud}}

## Verificar encabezados de respuesta HTTP

Utilice `curl` u otra utilidad para ver los encabezados de respuesta HTTP cuando visite cualquier página de Commerce en un explorador web.

Primero, asegúrese de que está usando [modo de desarrollador](../cli/set-mode.md#change-to-developer-mode); de lo contrario, no verá los encabezados.

Por ejemplo,

```shell
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Encabezados importantes:

```text
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

1. Acceda a cualquier página de Commerce almacenable en caché en Chrome.
1. Haga clic con el botón derecho en cualquier parte de la página.
1. En el menú emergente, haga clic en **[!UICONTROL Inspect Element]**
1. En el panel del inspector, haga clic en la ficha **[!UICONTROL Network]**.
1. Actualice la página.
1. Desplácese hasta la parte superior del panel del inspector para ver la dirección URL de la página que está viendo.

   En la ilustración siguiente se muestra un ejemplo de cómo cargar la página de índice `magento2`.

   ![Haga clic en la página que está viendo](../../assets/configuration/varnish-inspector.png)

   El tiempo de carga de la página se muestra junto a la dirección URL de la página. En este caso, el tiempo de carga es de 5 ms. Esto ayuda a confirmar que Varnish almacenó la página en caché.

1. Para ver los encabezados de respuesta HTTP, haga clic en la dirección URL de la página (en la columna Nombre ).

   Puede ver los encabezados HTTP que se describen con más detalle en la sección Verificar encabezados de respuesta HTTP.

## Verifique la caché de Commerce

Asegúrese de que el directorio `<magento_root>/var/page_cache` esté vacío:

1. Inicie sesión en el servidor de Commerce o cambie a propietario del sistema de archivos.
1. Introduzca el siguiente comando:

   ```shell
   rm -rf <magento_root>/var/page_cache/*
   ```

1. Acceda a una o más páginas de Commerce almacenables en caché.
1. Compruebe el directorio `var/page_cache/`.

   Si el directorio está vacío, ¡enhorabuena! ¡Ha configurado correctamente Varnish y Commerce para que trabajen juntos!

1. Si borró el directorio `var/page_cache/`, reinicie Varnish.

>[!TIP]
>
>Si encuentra errores 503 (Error de recuperación de servidor), consulte [Solución de problemas 503 (Servicio no disponible) errores](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshooting-503-errors.html) en el _Centro de ayuda de Adobe Commerce_.
