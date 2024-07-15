---
title: Requisitos previos para la implementación
description: Vea una lista de requisitos previos para implementar Commerce en un sistema de desarrollo, compilación o producción.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Requisitos previos para los sistemas de desarrollo, compilación y producción

Los permisos y la propiedad de los archivos deben ser coherentes en los sistemas de desarrollo, compilación y producción. Para que esto funcione, debe:

- Todo lo siguiente:

   - Configure el mismo nombre de usuario del propietario del sistema de archivos en todos los sistemas
   - Asegúrese de que el servidor web se ejecuta como el mismo usuario en todos los sistemas
   - Asegúrese de que el propietario del sistema de archivos está en el grupo de servidores web de todos los sistemas

- Cambie los permisos y la propiedad del sistema de archivos Commerce en cada sistema según sea necesario siguiendo las siguientes directrices:

   - Desarrollo y compilación: [Establezca la propiedad y los permisos previos a la instalación (dos usuarios)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - Producción: [Propiedad de Commerce y permisos en desarrollo y producción](file-system-permissions.md)

>[!INFO]
>
>Si elige este método, debe establecer los permisos y la propiedad del sistema de archivos cada vez que extraiga código del sistema de generación (si el propietario del sistema de archivos o el usuario del servidor web son diferentes en el sistema de generación).
