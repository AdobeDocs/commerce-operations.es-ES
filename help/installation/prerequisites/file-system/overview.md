---
title: Propiedad y permisos de archivos
description: Obtenga información sobre la importancia de los permisos del sistema de archivos al trabajar con instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Propiedad y permisos de archivos

Es importante asegurar la instalación de Adobe Commerce o Magento Open Source en un entorno de desarrollo para ayudar a evitar problemas relacionados con personas o procesos no autorizados que accedan a su sistema (y que puedan dañar su sistema). Utilice las siguientes directrices de propiedad y permisos del sistema de archivos para proteger la instalación.

## Propietario del sistema de archivos

El propietario del sistema de archivos es un usuario que posee y posee permisos de escritura para archivos del sistema de archivos.

Existen dos tipos de propietarios de sistemas de archivos:

- **Alojamiento compartido con un solo usuario**

   Los proveedores de alojamiento compartido permiten iniciar sesión en el servidor de aplicaciones como un solo usuario. Como usuario único, puede iniciar sesión, transferir archivos mediante FTP y ejecutar el servidor web. Tiene la opción de configurar un [`umask`](#restrict-access-with-a-umask) restringir aún más el acceso, especialmente en un entorno de producción.

- **Alojamiento privado con dos usuarios**

   El alojamiento privado es útil si administra un servidor de aplicaciones. Cada usuario tiene una responsabilidad específica:

   - La variable _usuario del servidor web_ ejecuta Admin y storefront.

   - La variable _usuario de línea de comandos_ ejecuta trabajos cron y utilidades de línea de comandos.
   Ambos usuarios requieren los mismos permisos para el sistema de archivos, por lo que es mejor utilizar un [grupo compartido](configure-permissions.md#set-ownership-and-permissions-for-two-users) y establezca un [`umask`](#restrict-access-with-a-umask).

### Restringir el acceso con una máscara

Para reforzar la seguridad, especialmente en un entorno de producción en un sistema de alojamiento compartido, puede utilizar `umask` para restringir el acceso. A `umask`—también denominado _máscara de creación del sistema de archivos_: es un conjunto de bits que controla cómo se establecen los permisos de archivo para los archivos recién creados.

>[!WARNING]
>
>La seguridad del sistema de archivos es compleja e importante. Se recomienda consultar a un administrador de sistemas o a un administrador de red con experiencia antes de decidir el nivel de permisos que desea establecer. Proporcionamos un mecanismo que puede usar, pero la creación de una estrategia de permisos es responsabilidad suya.

Adobe Commerce y el Magento Open Source utilizan una máscara predeterminada de tres bits: `002`. Reste la máscara predeterminada de los valores predeterminados de UNIX de 666 para archivos y 777 para directorios.

Por ejemplo:

- **775 para directorios**: control total por parte del usuario, control total por parte del grupo y permite a todos recorrer el directorio. Estos permisos suelen ser necesarios para proveedores de alojamiento compartidos.

- **664 para archivos**: escribible por el usuario, escribible por el grupo y solo lectura para todos los demás.

Para obtener más información sobre cómo crear un `magento_umask` archivo, consulte [Establecer una máscara](../../next-steps/set-umask.md).

## Modos de permisos, propiedad y aplicación

Se recomiendan diferentes permisos y propietarios cuando se utilizan los distintos modos de aplicación de Adobe Commerce y Magento Open Source:

- Predeterminado
- Desarrollador
- Producción

Consulte [Acerca de los modos](../../../configuration/bootstrap/application-modes.md) en el _Guía de configuración_.

Discutimos las recomendaciones de permisos en [Permisos de acceso de sistemas de archivos](../../../configuration/deployment/file-system-permissions.md) en el _Guía de configuración_.

>[!TIP]
>
>Antes de instalar Adobe Commerce o Magento Open Source, consulte [Configuración de la propiedad y los permisos de los archivos](configure-permissions.md).
