---
title: Referencia de trabajo de cron personalizada y de grupo cron
description: Aprenda a personalizar crons usando grupos cron.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---


# Personalización de la referencia de crons

Este tema le ayuda a configurar crontabs y, opcionalmente, grupos cron para módulos personalizados. Si el módulo personalizado necesita programar tareas periódicamente, debe configurar un crontab para ese módulo. A _crontab_ es una configuración de trabajo cron.

De forma opcional, puede configurar un grupo personalizado, que, entre otras cosas, le permite ejecutar trabajos cron definidos en ese grupo independientemente de otros trabajos cron.

Para ver un tutorial paso a paso, consulte [Configuración de trabajos cron personalizados y grupos cron (tutorial)](custom-cron-tutorial.md).

Para obtener información general sobre los trabajos cron, consulte [Configurar trabajos cron](../cli/configure-cron-jobs.md).

## Configurar grupos cron

En esta sección se explica cómo crear opcionalmente un grupo cron para un módulo personalizado. Si no necesita hacerlo, continúe con la siguiente sección.

A _grupo cron_ es un grupo lógico que le permite ejecutar fácilmente cron durante más de un proceso a la vez. La mayoría de los módulos de Commerce utilizan `default` grupo cron; algunos módulos utilizan la variable `index` grupo.

Si va a implementar cron para un módulo personalizado, puede elegir usar la variable `default` o un grupo diferente.

**Para configurar un grupo cron para su módulo**:

Cree un `crontab.xml` en el directorio del módulo:

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
| `classpath` | Clase a crear (ruta de clase). |
| `method` | Método en `classpath` para llamar a . |
| `time` | Programar en formato cron. Omita este parámetro si la programación está definida en la base de datos de Commerce u otro almacenamiento. |

El resultado `crontab.xml` con dos grupos puede tener este aspecto:

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

Como ejemplo, consulte [Magento_Customer crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Especificación de las opciones del grupo Cron

Puede declarar un nuevo grupo y especificar sus opciones de configuración (todas las cuales se ejecutan en el ámbito de vista de tienda) mediante la variable `cron_groups.xml` , ubicado en:

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

A continuación se muestra un ejemplo de la variable `cron_groups.xml` archivo:

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
| `schedule_generate_every` | Frecuencia (en minutos) con la que las programaciones se escriben en la variable `cron_schedule` tabla. |
| `schedule_ahead_for` | Tiempo (en minutos) previo a que las programaciones se escriban en la variable `cron_schedule` tabla. |
| `schedule_lifetime` | Ventana de tiempo (en minutos) en la que debe iniciarse un trabajo cron o el trabajo cron se considera perdido (&quot;demasiado tarde&quot; para ejecutarse). |
| `history_cleanup_every` | Tiempo (en minutos) que el historial de cron se mantiene en la base de datos. |
| `history_success_lifetime` | Tiempo (en minutos) que el registro de trabajos cron completados correctamente se conserva en la base de datos. |
| `history_failure_lifetime` | Tiempo (en minutos) que el registro de trabajos cron fallidos se mantiene en la base de datos. |
| `use_separate_process` | Ejecute los trabajos de este grupo cron en un proceso de php independiente |

## Desactivación de un trabajo cron

Los trabajos cron no tienen `disable` característica como la que tenemos para [observadores](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). Sin embargo, un trabajo cron se puede deshabilitar usando la siguiente técnica: `schedule` una hora que contiene una fecha que nunca se producirá.

Por ejemplo, deshabilite el `visitor_clean` trabajo cron que se define en `Magento_Customer` módulo:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

Para desactivar el `visitor_clean` trabajo cron, crear un módulo personalizado y reescribir el `visitor_clean` trabajo cron `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

Ahora, la variable `visitor_clean` el trabajo de cron se ha configurado para ejecutarse a las 00:00 del 30 de febrero, en la fecha en que nunca se producirá.
