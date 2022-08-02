---
title: Referencia config.php
description: Consulte una lista de valores en el archivo config.php .
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# Referencia config.php

La variable `config.php` contiene las siguientes secciones:

| Nombre | Descripción |
| --------- | -------------------|
| `i18n` | Todos los datos de traducción en línea. No se admite la lectura desde esta sección. |
| `modules` | Lista de módulos habilitados y deshabilitados. |
| `scopes` | Lista de tiendas, grupos de tiendas y sitios web con información relacionada. |
| `system` | Las configuraciones del sistema necesarias para la implementación de contenido estático. |
| `themes` | La configuración de los temas instalados. |

## módulos

Contiene una matriz de módulos y sus estados. Si el módulo está habilitado, el valor es 1. De lo contrario, el valor es 0.

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

Más información sobre [Módulos].

## ámbitos

Contiene una matriz de valores de configuración de ámbito. Tiene los siguientes subnodos:

| Nombre | Descripción |
| ---------- | -----------------------------------|
| `websites` | Configuración del sitio web |
| `groups` | Almacena la configuración |
| `stores` | Configuración de vistas de almacén |

```conf
'scopes' => [
  'websites' => [
    'admin' => [
      'website_id' => '0',
      'code' => 'admin',
      'name' => 'Admin',
      'sort_order' => '0',
      'default_group_id' => '0',
      'is_default' => '0'
    ]
  ],
  'groups' => [
    0 => [
      'group_id' => '0',
      'website_id' => '0',
      'code' => 'default',
      'name' => 'Default',
      'root_category_id' => '0',
      'default_store_id' => '0'
    ]
  ],
  'stores' => [
    'admin' => [
      'store_id' => '0',
      'code' => 'admin',
      'website_id' => '0',
      'group_id' => '0',
      'name' => 'Admin',
      'sort_order' => '0',
      'is_active' => '1'
    ]
  ]
]
```

Más información sobre [Ámbitos comerciales][scopes].

## sistema

Contiene una matriz de valores de configuración de campos del sistema.

```conf
'system'=> [
    'default' =>[
        'checkout' => [
            'cart' => [
                'delete_quote_after' => 31
            ]
        ]
    ]
]
```

Más información sobre [Configuraciones específicas del sistema](config-reference-sens.md).

## temáticas

Contiene una matriz de valores para la configuración del tema.

```conf
'themes' => [
  'frontend/Magento/luma' => [
    'parent_id' => 'Magento/blank',
    'theme_path' => 'Magento/luma',
    'theme_title' => 'Magento Luma',
    'is_featured' => '0',
    'area' => 'frontend',
    'type' => '0',
    'code' => 'Magento/luma'
  ]
]
```

Más información sobre [Temas].

<!-- link definitions -->

[Módulos]: https://devdocs.magento.com/videos/fundamentals/create-a-new-module/
[scopes]: https://docs.magento.com/user-guide/configuration/scope.html
[Temas]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/theme-create.html
