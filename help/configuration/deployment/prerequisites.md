---
title: Requisitos previos para la implementación
description: Vea una lista de requisitos previos para implementar Commerce en un sistema de desarrollo, compilación o producción.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '162'
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
