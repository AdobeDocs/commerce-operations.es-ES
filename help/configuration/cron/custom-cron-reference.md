---
title: Referencia de trabajo cron personalizado y grupo cron
description: Aprenda a personalizar crons mediante grupos de cron.
exl-id: 16e342ff-aa94-4e31-8c75-dfea1ef02706
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Personalización de la referencia de crons

Este tema le ayuda a configurar crontabs y, opcionalmente, grupos cron para módulos personalizados. Si el módulo personalizado necesita programar tareas periódicamente, debe configurar un crontab para ese módulo. A _crontab_ es una configuración de trabajo de cron.

Opcionalmente, puede configurar un grupo personalizado, que entre otras cosas le permite ejecutar trabajos cron definidos en ese grupo independientemente de otros trabajos cron.

Para ver un tutorial paso a paso, consulte [Configuración de trabajos cron personalizados y grupos cron (tutorial)](custom-cron-tutorial.md).

Para obtener una descripción general de los trabajos de cron, consulte [Configuración de trabajos cron](../cli/configure-cron-jobs.md).

## Configuración de grupos cron

En esta sección se explica cómo crear opcionalmente un grupo cron para un módulo personalizado. Si no necesita hacerlo, continúe con la siguiente sección.

A _grupo cron_ es un grupo lógico que le permite ejecutar cron fácilmente para más de un proceso a la vez. La mayoría de los módulos de Commerce utilizan `default` grupo cron; algunos módulos utilizan el `index` grupo.

Si va a implementar cron para un módulo personalizado, puede elegir utilizar el `default` o un grupo diferente.

**Para configurar un grupo cron para su módulo**:

Crear un `crontab.xml` en el directorio del módulo:

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

Para un grupo, el archivo debe tener el siguiente contenido:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="<group_name>">
        <job name="<job_name>" instance="<classpath>" method="<method>">
            <schedule><time></schedule>
        </job>
    </group>
</config>
```

Donde:

| Valor | Descripción |
|---|---|
| `group_name` | Nombre del grupo cron. El nombre del grupo no tiene que ser único. Puede ejecutar cron para un grupo a la vez. |
| `job_name` | ID único para este trabajo cron. |
| `classpath` | Clase para crear una instancia (classpath). |
| `method` | Método en `classpath` para llamar. |
| `time` | Programar en formato cron. Omita este parámetro si la programación se define en la base de datos de Commerce u otro almacenamiento. |

El resultante `crontab.xml` con dos grupos puede tener este aspecto:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="<job_1_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_2_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
    <group id="index">
        <job name="<job_3_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_4_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

Como ejemplo, consulte [Magento_Cliente crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Especificar las opciones del grupo Cron

Puede declarar un nuevo grupo y especificar sus opciones de configuración (todas las cuales se ejecutan en el ámbito de la vista de tienda) mediante el `cron_groups.xml` archivo, ubicado en:

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

A continuación se muestra un ejemplo del `cron_groups.xml` archivo:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
    <group id="<group_name>">
        <schedule_generate_every>1</schedule_generate_every>
        <schedule_ahead_for>4</schedule_ahead_for>
        <schedule_lifetime>2</schedule_lifetime>
        <history_cleanup_every>10</history_cleanup_every>
        <history_success_lifetime>60</history_success_lifetime>
        <history_failure_lifetime>600</history_failure_lifetime>
        <use_separate_process>1</use_separate_process>
    </group>
</config>
```

Donde:

| Opción | Descripción |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | Frecuencia (en minutos) con la que se escriben las programaciones en `cron_schedule` tabla. |
| `schedule_ahead_for` | Tiempo (en minutos) antes de que las programaciones se escriban en el `cron_schedule` tabla. |
| `schedule_lifetime` | Ventana de tiempo (en minutos) que debe iniciarse un trabajo cron o que se considera que el trabajo cron se ha perdido (&quot;demasiado tarde&quot; para ejecutarse). |
| `history_cleanup_every` | Tiempo (en minutos) que el historial cron se conserva en la base de datos. |
| `history_success_lifetime` | Tiempo (en minutos) que se mantiene en la base de datos el registro de los trabajos cron completados correctamente. |
| `history_failure_lifetime` | Tiempo (en minutos) que se mantiene en la base de datos el registro de trabajos cron fallidos. |
| `use_separate_process` | Ejecutar los trabajos de este grupo cron en un proceso php independiente |

## Deshabilitar un trabajo cron

Los trabajos de Cron no tienen un `disable` función como la que tenemos para [observadores](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). Sin embargo, un trabajo cron se puede deshabilitar mediante la siguiente técnica: `schedule` una hora que contiene una fecha que nunca ocurrirá.

Por ejemplo, deshabilite la variable `visitor_clean` trabajo cron definido en `Magento_Customer` módulo:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

Para deshabilitar la variable `visitor_clean` trabajo cron, cree un módulo personalizado y vuelva a escribir el `visitor_clean` trabajo cron `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

Ahora, la `visitor_clean` El trabajo cron se ha configurado para ejecutarse a las 00:00 del 30 de febrero, en la fecha que nunca ocurrirá.
