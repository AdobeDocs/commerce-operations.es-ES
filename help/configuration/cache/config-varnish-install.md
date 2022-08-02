---
title: Instalar Varniz
description: Consulte los consejos sobre la instalación de Varnish.
source-git-commit: 688db9fcc9cd196d1560e49719b03ef32d13870d
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Instalar Varniz

La instalación del software Varnish está fuera del alcance de esta guía. Para obtener más información sobre la instalación de Varnish, consulte:

- [wiki de instalación](http://wiki.mikejung.biz/Varnish)
- [Guías de instalación de barniz](https://www.varnish-cache.org/docs)
- [Instalación de Varnish (Tecmint)](http://www.tecmint.com/install-varnish-cache-web-accelerator)

>[!INFO]
>
>Este tema está escrito para Varnish en CentOS y Apache 2.4. Si está configurando Varnish en un entorno diferente, es probable que algunos comandos sean diferentes. Consulte la documentación anterior para obtener más información.
>
>Si tiene intención de instalar módulos (vmods) de Varnish, como el modo saint, debe instalar Varnish compilando el código, en lugar de instalar desde un paquete. Consulte [Modo Saint](config-varnish-advanced.md#saint-mode) para obtener más información.

## Confirmar la versión de Varnish

Abra un terminal e introduzca el siguiente comando para mostrar la versión de Varnish:

```bash
varnishd -V
```

A continuación se muestra una muestra:

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

Asegúrese de que la versión sea 6.x antes de continuar. Si está ejecutando una versión inferior a 6.x, debe actualizar a una versión compatible. Consulte la documentación de instalación de Varnish para obtener más información.
