---
title: Migración de cambios
description: Aprenda a migrar solo los datos que hayan cambiado desde la última migración de datos de Magento 1 con la variable [!DNL Data Migration Tool].
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# Migración de cambios

La herramienta de migración incremental instala tablas deltalog (con prefijo `m2_cl_*`) y déclencheur (para el seguimiento de cambios) en la base de datos de Magento 1 durante el [migración de datos](data.md). Estas tablas y déclencheur deltalog son esenciales para garantizar que se migran solo los cambios realizados en el Magento 1 desde la última vez que se migraron los datos. Estos cambios son:

* Datos que los clientes agregaron mediante [storefront](https://glossary.magento.com/storefront) (se han creado pedidos, revisiones y cambios en los perfiles de los clientes)

* Todas las operaciones con pedidos, productos y categorías en la variable [Administrador](https://glossary.magento.com/magento-admin) panel

>[!NOTE]
>
>Todas las demás entidades nuevas o actualizadas introducidas a través de la Administración, como los atributos o las páginas de CMS, no se incluyen en la migración incremental y no se migran.


Antes de empezar, siga los siguientes pasos para prepararse:

1. Inicie sesión en el servidor de Magento como [el propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Cambio en el Magento `/bin` o asegúrese de que se agrega a su PATH del sistema.

Consulte la [primeros pasos](overview.md#first-steps) para obtener más información.

## Ejecutar el comando de migración incremental

Para empezar a migrar cambios incrementales, ejecute:

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Donde:

* `[-r|--reset]` es un argumento opcional que inicia la migración desde el principio. Puede utilizar este argumento para probar la migración.

* `[-a|--auto]` es un argumento opcional que evita que la migración se detenga cuando encuentra errores de comprobación de integridad.

* `{<path to config.xml>}` es la ruta absoluta del sistema de archivos a `config.xml`; este argumento es obligatorio.

>[!NOTE]
>
>La migración incremental es un proceso continuo; se reinicia automáticamente cada 5 segundos. Utilice CTRL-C para anular el proceso de migración.


## Migración de datos creados por extensiones de terceros

En el `Delta` el modo [!DNL Data Migration Tool] migra datos creados únicamente por los módulos propios de Magento y no es responsable del código o las extensiones realizadas por desarrolladores de terceros. Si estas extensiones crearon datos en la base de datos de tienda y el comerciante desea que estos datos estén en el Magento 2 — Archivos de configuración de la variable [!DNL Data Migration Tool] debe crearse y modificarse en consecuencia.

Si una [Extensión](https://glossary.magento.com/extension) tiene sus propias tablas y debe realizar un seguimiento de los cambios para la migración delta, siga estos pasos:

1. Agregue las tablas que desea rastrear a la `deltalog.xml` file
1. Cree una clase delta adicional que amplíe la variable `Migration\App\Step\AbstractDelta`
1. Agregue el nombre de la clase recién creada a la sección del modo delta de `config.xml`
