---
title: Propiedad de archivos y permisos
description: Obtenga información acerca de la importancia de los permisos del sistema de archivos al trabajar con instalaciones locales de Adobe Commerce y Magento Open Source.
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# Propiedad de archivos y permisos

Es importante proteger la instalación de Adobe Commerce o de Magento Open Source en un entorno de desarrollo para evitar problemas relacionados con personas o procesos no autorizados que acceden al sistema y que podrían dañarlo. Utilice las siguientes directrices de propiedad y permisos del sistema de archivos para proteger la instalación.

## Propietario del sistema de archivos

El propietario del sistema de archivos es un usuario que posee y mantiene permisos de escritura en los archivos del sistema de archivos.

Existen dos tipos de propietarios del sistema de archivos:

- **Alojamiento compartido con un solo usuario**

   Los proveedores de alojamiento compartido permiten iniciar sesión en el servidor de aplicaciones como un usuario. Como usuario único, puede iniciar sesión, transferir archivos mediante FTP y ejecutar el servidor web. Tiene la opción de configurar una [`umask`](#restrict-access-with-a-umask) para restringir aún más el acceso, especialmente en un entorno de producción.

- **Alojamiento privado con dos usuarios**

   El alojamiento privado es útil si administra un servidor de aplicaciones. Cada usuario tiene una responsabilidad específica:

   - El _usuario de servidor web_ ejecuta el administrador y la tienda.

   - El _usuario de línea de comandos_ ejecuta trabajos cron y utilidades de línea de comandos.
   Ambos usuarios requieren los mismos permisos para el sistema de archivos, por lo que es mejor utilizar un [grupo compartido](configure-permissions.md#set-ownership-and-permissions-for-two-users) y establezca un [`umask`](#restrict-access-with-a-umask).

### Restringir el acceso con una máscara de usuario

Para reforzar la seguridad, especialmente en un entorno de producción en un sistema de alojamiento compartido, puede utilizar `umask` para restringir el acceso. A `umask`—también conocido como _máscara de creación del sistema de archivos_: es un conjunto de bits que controla cómo se definen los permisos de fichero para los ficheros recién creados.

>[!WARNING]
>
>La seguridad del sistema de archivos es compleja e importante. Le recomendamos encarecidamente que consulte con un administrador de sistema o de red experimentado antes de decidir el nivel de permisos que desea establecer. Proporcionamos un mecanismo para que lo utilice, pero la creación de una estrategia de permisos es su responsabilidad.

Adobe Commerce y Magento Open Source utilizan una máscara predeterminada de tres bits: `002`. Reste la máscara predeterminada de los valores predeterminados de UNIX de 666 para archivos y 777 para directorios.

Por ejemplo:

- **775 para directorios**: control total por el usuario, control total por el grupo y permite a todos atravesar el directorio. Estos permisos suelen ser necesarios para los proveedores de alojamiento compartido.

- **664 para archivos**: el usuario puede escribir, el grupo puede escribir y solo lectura para todos los demás.

Para obtener más información sobre la creación de un `magento_umask` archivo, consulte [Establecer una máscara de usuario](../../next-steps/set-umask.md).

## Permisos, propiedad y modos de aplicación

Se recomiendan diferentes permisos y propiedad cuando se utilizan los distintos modos de aplicación de Adobe Commerce y Magento Open Source:

- Predeterminado
- Desarrollador
- Producción

Consulte [Acerca de los modos](../../../configuration/bootstrap/application-modes.md) en el _Guía de configuración_.

Discutimos más sobre las recomendaciones de permisos en [Permisos de acceso a sistemas de archivos](../../../configuration/deployment/file-system-permissions.md) en el _Guía de configuración_.

>[!TIP]
>
>Antes de instalar Adobe Commerce o Magento Open Source, revise [Configurar la propiedad y los permisos del archivo](configure-permissions.md).
