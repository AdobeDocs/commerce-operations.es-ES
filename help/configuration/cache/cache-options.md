---
title: Opciones de caché
description: Configure el acceso al almacenamiento en caché de bajo nivel.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Opciones de caché de nivel bajo

La aplicación de Commerce utiliza un front-end y un back-end de caché de bajo nivel para proporcionar acceso al almacenamiento de caché.

## Caché de front-end de bajo nivel

Commerce amplía [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) implementando la caché de front-end [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php).

## Caché back-end de bajo nivel

En general, la aplicación Commerce funciona con cualquier caché back-end que [Zend_Cache admite Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html). Sin embargo, esta guía cubre solo las siguientes cachés de backend de bajo nivel:

- [Redis](config-redis.md)
- [Base de datos](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Sistema de archivos (predeterminado): no es necesaria ninguna configuración para utilizar el almacenamiento en caché del sistema de archivos.

[Varnish](config-varnish.md) no requiere la configuración de un backend de caché de nivel bajo.
