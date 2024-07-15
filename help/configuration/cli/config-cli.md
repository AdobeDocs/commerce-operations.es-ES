---
title: Herramienta de línea de comandos
description: Utilice la herramienta de línea de comandos de Commerce para ejecutar las tareas de instalación y configuración.
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Herramienta de línea de comandos

Commerce tiene una interfaz de línea de comandos (CLI), `<magento_root>/bin/magento`, que ejecuta tareas de instalación y configuración, entre las que se incluyen:

- Instalación de Commerce (y tareas relacionadas como actualizar el esquema de la base de datos, crear una configuración de implementación)
- Borrando la caché
- Administración de índices, incluida la reindexación
- Creación de diccionarios de traducción y paquetes de traducción
- Generación de clases inexistentes como fábricas e interceptores para complementos, generación de la configuración de inyección de dependencias para el administrador de objetos
- Implementación de archivos de vista estática
- Creación de CSS a partir de Less

Los beneficios adicionales incluyen:

- Un solo comando (`<magento_root>/bin/magento list`) enumera todos los comandos de instalación y configuración disponibles.
- Interfaz de usuario coherente basada en Symfony.
- La CLI es extensible para que los desarrolladores de terceros puedan &quot;conectarse&quot; a ella. Esto tiene la ventaja adicional de eliminar la curva de aprendizaje de los usuarios.
- No se muestran los comandos para los módulos desactivados.

En este tema se describe la configuración del software de Adobe Commerce mediante la CLI. Para obtener información acerca de la instalación de Commerce, consulte [Flujo de instalación](../../installation/overview.md) en la _Guía de instalación_.

## Requisitos previos

Antes de empezar a utilizar la CLI, asegúrese de lo siguiente:

1. Su sistema cumple los requisitos mencionados en [Requisitos del sistema](../../installation/system-requirements.md) en la _Guía de instalación_.
1. Ha completado todas las tareas previas descritas en [Requisitos previos](../../installation/prerequisites/overview.md) en la _Guía de instalación_.
1. Después de iniciar sesión en el servidor de Commerce, cambie a un usuario que tenga permisos para escribir en el sistema de archivos de Commerce. Vea [cambiar al propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md) en la _Guía de instalación_.

## Ejecución de comandos

Para el shell de bash, use la siguiente sintaxis para cambiar al propietario del sistema de archivos e ingresar el comando al mismo tiempo:

```bash
su <file system owner> -s /bin/bash -c <command>
```

Si el propietario del sistema de archivos no permite inicios de sesión, puede utilizar lo siguiente:

```bash
sudo -u <file system owner> <command>
```

**Para ejecutar comandos CLI desde cualquier directorio**:

Agregar `<magento_root>/bin` a su sistema `PATH`.

Ejemplo de shell de bash para CentOS:

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

Opcionalmente, puede ejecutar lo siguiente:

- `cd <magento_root>/bin` y ejecutarlos como `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` es un subdirectorio del servidor web docroot
