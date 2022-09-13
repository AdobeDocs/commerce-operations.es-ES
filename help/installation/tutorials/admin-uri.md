---
title: Mostrar o cambiar el URI de administración
description: Siga estos pasos para ver y modificar el URI de la aplicación de administración de Adobe Commerce o Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Mostrar o cambiar el URI de administración

Antes de ejecutar este comando, debe [Crear o actualizar la configuración de implementación](deployment.md).

## Mostrar el URI de administración

En esta sección se explica cómo utilizar la línea de comandos para mostrar la variable [Administrador](https://glossary.magento.com/admin) Identificador uniforme de recurso ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

Opciones de comando:

```bash
bin/magento info:adminuri
```

A continuación se muestra un resultado de muestra:

```terminal
Admin Panel URI: /admin_1wgrah
```

También puede ver el URI de administración en `<magento_root>/app/etc/env.php`. A continuación se muestra un fragmento de código:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Cambiar la dirección URL de administración

Para cambiar el URI de administración, utilice la variable [`magento setup:config:set`](deployment.md) comando.
