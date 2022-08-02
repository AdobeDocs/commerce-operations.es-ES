---
title: Habilitar la creación de perfiles
description: Obtenga más información sobre cómo habilitar el perfilador MAGE para utilizarlo con sus herramientas analíticas.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# Habilitar la creación de perfiles

Con la creación de perfiles de comercio, puede:

- Habilite un perfilador integrado.

   Puede utilizar un perfilador integrado con Commerce para realizar tareas como analizar el rendimiento. La naturaleza de la creación de perfiles depende de las herramientas analíticas que utilice. Admitimos varios formatos, incluido el HTML. Cuando habilite el perfilador, una `var/profiler.flag` genera el archivo indicando que el perfilador está habilitado y las configuraciones. Cuando está desactivado, este archivo se elimina.

- Mostrar gráficos de dependencias en una página de Comercio.

   A _gráfico de dependencias_ es una lista de dependencias de objeto y todas sus dependencias, así como todas las dependencias de esas dependencias, etc.

   Debería estar especialmente interesado en la lista de _dependencias no utilizadas_, que son objetos creados porque se solicitaron en algún constructor, pero nunca se utilizaron (es decir, no se llamó a ninguno de sus métodos). Como resultado, se pierden el tiempo y la memoria del procesador empleados para crear estas dependencias.

Commerce proporciona la funcionalidad básica en [`Magento\Framework\Profiler`][profiler].

Puede habilitar y configurar el perfilador mediante una variable MAGE_PROFILER o la línea de comandos.

## Establecer MAGE_PROFILER

Puede establecer el valor de `MAGE_PROFILER` de cualquiera de los modos mencionados en [Establezca el valor de los parámetros de arranque](../bootstrap/set-parameters.md).

`MAGE_PROFILER` admite los siguientes valores:

- `1` para habilitar la salida de un perfilador específico.

   Puede utilizar uno de los siguientes valores para habilitar un perfilador específico:

   - `csvfile` que utiliza [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - Cualquier otro valor (excepto `2`), incluido un valor vacío, que usa [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]

- `2` para habilitar los gráficos de dependencias.

   Los gráficos de dependencias normalmente se muestran en la parte inferior de una página. La siguiente figura muestra la parte de la salida:

   ![Gráficos de dependencias](../../assets/configuration/depend-graphs.png)

## Comandos CLI

Puede habilitar o deshabilitar el perfilador mediante comandos CLI:

- `dev:profiler:enable <type>` habilita el perfilador con `type` de `html` (predeterminado) o `csvfile`. Cuando está activado, un archivo de indicadores `var/profiler.flag` se crea.
- `dev:profiler:disable` deshabilita el perfilador. Cuando esté desactivado, el archivo de indicadores `var/profiler.flag` se elimina.

Para habilitar los gráficos de dependencia, utilice la opción de variable .

**Para habilitar o deshabilitar el perfilador**:

1. Inicie sesión en su servidor de comercio.
1. Cambie al directorio de instalación de Commerce.
1. Como propietario del sistema de archivos, habilite el perfilador:

   Para habilitar el perfilador mediante el tipo `html` y crear un archivo de indicadores:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   Para habilitar el perfilador mediante el tipo `csvfile` y crear un archivo de indicadores:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   La salida se guarda en `<project-root>/var/log/profiler.csv`. La variable `profiler.csv` se sobrescribe en cada actualización de página.

   Para deshabilitar el perfilador y eliminar el archivo de indicadores:

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
