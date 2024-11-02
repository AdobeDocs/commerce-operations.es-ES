---
title: Configuración del proveedor de bloqueos
description: Siga estos pasos para evitar que los trabajos cron y los grupos cron duplicados se ejecuten en la implementación de Adobe Commerce.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Configuración del proveedor de bloqueos

Antes de ejecutar este comando, debe hacer lo siguiente *o* y debe [instalar la aplicación](../advanced.md):

* [Crear o actualizar la configuración de implementación](deployment.md)
* [Creación del esquema de base de datos](database.md)

## Instalación segura

{{$include /help/_includes/secure-install.md}}

## Configuración del bloqueo

Configure un proveedor de bloqueo para evitar el inicio de trabajos cron y grupos cron duplicados. (Requiere Adobe Commerce 2.2.x, 2.2.5 y posterior, y 2.3.3 y posterior).

Adobe Commerce utiliza la base de datos para guardar bloqueos de forma predeterminada. Si tiene varios nodos en sus servidores, le recomendamos que utilice Zookeeper como proveedor de bloqueos.

Si está ejecutando Adobe Commerce en una infraestructura en la nube, no es necesario configurar el proveedor de bloqueos. La aplicación configura el proveedor de bloqueo de archivos para proyectos Pro durante el proceso de aprovisionamiento. Consulte [Variables de nube](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud).

### Uso de comandos

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descripciones de parámetros

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--lock-provider` | Bloquear nombre de proveedor: `db`, `zookeeper` o `file`.<br><br>El proveedor de bloqueo predeterminado: `db` | No |
| `--lock-db-prefix` | Prefijo de base de datos específico para evitar conflictos de bloqueo al utilizar el proveedor de bloqueo `db`.<br><br>El valor predeterminado: `NULL` | No |
| `--lock-zookeeper-host` | Host y puerto para conectarse al clúster de Zookeeper cuando se utiliza el proveedor de bloqueo `zookeeper`.<br><br>Por ejemplo: `127.0.0.1:2181` | Sí, si se establece `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | El camino donde Zookeeper guarda las cerraduras.<br><br>La ruta predeterminada es: `/magento/locks` | No |
| `--lock-file-path` | Ruta de acceso donde se guardan los bloqueos de archivo. | Sí, si se establece `--lock-provider=file` |
