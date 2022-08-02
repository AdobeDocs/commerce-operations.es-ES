---
title: Configurar el almacenamiento en caché
description: Obtenga información sobre el almacenamiento en caché y cómo configurar los mecanismos de caché para la aplicación Adobe Commerce y Magento Open Source.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Configurar el almacenamiento en caché

[!DNL Commerce] permite configurar alternativas al almacenamiento en caché predeterminado del sistema de archivos. En la presente guía se examinan algunas de esas alternativas; es decir,

- Configure lo siguiente [cache](https://glossary.magento.com/cache) en el [!DNL Commerce] configuración:

   - [Base de datos](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Sistema de archivos (predeterminado): No es necesaria ninguna configuración para utilizar el almacenamiento en caché predeterminado del sistema de archivos.

- Configure el [Varniz](config-varnish.md) sin modificar el [!DNL Commerce] configuración.

## Terminología de almacenamiento en caché

[!DNL Commerce] utiliza la siguiente terminología de almacenamiento en caché:

- **Frontera**: similar a una interfaz o gateway para el almacenamiento de caché, implementada por [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Tipos de caché**: puede ser uno de los tipos proporcionados con [!DNL Commerce] o puede [cree su propio](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Back-end**—Especifica detalles sobre [almacenamiento en caché](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implementado por [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Servidor back-end de dos niveles**: almacena registros de caché en dos backends: uno más rápido y uno más lento.

   >[!INFO]
   >
   >La configuración de caché de back-end de dos niveles está fuera del alcance de esta guía.

## Opciones de configuración

- Modificación de los datos proporcionados `default` front-end de caché—

   Solo puede modificar el `<magento_root>/app/etc/di.xml` , el archivo global de la aplicación Commerce [inyección de dependencia](https://glossary.magento.com/dependency-injection) configuración.

- Configuración de su propio front-end de caché personalizado:

   Solo puede modificar el `<magento_root>/app/etc/env.php` porque anula la configuración equivalente en la `di.xml` archivo.

>[!TIP]
>
>El barniz no requiere cambios en la variable [!DNL Commerce] configuración. Consulte [Configuración y uso de Varnish](config-varnish.md).
