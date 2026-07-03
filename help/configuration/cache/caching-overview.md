---
title: Información general de almacenamiento en caché y opciones de configuración
description: Obtenga información acerca del almacenamiento en caché en Adobe Commerce, incluido el almacenamiento back-end, la configuración de front-end y el almacenamiento en caché de página completa con Varnish, Redis, Valkey y caché L2.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 7171e5abfad69ad0f2d3f4c4b5eb57c13d07feb4
workflow-type: tm+mt
source-wordcount: 593
ht-degree: 0%

---

# Información general de almacenamiento en caché y opciones de configuración

Adobe Commerce se basa en una arquitectura de almacenamiento en caché de varios niveles para reducir la carga de la base de datos, minimizar el procesamiento redundante y acelerar la entrega de páginas. A nivel de aplicación, Commerce mantiene más de una docena de [tipos de caché](../cli/manage-cache.md#clean-and-flush-cache-types), como configuración, diseño, HTML de bloques y colecciones, cada uno de los cuales se puede enrutar a un servidor de almacenamiento dedicado como [Redis](config-redis.md) o [Valkey](config-valkey.md). Para el almacenamiento en caché de página completa en implementaciones locales, Adobe recomienda [Varnish](config-varnish.md). Las implementaciones de Commerce en la nube utilizan Fastly. Capas adicionales como [almacenamiento en caché L2](level-two-cache.md) y [firma de contenido estático](static-content-signing.md) mejoran aún más el rendimiento para implementaciones de varios nodos y de alto tráfico.

Esta guía explica cómo funciona cada capa de almacenamiento en caché y muestra cómo configurar front-end, backends y opciones avanzadas para que coincidan con los requisitos de implementación.

## Almacenar en caché frontend

Un front-end de caché es una interfaz entre Commerce y el back-end de almacenamiento de caché. Puede definir varios front-end, cada uno con una configuración de back-end diferente, y luego asignar [tipos de caché](../cli/manage-cache.md#clean-and-flush-cache-types) específicos a cada front-end. Para obtener detalles de configuración, consulte [Configurar tipos y front-end de caché](cache-types.md).

## Almacenar en caché backends

Un back-end de caché es el mecanismo de almacenamiento subyacente para los datos en caché. Commerce proporciona un back-end del sistema de archivos predeterminado, pero puede configurar otros back-end, como Redis o Valkey, para mejorar el rendimiento y la escalabilidad. Para obtener más información sobre las opciones disponibles, consulte [Opciones del servidor de caché](cache-options.md).

## Almacenamiento en caché de página completa con Barniz

[Varnish Cache](config-varnish.md) es un acelerador HTTP que almacena en caché páginas completas en la memoria. Para entornos de producción locales, Adobe recomienda encarecidamente Varnish, ya que es considerablemente más rápido que la caché integrada de página completa. Commerce en entornos de nube usa [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) para el almacenamiento en caché de página completa en lugar de Varnish.

>[!NOTE]
>
>El barniz funciona como un proxy inverso delante del servidor web y no requiere cambios en la configuración del back-end de la caché de Commerce.

## Almacenamiento en caché L2 (dos niveles)

[Caché L2](level-two-cache.md) almacena los datos de caché localmente en cada nodo web mientras usa una caché remota (Redis o Valkey) como origen de la verdad. Esto reduce el tráfico de red entre los nodos web y la caché remota, lo que mejora el rendimiento de los sitios con mucho tráfico.

## Almacenamiento en caché de contenido estático

[La firma de contenido estático](static-content-signing.md) invalida la memoria caché del explorador para los recursos estáticos (CSS, JavaScript, imágenes) al incrustar una versión de implementación en las direcciones URL de los archivos.

## Terminología del almacenamiento en caché

[!DNL Commerce] utiliza la siguiente terminología de almacenamiento en caché:

- **Frontend**: una interfaz o puerta de enlace para el almacenamiento en caché, implementada por [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Tipos de caché**: uno de los tipos integrados proporcionados con [!DNL Commerce] (como `config`, `layout`, `block_html`, `full_page`) o un [tipo personalizado](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Servidor**: especifica los detalles de [almacenamiento en caché](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implementado por [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend).
- **Servidor de dos niveles**: almacena registros de caché en dos servidores: una caché local (rápida) y una caché remota (compartida). Consulte [Configuración de caché L2](level-two-cache.md).

## Opciones de configuración

Para la asignación de front-end-to-type y la sintaxis de configuración de caché:

**Local**: la configuración de la caché se almacena en dos archivos:

- `<magento_root>/app/etc/di.xml`: la configuración de inyección de dependencia global. Modifique este archivo para cambiar el front-end de caché `default` proporcionado.
- `<magento_root>/app/etc/env.php`: configuración específica del entorno. Modifique este archivo para configurar los front-end de caché personalizados. Este archivo anula la configuración equivalente de `di.xml`.

Para obtener más información, consulte:

- [Configurar tipos y front-end de caché](cache-types.md): asocie un front-end de caché con tipos de caché específicos
- [Opciones de servidor de caché](cache-options.md): referencia de opción de servidor

**Adobe Commerce en la nube**: configure el almacenamiento en caché con `CACHE_CONFIGURATION` en `.magento.env.yaml`. Consulte [Prácticas recomendadas para la configuración de los servicios Redis y Valkey](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md).
