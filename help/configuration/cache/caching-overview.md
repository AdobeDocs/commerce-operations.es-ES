---
title: Configurar almacenamiento en caché
description: Obtenga información sobre los mecanismos de almacenamiento en caché y las opciones de configuración para aplicaciones de Adobe Commerce. Descubra alternativas al almacenamiento en caché predeterminado del sistema de archivos.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Configurar almacenamiento en caché

[!DNL Commerce] le permite configurar alternativas al almacenamiento en caché predeterminado del sistema de archivos. En esta guía se analizan algunas de estas alternativas, a saber:

- Configure los siguientes mecanismos de caché en la configuración de [!DNL Commerce]:

   - [Base de datos](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Sistema de archivos (predeterminado): no es necesaria ninguna configuración para utilizar el almacenamiento en caché predeterminado del sistema de archivos.

- Configure [Varnish](config-varnish.md) sin modificar la configuración de [!DNL Commerce].

## Terminología del almacenamiento en caché

[!DNL Commerce] utiliza la siguiente terminología de almacenamiento en caché:

- **Frontend**: similar a una interfaz o puerta de enlace para el almacenamiento en caché, implementada por [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Tipos de caché**: puede ser uno de los tipos proporcionados con [!DNL Commerce] o puede [crear los suyos propios](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Servidor**: especifica detalles sobre el [almacenamiento en caché](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implementado por [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Servidor de dos niveles**: almacena los registros de caché en dos servidores: uno más rápido y uno más lento.

  >[!INFO]
  >
  >La configuración de caché back-end de dos niveles está fuera del ámbito de esta guía.

## Opciones de configuración

- Modificando el front-end de caché de `default` proporcionado:

  Solo modifica el archivo `<magento_root>/app/etc/di.xml`, la configuración de inyección de dependencia global de la aplicación Commerce.

- Configurar su propio front-end de caché personalizado:

  Solo modifica el archivo `<magento_root>/app/etc/env.php` porque anula la configuración equivalente del archivo `di.xml`.

>[!TIP]
>
>El barniz no requiere cambios en la configuración de [!DNL Commerce]. Consulte [Configurar y utilizar Barniz](config-varnish.md).
