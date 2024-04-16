---
title: Instalar barniz
description: Consulte los consejos sobre la instalación de Barnish.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Instalar barniz

La instalación del software Varnish no entra dentro del ámbito de esta guía. Para obtener más información sobre la instalación de Barniz, consulte:

- [guía de instalación](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Guías de instalación de barniz](https://www.varnish-cache.org/docs)
- [Cómo instalar Varnish (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Este tema está escrito para Varnish en CentOS y Apache 2.4. Si está configurando Barnish en un entorno diferente, es probable que algunos comandos sean diferentes. Consulte la documentación anterior para obtener más información.
>
>Si tiene intención de instalar módulos Varnish (vmods), como el modo Saint, debe instalar Varnish compilando el código, en lugar de instalar desde un paquete. Consulte [Modo Saint](config-varnish-advanced.md#saint-mode) para obtener más información.

## Confirma tu versión de Barniz

Abra un terminal e introduzca el siguiente comando para mostrar la versión de Barniz:

```bash
varnishd -V
```

Asegúrese de que [Adobe Commerce admite](../../installation/system-requirements.md) Seleccione la versión instalada de Varnish antes de continuar. Si está ejecutando una versión no compatible, debe actualizar a una versión compatible. Consulte la documentación de instalación de Varnish para obtener más información.
