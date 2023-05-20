---
title: Configuración del proveedor de bloqueos
description: Siga estos pasos para evitar que los trabajos cron y los grupos cron duplicados se ejecuten en la implementación de Adobe Commerce o de Magento Open Source.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Configuración del proveedor de bloqueos

Antes de ejecutar este comando, debe hacer lo siguiente *o* usted debe [instalar la aplicación](../advanced.md):

* [Crear o actualizar la configuración de implementación](deployment.md)
* [Creación del esquema de base de datos](database.md)

## Instalación segura

{{$include /help/_includes/secure-install.md}}

## Configuración del bloqueo

Configure un proveedor de bloqueo para evitar el inicio de trabajos cron y grupos cron duplicados. (Requiere Adobe Commerce o Magento Open Source 2.2.x, 2.2.5 y posterior, y 2.3.3 y posterior).

Adobe Commerce y Magento Open Source utilizan la base de datos para guardar bloqueos de forma predeterminada. Si tiene varios nodos en sus servidores, le recomendamos que utilice Zookeeper como proveedor de bloqueos.

Si está ejecutando Adobe Commerce en una infraestructura en la nube, no es necesario configurar el proveedor de bloqueos. La aplicación configura el proveedor de bloqueo de archivos para proyectos Pro durante el proceso de aprovisionamiento. Consulte [Variables de nube](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### Uso de comandos

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descripciones de parámetros

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--lock-provider` | Bloquear nombre de proveedor: `db`, `zookeeper`, o `file`.<br><br>El proveedor de bloqueo predeterminado: `db` | No |
| `--lock-db-prefix` | El prefijo de base de datos específico para evitar conflictos de bloqueo al utilizar `db` bloquear proveedor.<br><br>El valor predeterminado: `NULL` | No |
| `--lock-zookeeper-host` | Host y puerto para conectarse al clúster de Zookeeper cuando se utiliza el `zookeeper` bloquear proveedor.<br><br>Por ejemplo: `127.0.0.1:2181` | Sí, si se establece `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | El camino donde Zookeeper guarda las cerraduras.<br><br>La ruta predeterminada es: `/magento/locks` | No |
| `--lock-file-path` | Ruta de acceso donde se guardan los bloqueos de archivo. | Sí, si se establece `--lock-provider=file` |
