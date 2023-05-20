---
title: Opciones de caché
description: Configure el acceso al almacenamiento en caché de bajo nivel.
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Opciones de caché de nivel bajo

La aplicación de Commerce utiliza un front-end y un back-end de caché de bajo nivel para proporcionar acceso al almacenamiento de caché.

## Caché de front-end de bajo nivel

Commerce amplía [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) mediante la implementación [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) caché de front-end.

## Caché back-end de bajo nivel

En general, la aplicación Commerce funciona con cualquier caché back-end que [Backends de Zend_Cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) admite. Sin embargo, esta guía cubre solo las siguientes cachés de backend de bajo nivel:

- [Redis](config-redis.md)
- [Base de datos](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Sistema de archivos (predeterminado): no es necesaria ninguna configuración para utilizar el almacenamiento en caché del sistema de archivos.

[Barniz](config-varnish.md) no requiere la configuración de un back-end de caché de nivel bajo.
