---
title: Mostrar o cambiar el URI de administrador
description: Siga estos pasos para ver y modificar el URI de su aplicación de administración de Adobe Commerce.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%
---
# Mostrar o cambiar el URI de administrador

Antes de ejecutar este comando, debe [crear o actualizar la configuración de implementación](deployment.md).

## Mostrar el URI de administrador

En esta sección se explica cómo usar la línea de comandos para mostrar el identificador uniforme de recursos de administración ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

Opciones de comando:

```shell
bin/magento info:adminuri
```

A continuación se muestra un ejemplo:

```text
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
