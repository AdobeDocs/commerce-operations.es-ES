---
title: Importar datos de archivos de configuración
description: Importe los ajustes de configuración de Adobe Commerce desde los archivos de configuración.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---


# Importar ajustes de configuración

{{file-system-owner}}

Al configurar un sistema de producción mediante Commerce 2.2 [modelo de implementación de canalización](../deployment/technical-details.md), debe _importar_ configuración de `config.php` y `env.php` en la base de datos.
Estos ajustes incluyen rutas y valores de configuración, sitios web, tiendas, vistas de tiendas y temas.

Después de importar sitios web, tiendas, vistas de tiendas y temas, puede crear atributos de producto y aplicarlos a sitios web, tiendas y vistas de tiendas, en el sistema de producción.

>[!INFO]
>
>La variable `bin/magento app:config:import` no procesa la configuración almacenada en variables de entorno.

## Importar, comando

En el sistema de producción, ejecute el siguiente comando para importar datos de los archivos de configuración (`config.php` y `env.php`) a la base de datos:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Utilice el `[-n, --no-interaction]` indicador para importar datos sin ninguna interacción.

Si introduce `bin/magento app:config:import` sin el indicador opcional , debe confirmar los cambios.

Por ejemplo, si el archivo de configuración contiene un nuevo sitio web y un nuevo almacén, se muestra el siguiente mensaje:

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Para continuar con la importación, introduzca `yes`.

Si los archivos de configuración de implementación contienen algunos datos para importar, se muestra un mensaje similar al siguiente:

```terminal
Start import:
Some information about importing
```

Si los archivos de configuración de implementación no contienen datos para importar, se muestra un mensaje similar al siguiente:

```terminal
Start import:
Nothing to import
```

## Qué se importa

Las siguientes secciones analizan en detalle qué datos importamos.

### Configuración del sistema

El comercio utiliza directamente los valores en la variable `system` en el `config.php` o `env.php` en lugar de importarlos a la base de datos, ya que requieren algunas acciones previas y posteriores al procesamiento.

Por ejemplo, el valor de la ruta de configuración `web/secure/base_url` debe validarse con modelos backend.

#### Modelos back-end

Los modelos back-end son el mecanismo para procesar los cambios en la configuración del sistema.
Puede definir módulos de backend en `<module_name>/adminhtml/system.xml`.

Todos los modelos backend deben ampliar el [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) Clase .

Cuando importamos modelos backend, no guardamos los valores de configuración.

### Configuración de sitios web, tiendas y grupos de tiendas

Importamos los siguientes tipos de configuraciones.
(Estas configuraciones se encuentran en la sección `scopes` matriz en `config.php`.)

- `websites`: configuración relacionada con los sitios web
- `groups`: configuración relacionada con las tiendas
- `stores`: configuración relacionada con vistas de almacén

Las configuraciones anteriores se pueden importar en los siguientes modos:

- `create`: `config.php` contiene nuevas entidades (`websites`, `groups`, `stores`) que están ausentes en el entorno de producción
- `update`: `config.php` contiene entidades (`websites`, `groups`, `stores`) que son diferentes del entorno de producción
- `delete`: `config.php` does _not_ contiene entidades (`websites`, `groups`, `stores`) que están presentes en el entorno de producción

>[!INFO]
>
>No importamos la categoría raíz asociada a las tiendas. Debe asociar una categoría raíz con una tienda mediante el administrador de comercio.

### Configuración del tema

La configuración de temas incluye todos los temas registrados en su sistema de comercio; los datos proceden directamente de la variable `theme` tabla de base de datos. (La configuración del tema se encuentra en la `themes` matriz en `config.php`.)

#### Estructura de los datos del tema

La clave de la matriz es la ruta completa del tema: `area` + `theme path`

Por ejemplo, `frontend/Magento/luma`.
`frontend` es area y `Magento/luma` es la ruta del tema.

El valor de la matriz son los datos sobre el tema: código, título, ruta, id principal

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
>- _Registro de temas_. Si los datos de un tema están definidos en `config.php` pero el código fuente del tema no está presente en el sistema de archivos, el tema se ignora (es decir, no está registrado).
>- _Eliminación de tema_. Si un tema no está presente en `config.php` pero el código fuente está presente en el sistema de archivos, el tema no se elimina.

