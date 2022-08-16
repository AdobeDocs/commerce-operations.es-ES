---
title: Opciones de caché
description: Configure el acceso al almacenamiento de caché de bajo nivel.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---

# Opciones de caché de bajo nivel

La aplicación Commerce utiliza un nivel bajo [cache](https://glossary.magento.com/cache) [front-end](https://glossary.magento.com/frontend) y [backend](https://glossary.magento.com/backend) para proporcionar acceso al almacenamiento de caché.

## Caché de front-end de bajo nivel

Extensiones comerciales [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) implementando [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) caché de front-end.

## Caché back-end de bajo nivel

En general, la aplicación Commerce funciona con cualquier caché backend que [Backends Zend_Cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) admite . Sin embargo, esta guía solo cubre las siguientes cachés back-end de bajo nivel:

- [Redis](config-redis.md)
- [Base de datos](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Sistema de archivos (predeterminado): No es necesaria ninguna configuración para utilizar el almacenamiento en caché del sistema de archivos.

[Varniz](config-varnish.md) no requiere la configuración de un back-end de caché de bajo nivel.