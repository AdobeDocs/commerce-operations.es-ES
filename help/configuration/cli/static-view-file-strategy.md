---
title: Estrategias de implementación para archivos de vista estática
description: Obtenga información sobre las estrategias de implementación para la aplicación Commerce.
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# Estrategias de implementación para archivos de vista estática

Al implementar archivos de vista estática, puede elegir una de las tres estrategias disponibles. Cada uno de ellos proporciona resultados de implementación óptimos para diferentes casos de uso:

- [Standard](#standard-strategy): el proceso de implementación normal.
- [Rápido](#quick-strategy) (_predeterminado_): minimiza el tiempo necesario para la implementación cuando se implementan archivos para más de una configuración regional.
- [Compacto](#compact-strategy): minimiza el espacio que ocupan los archivos de vista publicados.

En las secciones siguientes se describen los detalles y las características de implementación de cada estrategia.

## Estrategia estándar

Cuando se utiliza la estrategia estándar, se implementan todos los archivos de vista estática de todos los paquetes, es decir, los procesa [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

Para obtener más información, consulte [Implementación de archivos de vista estática](../cli/static-view-file-deployment.md).

## Estrategia rápida

La estrategia rápida realiza las siguientes acciones:

1. Para cada tema, se elige una configuración regional arbitraria y se implementan todos los archivos para esta configuración regional, como en la estrategia estándar.
1. Para todas las demás configuraciones regionales de la temática:

   1. Los archivos que anulan la configuración regional implementada se definen e implementan.
   1. Todos los demás archivos se consideran similares para todas las configuraciones regionales y se copian de la configuración regional implementada.

>[!INFO]
>
>Por _parecido_, es decir, archivos que son independientes de la configuración regional, el tema o el área. Estos archivos pueden incluir CSS, imágenes y fuentes.

Este método minimiza el tiempo de implementación necesario para varias configuraciones regionales, aunque se dupliquen muchos archivos.

## Estrategia compacta

La estrategia compacta evita la duplicación de archivos al almacenar archivos similares en `base` subdirectorios.

Para el resultado más optimizado, se asignan tres ámbitos para una posible similitud: área, tema y configuración regional. El `base` los subdirectorios se crean para todas las combinaciones de estos ámbitos.

Los archivos se implementan en estos subdirectorios según los siguientes patrones.

| Patrón | Descripción |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | Archivos específicos de un área, tema y configuración regional determinados |
| `<area>/<theme>/default` | Archivos similares para todas las configuraciones regionales de un tema en particular de un área en particular. |
| `<area>/Magento/base/<locale>` | Archivos específicos de un área y configuración regional determinada, pero similares para todas las temáticas. |
| `<area>/Magento/base/default` | Archivos específicos de un área en particular, pero similares para todas las temáticas y configuraciones regionales. |
| `base/Magento/base/<locale>` | Archivos similares para todas las áreas y temáticas, pero específicos de una configuración regional en particular. |
| `base/Magento/base/default` | Similar para todas las áreas, temáticas y configuraciones regionales. |

### Asignación de archivos implementados

El método de implementación utilizado en la estrategia compacta significa que los archivos se heredan de los temas base y las configuraciones regionales. Estas relaciones de herencia se almacenan en los archivos de asignación para cada combinación de área, tema y configuración regional. Hay archivos de mapa independientes para PHP y JS:

- `map.php`
- `requirejs-map.js`

El `map.php` lo utiliza el archivo [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) para crear direcciones URL correctas.

El `requirejs-map.js` es utilizado por `baseUrlResolver` para RequireJS.

Ejemplo de `map.php`:

```php?start_inline=1
return [
    'Magento_Checkout::cvv.png' => [
        'area' => 'frontend',
        'theme' => 'Magento/luma',
        'locale' => 'en_US',
    ],
    '...' => [
        'area' => '...',
        'theme' => '...',
        'locale' => '...'
    ]
];
```

Ejemplo de `requirejs-map.js`:

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## Sugerencias para desarrolladores de extensiones

Para crear direcciones URL para archivos de vista estática, utilice [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

No utilice concatenaciones de URL para evitar problemas con los archivos estáticos que no se encuentran y no se muestran durante la representación de la página.
