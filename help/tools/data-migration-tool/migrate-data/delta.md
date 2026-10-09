---
title: Migrar cambios
description: Descubra cómo migrar únicamente los datos que han cambiado desde la última migración de datos de Magento 1 con [!DNL Data Migration Tool].
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%
---
# Migrar cambios

La herramienta de migración incremental instala tablas deltalog (con prefijo `m2_cl_*`) y déclencheur (para el seguimiento de cambios) en la base de datos de Magento 1 durante la [migración de datos](data.md). Estas tablas y déclencheur de deltalog son esenciales para garantizar que solo se migran los cambios realizados en Magento 1 desde la última vez que se migraron los datos. Estos cambios son:

* Datos que los clientes agregaron mediante tienda (pedidos creados, revisiones y cambios en los perfiles de los clientes)

* Todas las operaciones con pedidos, productos y categorías en el panel Administración

>[!NOTE]
>
>Todas las demás entidades nuevas o actualizadas introducidas a través de Admin, como atributos o páginas de CMS, no se incluyen en la migración incremental y no se migran.


Antes de empezar, siga estos pasos para prepararse:

1. Inicie sesión en el servidor de aplicaciones como [propietario del sistema de archivos](../../../installation/prerequisites/file-system/overview.md).
1. Cambie al directorio `/bin` o asegúrese de que se agrega a su sistema `PATH`.

Consulte la sección [primeros pasos](overview.md#first-steps) para obtener más información.

## Ejecute el comando de migración incremental

Para empezar a migrar cambios incrementales, ejecute:

```shell
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Donde:

* `[-r|--reset]` es un argumento opcional que inicia la migración desde el principio. Puede utilizar este argumento para probar la migración.

* `[-a|--auto]` es un argumento opcional que impide que se detenga la migración cuando encuentra errores de comprobación de integridad.

* `{<path to config.xml>}` es la ruta absoluta del sistema de archivos a `config.xml`; este argumento es obligatorio.

>[!NOTE]
>
>La migración incremental es un proceso continuo; se reinicia automáticamente cada 5 segundos. Utilice CTRL-C para anular el proceso de migración.


## Migrar datos creados por extensiones de terceros

En el modo `Delta`, [!DNL Data Migration Tool] migra datos creados únicamente por módulos propios de Magento y no es responsable del código o las extensiones realizadas por desarrolladores de terceros. Si estas extensiones crearon datos en la base de datos de la tienda y el comerciante desea tenerlos en Magento 2, los archivos de configuración de [!DNL Data Migration Tool] deben crearse y modificarse en consecuencia.

Si una extensión tiene sus propias tablas y necesita realizar un seguimiento de sus cambios para la migración delta, siga estos pasos:

1. Agregar las tablas de las que se realizará un seguimiento al archivo `deltalog.xml`
1. Crear una clase delta adicional que extienda `Migration\App\Step\AbstractDelta`
1. Agregue el nombre de la clase recién creada a la sección de modo delta de `config.xml`
