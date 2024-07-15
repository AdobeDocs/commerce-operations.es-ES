---
title: Propiedad de archivos y permisos
description: Obtenga información acerca de la importancia de los permisos del sistema de archivos al trabajar con instalaciones locales de Adobe Commerce.
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Propiedad de archivos y permisos

Es importante proteger la instalación de Adobe Commerce en un entorno de desarrollo para ayudar a evitar problemas relacionados con personas o procesos no autorizados que acceden al sistema y pueden dañarlo. Utilice las siguientes directrices de propiedad y permisos del sistema de archivos para proteger la instalación.

## Propietario del sistema de archivos

El propietario del sistema de archivos es un usuario que posee y mantiene permisos de escritura en los archivos del sistema de archivos.

Existen dos tipos de propietarios del sistema de archivos:

- **Hosting compartido con un solo usuario**

  Los proveedores de alojamiento compartido permiten iniciar sesión en el servidor de aplicaciones como un usuario. Como usuario único, puede iniciar sesión, transferir archivos mediante FTP y ejecutar el servidor web. Tiene la opción de configurar un [`umask`](#restrict-access-with-a-umask) para restringir aún más el acceso, especialmente en un entorno de producción.

- **Hosting privado con dos usuarios**

  El alojamiento privado es útil si administra un servidor de aplicaciones. Cada usuario tiene una responsabilidad específica:

   - El _usuario del servidor web_ ejecuta el administrador y la tienda.

   - El _usuario de línea de comandos_ ejecuta trabajos cron y utilidades de línea de comandos.

  Ambos usuarios necesitan los mismos permisos para el sistema de archivos, por lo que es mejor usar un [grupo compartido](configure-permissions.md#set-ownership-and-permissions-for-two-users) y establecer un [`umask`](#restrict-access-with-a-umask).

### Restringir el acceso con una máscara de usuario

Para reforzar la seguridad, especialmente en un entorno de producción en un sistema de alojamiento compartido, puede usar `umask` para restringir el acceso. Un `umask`, también denominado _máscara de creación del sistema de archivos_, es un conjunto de bits que controla cómo se establecen los permisos de archivo para los archivos recién creados.

>[!WARNING]
>
>La seguridad del sistema de archivos es compleja e importante. Le recomendamos encarecidamente que consulte con un administrador de sistema o de red experimentado antes de decidir el nivel de permisos que desea establecer. Proporcionamos un mecanismo para que lo utilice, pero la creación de una estrategia de permisos es su responsabilidad.

Adobe Commerce usa una máscara predeterminada de tres bits: `002`. Reste la máscara predeterminada de los valores predeterminados de UNIX de 666 para archivos y 777 para directorios.

Por ejemplo:

- **775 para directorios**: control total por parte del usuario, control total por parte del grupo y permite a todos atravesar el directorio. Estos permisos suelen ser necesarios para los proveedores de alojamiento compartido.

- **664 para archivos**: grabable por el usuario, grabable por el grupo y de solo lectura para todos los demás.

Para obtener más información acerca de cómo crear un archivo de `magento_umask`, vea [Establecer una máscara de usuario](../../next-steps/set-umask.md).

## Permisos, propiedad y modos de aplicación

Se recomiendan diferentes permisos y propiedad al utilizar los diferentes modos de aplicación de Adobe Commerce:

- Predeterminado
- Desarrollador
- Producción

Consulte [Acerca de los modos](../../../configuration/bootstrap/application-modes.md) en la _Guía de configuración_.

Discutimos las recomendaciones de permisos en [Permisos de acceso a sistemas de archivos](../../../configuration/deployment/file-system-permissions.md) en la _Guía de configuración_.

>[!TIP]
>
>Antes de instalar Adobe Commerce, revise [Configurar la propiedad y los permisos de los archivos](configure-permissions.md).
