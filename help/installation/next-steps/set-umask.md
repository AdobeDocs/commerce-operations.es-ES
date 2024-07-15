---
title: Establecer una máscara de usuario (opcional)
description: Mejore la postura de seguridad de su instalación local de Adobe Commerce restringiendo los permisos del sistema de archivos.
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Establecer una máscara de usuario (opcional)

El grupo de servidores web debe tener permisos de escritura en determinados directorios del sistema de archivos; sin embargo, es posible que desee una mayor seguridad, especialmente en la producción. Proporcionamos la flexibilidad para que restrinjas aún más esos permisos usando [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

Nuestra solución es permitirle crear opcionalmente un archivo con el nombre `magento_umask` en el directorio raíz de la aplicación que restrinja los permisos para el grupo de servidores web y para todos los demás.

>[!NOTE]
>
>Se recomienda cambiar la máscara de usuario en un sistema de alojamiento compartido o de un solo usuario. Si tiene un servidor de aplicaciones privado, el grupo debe tener acceso de escritura al sistema de archivos; umask elimina el acceso de escritura del grupo.

La máscara de usuario predeterminada (sin `magento_umask` especificado) es `002`, lo que significa que:

* 775 para directorios, lo que significa control total por parte del usuario, control total por parte del grupo y permite a todos atravesar el directorio. Estos permisos suelen ser necesarios para los proveedores de alojamiento compartido.

* 664 para archivos, lo que significa que el usuario puede escribir, el grupo puede escribir y solo lectura para todos los demás

Una sugerencia habitual es utilizar un valor de `022` en el archivo `magento_umask`, lo que significa que:

* 755 para directorios: control total para el usuario y todos los demás pueden atravesar directorios.
* 644 para archivos: permisos de lectura y escritura para el usuario y de solo lectura para todos los demás.

Para establecer `magento_umask`:

1. En un terminal de línea de comandos, inicie sesión en su servidor de aplicaciones como [propietario del sistema de archivos](../prerequisites/file-system/overview.md).
1. Vaya al directorio de instalación de la aplicación:

   ```bash
   cd <Application install directory>
   ```

1. Use el siguiente comando para crear un archivo con el nombre `magento_umask` y escriba el valor `umask` en él.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   Ahora debería tener un archivo de nombre `magento_umask` en `<Magento install dir>` con el único contenido que es el número `umask`.

1. Cierre la sesión y vuelva a iniciarla como [propietario del sistema de archivos](../prerequisites/file-system/overview.md) para aplicar los cambios.
