---
title: Importación de datos de archivos de configuración
description: Obtenga información sobre cómo importar los ajustes de configuración de Adobe Commerce desde archivos de configuración. Descubra los procesos de implementación de canalización e importación de base de datos.
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Importar opciones de configuración

{{file-system-owner}}

Cuando configura un sistema de producción con el [modelo de implementación de canalización](../deployment/technical-details.md) de Commerce 2.2, debe _importar_ las opciones de configuración de `config.php` y `env.php` en la base de datos.
Estas opciones incluyen rutas y valores de configuración, sitios web, tiendas, vistas de tiendas y temas.

Después de importar sitios web, tiendas, vistas de tiendas y temas, puede crear atributos de producto y aplicarlos a sitios web, tiendas y vistas de tiendas en el sistema de producción.

>[!INFO]
>
>El comando `bin/magento app:config:import` no procesa la configuración almacenada en variables de entorno.

## Importar, comando

En el sistema de producción, ejecute el siguiente comando para importar los datos de los archivos de configuración (`config.php` y `env.php`) a la base de datos:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Use el indicador `[-n, --no-interaction]` opcional para importar datos sin ninguna interacción.

Si escribe `bin/magento app:config:import` sin el marcador opcional, deberá confirmar los cambios.

Por ejemplo, si el archivo de configuración contiene un nuevo sitio web y un nuevo almacén, se muestra el siguiente mensaje:

```
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Para continuar la importación, ingrese `yes`.

Si los archivos de configuración de implementación contienen datos para importar, aparece un mensaje similar al siguiente:

```
Start import:
Some information about importing
```

Si los archivos de configuración de implementación no contienen datos para importar, aparece un mensaje similar al siguiente:

```
Start import:
Nothing to import
```

## Qué importamos

Las siguientes secciones analizan en detalle qué datos importamos.

### Configuración del sistema

Commerce utiliza directamente los valores de la matriz `system` en los archivos `config.php` o `env.php` en lugar de importarlos a la base de datos, ya que requieren algunas acciones de procesamiento previo y posterior.

Por ejemplo, el valor de la ruta de configuración `web/secure/base_url` debe validarse con modelos backend.

#### Modelos back-end

Los modelos back-end son el mecanismo para procesar los cambios en la configuración del sistema.
Usted define los módulos back-end en `<module_name>/adminhtml/system.xml`.

Todos los modelos backend deben extender la clase [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php).

Al importar modelos back-end, no se guardan los valores de configuración.

### Configuración de sitios web, tiendas y grupos de tiendas

Importamos los siguientes tipos de configuraciones.
(Estas configuraciones se encuentran en la matriz `scopes` de `config.php`).

- `websites`: configuración relacionada con sitios web
- `groups`: almacena la configuración relacionada
- `stores`: configuración relacionada con las vistas de tienda

Las configuraciones anteriores se pueden importar en los modos siguientes:

- `create`: `config.php` contiene nuevas entidades (`websites`, `groups`, `stores`) que están ausentes en el entorno de producción
- `update`: `config.php` contiene entidades (`websites`, `groups`, `stores`) diferentes del entorno de producción
- `delete`: `config.php` _no_ contiene entidades (`websites`, `groups`, `stores`) que están presentes en el entorno de producción

>[!INFO]
>
>No importamos la categoría raíz asociada con las tiendas. Debe asociar una categoría raíz a una tienda mediante el administrador de Commerce.

### Configuración del tema

La configuración de temáticas incluye todas las temáticas registradas en su sistema Commerce; los datos proceden directamente de la tabla de base de datos `theme`. (La configuración del tema se encuentra en la matriz `themes` de `config.php`.)

#### Estructura de los datos del tema

La clave de la matriz es la ruta de acceso completa del tema: `area` + `theme path`

Por ejemplo, `frontend/Magento/luma`.
`frontend` es el área y `Magento/luma` es la ruta del tema.

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
>- _Registro de tema_. Si los datos de un tema están definidos en `config.php` pero el código fuente del tema no está presente en el sistema de archivos, el tema se omite (es decir, no está registrado).
>- _Eliminación de tema_. Si un tema no está presente en `config.php` pero el código fuente está presente en el sistema de archivos, el tema no se quita.
