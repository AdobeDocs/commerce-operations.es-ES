---
title: Prácticas recomendadas de cambio de tamaño de imagen de catálogo
description: Obtenga información sobre cómo evitar la degradación del rendimiento antes del lanzamiento de producción del sitio de Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 94d37b6a95cae93f465daf8eb96363a198833e27
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---


# Prácticas recomendadas de cambio de tamaño de imagen de catálogo

Se debe cambiar el tamaño de todas las imágenes del catálogo antes de que una tienda entre en producción. Al no cambiar el tamaño de las imágenes antes de la producción, se fuerza el cambio de tamaño de la imagen durante la carga de la página, lo que reduce significativamente la velocidad del sitio y aumenta la carga del servidor en los primeros días o semanas después del lanzamiento.

## La forma lenta

Utilice el comando CLI predeterminado para cambiar el tamaño de todas las imágenes:

```bash
bin/magento catalog:images:resize
```

Las desventajas de este enfoque incluyen:

- El proceso es de un solo hilo
- El proceso cambia el tamaño de las imágenes a las que ya se ha cambiado el tamaño
- El proceso no se puede interrumpir, lo que puede llevar días

## La(s) forma(s) rápida(s)

El cambio de tamaño de imagen asincrónico se introdujo en Adobe Commerce 2.4 y puede cambiar el tamaño de las imágenes más rápido.

1. En cada servidor web, inicie algunos controladores de cola adicionales temporalmente (el doble del número de procesadores físicos por servidor):

   ```bsh
   for i in {1.."$((2 * `nproc --all`))"};do bin/magento queue:consumers:start media.storage.catalog.image.resize &;done;
   ```

1. Compruebe que los controladores de cola se están ejecutando:

   ```bash
   pgrep -fl media.storage.catalog.image.resize
   ```

1. Rellene la cola con todas las solicitudes de cambio de tamaño de imagen:

   ```bash
   bin/magento catalog:images:resize --async
   ```

1. Una vez cambiado el tamaño de todas las imágenes, finalice el proceso:

   ```bash
   pkill -f media.storage.catalog.image.resize
   ```

## La vía rápida

Hay otra forma de cambiar el tamaño de las imágenes mediante el front-end.

Las ventajas de este enfoque incluyen:

- El proceso es multiproceso
- El proceso es de varios servidores (si tiene varios nodos web, un equilibrador de carga y espacio en disco compartido para `media/` directory)
- El proceso omite las imágenes cuyo tamaño ya se ha cambiado

Este enfoque cambia el tamaño de 100 000 imágenes en menos de 8 horas, mientras que el comando CLI tarda 6 días en completarse.

1. Inicie sesión en el servidor de.
1. Vaya a `pub/media/catalog/product` y anote uno de los hash (por ejemplo, 0047d83143a5a3a4683afdf1116df680).
1. En los ejemplos siguientes, reemplace `www.example.com` con el dominio de su tienda y reemplace el hash por el que anotó.

>[!BEGINTABS]

>[!TAB sed]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB sitiar]

La desventaja de `siege` Esto significa que visita todas las direcciones URL del servidor 10 veces si la concurrencia se establece en 10.

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB rizar]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

El `-P` determina el número de subprocesos.

>[!TAB bash one-liner]

La línea de una para la `find/curl` Por ejemplo, en caso de que pueda ejecutar `curl` desde el mismo equipo en el que se encuentran las imágenes:

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

De nuevo, reemplace `www.example.com` con el dominio y el conjunto del sitio web `-P` al número de subprocesos que el servidor puede gestionar sin que se bloqueen.

>[!ENDTABS]

La salida devuelve una lista de todas las imágenes de producto de la tienda. Puede rastrear las imágenes (con `siege` o cualquier otro rastreador) utilizando todos los servidores y núcleos de procesador disponibles para usted y genere la caché de cambio de tamaño a una velocidad significativamente mayor que otros enfoques.

Al visitar una URL de caché de imagen, se generan todos los tamaños de imagen en segundo plano, si aún no existen. Además, omite los archivos que ya han cambiado de tamaño.

>[!NOTE]
>
>- Adobe Commerce en proyectos de infraestructura en la nube puede descargar el cambio de tamaño de la imagen del producto en el servicio Fastly. Consulte [Optimización de imagen profunda](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=en#deep-image-optimization) en el _Guía de Cloud_.
>- Si utiliza el módulo de almacenamiento remoto, también puede intentar descargar el cambio de tamaño de la imagen a nginx. Consulte [Configurar el cambio de tamaño de la imagen para almacenamiento remoto](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html) en el _Guía de configuración_.
