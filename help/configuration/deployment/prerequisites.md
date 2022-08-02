---
title: Requisitos previos para la implementación
description: Consulte una lista de requisitos previos para implementar Commerce en un sistema de desarrollo, compilación o producción.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Requisitos previos para los sistemas de desarrollo, construcción y producción

Los permisos y la propiedad de los archivos deben ser coherentes en todos los sistemas de desarrollo, compilación y producción. Para que esto funcione, debe:

- Todos los siguientes:

   - Configure lo mismo [propietario del sistema de archivos](https://glossary.magento.com/magento-file-system-owner) nombre de usuario en todos los sistemas
   - Asegúrese de que el servidor web se ejecuta como el mismo usuario en todos los sistemas
   - Asegúrese de que el propietario del sistema de archivos está en el grupo de servidores web en todos los sistemas

- Cambie los permisos y la propiedad del sistema de archivos de Commerce en cada sistema según sea necesario mediante las siguientes directrices:

   - Desarrollo y construcción: [Establecer la propiedad y los permisos previos a la instalación (dos usuarios)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - Producción: [Propiedad y permisos comerciales en desarrollo y producción](file-system-permissions.md)

>[!INFO]
>
>Si elige este método, debe establecer los permisos y la propiedad del sistema de archivos cada vez que extraiga código del sistema de compilación (si el propietario del sistema de archivos o el usuario del servidor web son diferentes en el sistema de compilación).
