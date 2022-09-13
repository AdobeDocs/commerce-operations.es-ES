---
title: Establecer una máscara (opcional)
description: Mejore la postura de seguridad de su instalación local de Adobe Commerce o Magento Open Source restringiendo los permisos del sistema de archivos.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Establecer una máscara (opcional)

El grupo de servidores web debe tener permisos de escritura para ciertos directorios del sistema de archivos; sin embargo, es posible que desee una seguridad más estricta, especialmente en producción. Proporcionamos flexibilidad para que usted restrinja aún más esos permisos mediante una [máscara](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

Nuestra solución es permitirle, opcionalmente, crear un archivo llamado `magento_umask` en el directorio raíz de la aplicación que restringe los permisos para el grupo de servidores web y para todos los demás.

>[!NOTE]
>
>Se recomienda cambiar la máscara solo en un sistema de alojamiento compartido o de un usuario. Si tiene un servidor de aplicaciones privado, el grupo debe tener acceso de escritura al sistema de archivos; la máscara elimina el acceso de escritura del grupo.

La máscara predeterminada (sin `magento_umask` specified) is `002`, lo que significa que:

* 775 para directorios, lo que significa control total por parte del usuario, control total por parte del grupo, y permite a todos recorrer el directorio. Estos permisos suelen ser necesarios para proveedores de alojamiento compartidos.

* 664 para archivos, es decir, que el usuario pueda escribir, que el grupo pueda escribirlo y que sea de solo lectura para todos los demás

Una sugerencia común es utilizar un valor de `022` en el `magento_umask` , lo que significa que:

* 755 para directorios: control total para el usuario, y todos los demás pueden recorrer directorios.
* 644 para archivos: permisos de lectura y escritura para el usuario y de solo lectura para todos los demás.

Para configurar `magento_umask`:

1. En un terminal de línea de comandos, inicie sesión en el servidor de aplicaciones como [propietario del sistema de archivos](../prerequisites/file-system/overview.md).
1. Vaya al directorio de instalación de la aplicación:

   ```bash
   cd <Application install directory>
   ```

1. Utilice el siguiente comando para crear un archivo denominado `magento_umask` y escriba el `umask` para él.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   Ahora debería tener un archivo llamado `magento_umask` en el `<Magento install dir>` con el único contenido que es la variable `umask` número.

1. Cierre la sesión y vuelva a iniciarla como [propietario del sistema de archivos](../prerequisites/file-system/overview.md) para aplicar los cambios.
