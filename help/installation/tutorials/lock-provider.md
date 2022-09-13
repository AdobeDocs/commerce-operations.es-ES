---
title: Configuración del proveedor de bloqueo
description: Siga estos pasos para evitar que los trabajos cron duplicados y los grupos cron se ejecuten en la implementación de Adobe Commerce o Magento Open Source.
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# Configuración del proveedor de bloqueo

Antes de ejecutar este comando, debe hacer lo siguiente *o* debe [instalar la aplicación](../advanced.md):

* [Crear o actualizar la configuración de implementación](deployment.md)
* [Crear el esquema de la base de datos](database.md)

## Instalación segura

{{$include /help/_includes/secure-install.md}}

## Configuración del bloqueo

Configure un proveedor de bloqueo para evitar el lanzamiento de trabajos cron duplicados y grupos cron. (Requiere Adobe Commerce o Magento Open Source 2.2.x, 2.2.5 y posteriores, y 2.3.3 y posteriores).

Adobe Commerce y el Magento Open Source utilizan la base de datos para guardar los bloqueos de forma predeterminada. Si tiene varios nodos en los servidores, se recomienda utilizar Zookeeper como proveedor de bloqueo.

Si ejecuta Adobe Commerce en la infraestructura de la nube, no es necesario configurar la configuración del proveedor de bloqueo. La aplicación configura el proveedor de bloqueo de archivos para proyectos Pro durante el proceso de aprovisionamiento. Consulte [Variables de nube](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### Uso del comando

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descripciones de parámetros

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--lock-provider` | Bloquear nombre del proveedor: `db`, `zookeeper`o `file`.<br><br>El proveedor de bloqueo predeterminado: `db` | No |
| `--lock-db-prefix` | El prefijo db específico para evitar conflictos de bloqueo al usar la variable `db` bloquear proveedor.<br><br>El valor predeterminado: `NULL` | No |
| `--lock-zookeeper-host` | Host y puerto para conectarse al clúster de Zookeeper cuando utiliza el `zookeeper` bloquear proveedor.<br><br>Por ejemplo: `127.0.0.1:2181` | Sí, si establece `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Ruta donde Zookeeper guarda los bloqueos.<br><br>La ruta predeterminada es: `/magento/locks` | No |
| `--lock-file-path` | Ruta donde se guardan los bloqueos de archivo. | Sí, si establece `--lock-provider=file` |
