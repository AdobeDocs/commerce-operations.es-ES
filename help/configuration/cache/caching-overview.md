---
title: Configurar almacenamiento en caché
description: Obtenga información sobre el almacenamiento en caché y cómo configurarlo para la aplicación de Adobe Commerce y de Magento Open Source.
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Configurar almacenamiento en caché

[!DNL Commerce] permite configurar alternativas al almacenamiento en caché predeterminado del sistema de archivos. En esta guía se analizan algunas de estas alternativas, a saber:

- Configure los siguientes mecanismos de caché en la [!DNL Commerce] configuración:

   - [Base de datos](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Sistema de archivos (predeterminado): no es necesaria ninguna configuración para utilizar el almacenamiento en caché predeterminado del sistema de archivos.

- Configure las variables [Barniz](config-varnish.md) sin modificar el [!DNL Commerce] configuración.

## Terminología del almacenamiento en caché

[!DNL Commerce] utiliza la siguiente terminología de almacenamiento en caché:

- **Front-end**: similar a una interfaz o puerta de enlace para el almacenamiento en caché, implementada por [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Tipos de caché**: puede ser uno de los tipos proporcionados con [!DNL Commerce] o puede [cree los suyos propios](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Servidor**: permite especificar detalles acerca de [almacenamiento en caché](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implementado por [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Servidor de dos niveles**: permite almacenar los registros de caché en dos backends: uno más rápido y uno más lento.

   >[!INFO]
   >
   >La configuración de caché back-end de dos niveles está fuera del ámbito de esta guía.

## Opciones de configuración

- Modificación del proporcionado `default` front-end de caché—

   Solo se modifica la variable `<magento_root>/app/etc/di.xml` , la configuración de inyección de dependencia global de la aplicación Commerce.

- Configurar su propio front-end de caché personalizado:

   Solo se modifica la variable `<magento_root>/app/etc/env.php` porque anula la configuración equivalente en el archivo `di.xml` archivo.

>[!TIP]
>
>El barniz no requiere cambios en el [!DNL Commerce] configuración. Consulte [Configuración y uso de Barniz](config-varnish.md).
