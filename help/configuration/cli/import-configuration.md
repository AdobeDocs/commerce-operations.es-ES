---
title: Importación de datos de archivos de configuración
description: Importe las opciones de configuración de Adobe Commerce desde los archivos de configuración.
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Importar opciones de configuración

{{file-system-owner}}

Al configurar un sistema de producción con Commerce 2.2 [modelo de implementación de canalización](../deployment/technical-details.md), debe _importar_ opciones de configuración de `config.php` y `env.php` en la base de datos.
Estas opciones incluyen rutas y valores de configuración, sitios web, tiendas, vistas de tiendas y temas.

Después de importar sitios web, tiendas, vistas de tiendas y temas, puede crear atributos de producto y aplicarlos a sitios web, tiendas y vistas de tiendas en el sistema de producción.

>[!INFO]
>
>El `bin/magento app:config:import` El comando no procesa la configuración almacenada en variables de entorno.

## Importar, comando

En el sistema de producción, ejecute el siguiente comando para importar datos de los archivos de configuración (`config.php` y `env.php`) a la base de datos:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Utilice el opcional `[-n, --no-interaction]` para importar datos sin ninguna interacción.

Si introduce `bin/magento app:config:import` sin el indicador opcional, es necesario confirmar los cambios.

Por ejemplo, si el archivo de configuración contiene un nuevo sitio web y un nuevo almacén, se muestra el siguiente mensaje:

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Para continuar con la importación, escriba `yes`.

Si los archivos de configuración de implementación contienen datos para importar, aparece un mensaje similar al siguiente:

```terminal
Start import:
Some information about importing
```

Si los archivos de configuración de implementación no contienen datos para importar, aparece un mensaje similar al siguiente:

```terminal
Start import:
Nothing to import
```

## Qué importamos

Las siguientes secciones analizan en detalle qué datos importamos.

### Configuración del sistema

Commerce utiliza directamente los valores de `system` matriz en la `config.php` o `env.php` en lugar de importarlos a la base de datos porque requieren algunas acciones de preprocesamiento y posprocesamiento.

Por ejemplo, el valor de la ruta de configuración `web/secure/base_url` debe validarse con modelos backend.

#### Modelos back-end

Los modelos back-end son el mecanismo para procesar los cambios en la configuración del sistema.
Los módulos back-end se definen en `<module_name>/adminhtml/system.xml`.

Todos los modelos backend deben ampliar el [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) clase.

Al importar modelos back-end, no se guardan los valores de configuración.

### Configuración de sitios web, tiendas y grupos de tiendas

Importamos los siguientes tipos de configuraciones.
(Estas configuraciones se encuentran en la sección `scopes` matriz en `config.php`.)

- `websites`: configuración relacionada con sitios web
- `groups`: almacena la configuración relacionada
- `stores`: configuración relacionada con las vistas de tienda

Las configuraciones anteriores se pueden importar en los modos siguientes:

- `create`: `config.php` contiene nuevas entidades (`websites`, `groups`, `stores`) que están ausentes en el entorno de producción
- `update`: `config.php` contiene entidades (`websites`, `groups`, `stores`) que son diferentes del entorno de producción
- `delete`: `config.php` hace _no_ contener entidades (`websites`, `groups`, `stores`) presentes en el entorno de producción

>[!INFO]
>
>No importamos la categoría raíz asociada con las tiendas. Debe asociar una categoría raíz con una tienda mediante el administrador de comercio.

### Configuración del tema

La configuración de temáticas incluye todas las temáticas registradas en su sistema de comercio; los datos proceden directamente del `theme` tabla de base de datos. (La configuración de la temática se encuentra en la `themes` matriz en `config.php`.)

#### Estructura de los datos del tema

La clave de la matriz es la ruta completa del tema: `area` + `theme path`

Por ejemplo, `frontend/Magento/luma`.
`frontend` es área y `Magento/luma` es la ruta del tema.

El valor de la matriz son los datos sobre el tema: código, título, ruta, ID principal

Ejemplo completo:

```php?start_inline=1
'frontend/Magento/luma' =>
   array (
      'parent_id' => 'Magento/blank',
      'theme_path' => 'Magento/luma',
      'theme_title' => 'Magento Luma',
      'is_featured' => '0',
      'area' => 'frontend',
      'type' => '0',
      'code' => 'Magento/luma',
),
```

>[!INFO]
>
>- _Registro de temas_. Si los datos de una temática se definen en `config.php` pero el código fuente de la temática no está presente en el sistema de archivos, la temática se ignora (es decir, no se registra).
>- _Eliminación de temas_. Si una temática no está presente en `config.php` pero el código fuente está presente en el sistema de archivos, el tema no se elimina.
