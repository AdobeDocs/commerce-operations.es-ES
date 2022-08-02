---
title: Estrategias de implementación para archivos de vista estáticos
description: Obtenga más información sobre las estrategias de implementación para la aplicación Commerce.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# Estrategias de implementación para archivos de vista estáticos

Al implementar archivos de vista estáticos, puede elegir una de las tres estrategias disponibles. Cada uno de ellos proporciona resultados de implementación óptimos para diferentes casos de uso:

- [Estándar](#standard-strategy): el proceso de implementación regular.
- [Rápido](#quick-strategy) (_default_): minimiza el tiempo necesario para la implementación cuando se implementan archivos para más de una configuración regional.
- [Compacta](#compact-strategy): minimiza el espacio que ocupan los archivos de vista publicados.

En las secciones siguientes se describen los detalles y las características de la implementación de cada estrategia.

## Estrategia estándar

Cuando se utiliza la estrategia estándar, se implementan todos los archivos de vista estáticos de todos los paquetes, es decir, se procesan mediante [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

Para obtener más información, consulte [Implementación de archivos de vista estáticos](../cli/static-view-file-deployment.md).

## Estrategia rápida

La estrategia rápida realiza las siguientes acciones:

1. Para cada tema, se elige una configuración regional arbitraria y se implementan todos los archivos de esta configuración regional, como en la estrategia estándar.
1. Para todas las demás configuraciones regionales del tema:

   1. Los archivos que anulan la configuración regional implementada se definen y se implementan.
   1. Todos los demás archivos se consideran similares para todas las configuraciones regionales y se copian de la configuración regional implementada.

>[!INFO]
>
>Por _similar_, nos referimos a archivos que son independientes de la configuración regional, tema o área. Estos archivos pueden incluir CSS, imágenes y fuentes.

Este método minimiza el tiempo de implementación necesario para varias configuraciones regionales, aunque muchos archivos están duplicados.

## Estrategia compacta

La estrategia compacta evita la duplicación de archivos al almacenar archivos similares en `base` subdirectorios.

Para el resultado más optimizado, se asignan tres ámbitos para posible similitud: área, tema y configuración regional. La variable `base` los subdirectorios se crean para todas las combinaciones de estos ámbitos.

Los archivos se implementan en estos subdirectorios según los patrones siguientes.

| Patrón | Descripción |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | Archivos específicos de un área, tema y configuración regional en particular |
| `<area>/<theme>/default` | Archivos similares para todas las configuraciones regionales de un tema concreto de un área en particular. |
| `<area>/Magento/base/<locale>` | Archivos específicos de un área y configuración regional en particular, pero similares para todos los temas. |
| `<area>/Magento/base/default` | Archivos específicos de un área en particular, pero similares para todos los temas y configuraciones regionales. |
| `base/Magento/base/<locale>` | Archivos similares para todas las áreas y temas, pero específicos de una configuración regional concreta. |
| `base/Magento/base/default` | Es similar para todas las áreas, temas y configuraciones regionales. |

### Asignación de archivos implementados

El método de implementación utilizado en la estrategia compacta significa que los archivos se heredan de los temas base y las configuraciones regionales. Estas relaciones de herencia se almacenan en los archivos de asignación para cada combinación de área, tema y configuración regional. Existen archivos de mapa independientes para PHP y JS:

- `map.php`
- `requirejs-map.js`

La variable `map.php` el archivo es utilizado por [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) para crear direcciones URL correctas.

La variable `requirejs-map.js` la usa el `baseUrlResolver` complemento para RequireJS.

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

Para crear direcciones URL para archivos de vista estáticos, utilice [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

No utilice concatenaciones de URL para evitar problemas con archivos estáticos que no se encuentran ni se muestran durante el procesamiento de la página.
