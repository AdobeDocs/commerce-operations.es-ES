---
title: Mostrar o cambiar el URI de administrador
description: Siga estos pasos para ver y modificar el URI de su aplicación de administración de Adobe Commerce.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Mostrar o cambiar el URI de administrador

Antes de ejecutar este comando, debe [crear o actualizar la configuración de implementación](deployment.md).

## Mostrar el URI de administrador

En esta sección se explica cómo usar la línea de comandos para mostrar el identificador uniforme de recursos de administración ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

Opciones de comando:

```bash
bin/magento info:adminuri
```

A continuación se muestra un ejemplo:

```
Admin Panel URI: /admin_1wgrah
```

También puede ver el URI de administrador en `<magento_root>/app/etc/env.php`. A continuación se muestra un fragmento:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Cambio de la URL de administración

Para cambiar el URI de administrador, use el comando [`magento setup:config:set`](deployment.md).
