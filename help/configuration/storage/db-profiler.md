---
title: Configurar el perfilador de la base de datos
description: Consulte un ejemplo de cómo configurar la salida para el perfilador de la base de datos.
contributor_name: Atish Goswami
contributor_link: http://atishgoswami.com
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# Configurar el perfilador de la base de datos

El perfilador de base de datos de comercio muestra todas las consultas implementadas en una página, incluido el tiempo para cada consulta y los parámetros que se aplicaron.

## Paso 1: Modificación de la configuración de implementación

Modificar `<magento_root>/app/etc/env.php` para añadir la siguiente referencia al [clase profiler de base de datos](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

A continuación se muestra un ejemplo:

```php?start_inline=1
 'db' =>
  array (
    'table_prefix' => '',
    'connection' =>
    array (
      'default' =>
      array (
        'host' => 'localhost',
        'dbname' => 'magento',
        'username' => 'magento',
        'password' => 'magento',
        'model' => 'mysql4',
        'engine' => 'innodb',
        'initStatements' => 'SET NAMES utf8;',
        'active' => '1',
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
      ),
    ),
  ),
```

## Paso 2: Configuración de la salida

Configure el resultado en el archivo de arranque de la aplicación Commerce; puede ser `<magento_root>/pub/index.php` o puede estar ubicado en una configuración de host virtual de servidor web.

El siguiente ejemplo muestra los resultados en una tabla de tres columnas:

- Tiempo total (muestra la cantidad total de tiempo para ejecutar todas las consultas en la página)
- SQL (muestra todas las consultas SQL; el encabezado de fila muestra el recuento de consultas)
- Parámetros de consulta (muestra los parámetros de cada consulta SQL)

Para configurar la salida, agregue lo siguiente después de la variable `$bootstrap->run($app);` en su archivo de arranque:

```php?start_inline=1
/** @var \Magento\Framework\App\ResourceConnection $res */
$res = \Magento\Framework\App\ObjectManager::getInstance()->get('Magento\Framework\App\ResourceConnection');
/** @var Magento\Framework\DB\Profiler $profiler */
$profiler = $res->getConnection('read')->getProfiler();
echo "<table cellpadding='0' cellspacing='0' border='1'>";
echo "<tr>";
echo "<th>Time <br/>[Total Time: ".$profiler->getTotalElapsedSecs()." secs]</th>";
echo "<th>SQL [Total: ".$profiler->getTotalNumQueries()." queries]</th>";
echo "<th>Query Params</th>";
echo "</tr>";
foreach ($profiler->getQueryProfiles() as $query) {
    /** @var Zend_Db_Profiler_Query $query*/
    echo '<tr>';
    echo '<td>', number_format(1000 * $query->getElapsedSecs(), 2), 'ms', '</td>';
    echo '<td>', $query->getQuery(), '</td>';
    echo '<td>', json_encode($query->getQueryParams()), '</td>';
    echo '</tr>';
}
echo "</table>";
```

## Paso 3: Ver los resultados

Vaya a cualquier página de su tienda o administrador para ver los resultados. A continuación se muestra una muestra:

![Resultados de perfil de base de datos de muestra](../../assets/configuration/db-profiler-results.png)
