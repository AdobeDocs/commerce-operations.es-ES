---
title: Herramienta Línea de comandos
description: Utilice la herramienta de línea de comandos Commerce para ejecutar las tareas de instalación y configuración.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---


# Herramienta Línea de comandos

Commerce tiene una interfaz de línea de comandos (CLI)—`<magento_root>/bin/magento`—que ejecuta tareas de instalación y configuración, que incluyen:

- Instalación de Commerce (y tareas relacionadas como actualizar el esquema de la base de datos, crear una configuración de implementación)
- Borrado de la caché
- Administración de índices, incluida la reindexación
- Creación de diccionarios de traducción y paquetes de traducción
- Generación de clases inexistentes, como fábricas e interceptores para complementos, que generan la configuración de inyección de dependencias para el administrador de objetos
- Implementación de archivos de vista estáticos
- Creación de CSS a partir de menos

Los beneficios adicionales incluyen:

- Un solo comando (`<magento_root>/bin/magento list`) enumera todos los comandos de instalación y configuración disponibles.
- Interfaz de usuario coherente basada en Symfony.
- La CLI es extensible, por lo que los desarrolladores de terceros pueden &quot;conectarla&quot; a ella. Esto tiene la ventaja adicional de eliminar la curva de aprendizaje de los usuarios.
- Los comandos para los módulos desactivados no se muestran.

En este tema se analiza la configuración del software Adobe Commerce y del Magento Open Source mediante la CLI. Para obtener información sobre la instalación de Commerce, consulte [Flujo de instalación](https://devdocs.magento.com/guides/v2.4/install-gde/install-flow-diagram.html) en el _Guía de instalación_.

## Requisitos previos

Antes de comenzar a utilizar la CLI, asegúrese de que:

1. Su sistema cumple los requisitos descritos en [Requisitos del sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) en el _Guía de instalación_.
1. Ha completado todas las tareas previas que se describen en [Requisitos previos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/prereq-overview.html) en el _Guía de instalación_.
1. Después de iniciar sesión en el servidor de Commerce, cambie a un usuario que tenga permisos para escribir en el sistema de archivos de Commerce. Consulte [cambie al propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html) en el _Guía de instalación_.

## Ejecución de comandos

Para el shell de bash, utilice la siguiente sintaxis para cambiar al propietario del sistema de archivos e introduzca el comando al mismo tiempo:

```bash
su <file system owner> -s /bin/bash -c <command>
```

Si el propietario del sistema de archivos no permite inicios de sesión, puede utilizar lo siguiente:

```bash
sudo -u <file system owner> <command>
```

**Para ejecutar comandos CLI desde cualquier directorio**:

Agregar `<magento_root>/bin` al sistema `PATH`.

Ejemplo de shell bash para CentOS:

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

De forma opcional, puede ejecutar lo siguiente:

- `cd <magento_root>/bin` y ejecútelos como `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` es un subdirectorio de su servidor web docroot
