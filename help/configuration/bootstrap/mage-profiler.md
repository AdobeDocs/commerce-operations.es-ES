---
title: Habilitar generación de perfiles
description: Obtenga más información sobre cómo habilitar el analizador de imágenes para utilizarlo con sus herramientas analíticas.
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Habilitar generación de perfiles

Con los perfiles de Commerce, puede:

- Habilite un generador de perfiles integrado.

  Puede utilizar un generador de perfiles integrado con Commerce para realizar tareas como analizar el rendimiento. La naturaleza de los perfiles depende de las herramientas analíticas que utilice. Admitimos varios formatos, incluido HTML. Cuando se habilita el generador de perfiles, se genera un archivo de `var/profiler.flag` que indica que el generador de perfiles está habilitado y que hay configuraciones. Cuando está desactivado, este archivo se elimina.

- Mostrar gráficos de dependencias en una página de Commerce.

  Un gráfico de dependencias _1} es una lista de dependencias de objetos y todas sus dependencias, todas las dependencias de esas dependencias, etc._

  Debería interesarle especialmente la lista de _dependencias sin usar_, que son objetos que se crearon porque se solicitaron en algún constructor, pero que nunca se utilizaron (es decir, no se llamó a ninguno de sus métodos). Como resultado, se desperdician el tiempo y la memoria del procesador empleados para crear estas dependencias.

Commerce proporciona la funcionalidad base en [`Magento\Framework\Profiler`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/Profiler.php).

Puede habilitar y configurar el generador de perfiles mediante una variable MAGE_PROFILER o la línea de comandos.

## Set MAGE_PROFILER

Puede establecer el valor de `MAGE_PROFILER` de cualquiera de las formas descritas en [Establecer el valor de los parámetros de arranque](../bootstrap/set-parameters.md).

`MAGE_PROFILER` admite los siguientes valores:

- `1` para habilitar la salida de un generador de perfiles específico.

  Puede utilizar uno de los siguientes valores para habilitar un generador de perfiles específico:

   - `csvfile` que usa [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php)
   - Cualquier otro valor (excepto `2`), incluido un valor vacío, que utiliza [`Magento\Framework\Profiler\Driver\Standard\Output\Html`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php)

- `2` para habilitar los gráficos de dependencias.

  Los gráficos de dependencias generalmente se muestran en la parte inferior de una página. La siguiente figura muestra una parte del resultado:

  ![Gráficos de dependencias](../../assets/configuration/depend-graphs.png)

## Comandos CLI

Puede habilitar o deshabilitar el generador de perfiles mediante comandos CLI:

- `dev:profiler:enable <type>` habilita el generador de perfiles con `type` de `html` (predeterminado) o `csvfile`. Cuando se habilita, se crea un archivo de indicador `var/profiler.flag`.
- `dev:profiler:disable` deshabilita el generador de perfiles. Cuando está deshabilitado, se quita el archivo de indicador `var/profiler.flag`.

Para habilitar los gráficos de dependencias, utilice la opción de variable.

**Para habilitar o deshabilitar el analizador**:

1. Inicie sesión en el servidor de Commerce.
1. Cambie al directorio de instalación de Commerce.
1. Habilite el analizador como propietario del sistema de archivos:

   Para habilitar el generador de perfiles con el tipo `html` y crear un archivo de indicador:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   Para habilitar el generador de perfiles con el tipo `csvfile` y crear un archivo de indicador:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   El resultado se guardó en `<project-root>/var/log/profiler.csv`. `profiler.csv` se reemplaza en cada actualización de página.

   Para deshabilitar el generador de perfiles y quitar el archivo de indicador:

   ```bash
   bin/magento dev:profiler:disable
   ```

