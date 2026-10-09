---
title: Configuración del sistema de desarrollo
description: Obtenga información sobre cómo configurar un sistema de desarrollo para la aplicación de Commerce.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '131'
ht-degree: 0%
---
# Configuración del sistema de desarrollo

Puede tener cualquier número de sistemas de desarrollo, siempre que lo siguiente sea válido para todos ellos:

- Todos ejecutan Commerce 2.2 o posterior
- Todo el código Commerce está bajo control de código fuente en el mismo repositorio que los sistemas de compilación y producción
- Cada sistema de desarrollo debe usar [modo predeterminado](../bootstrap/application-modes.md#default-mode) o [modo de desarrollador](../bootstrap/application-modes.md#developer-mode)
- Tiene la propiedad del sistema de archivos y los permisos establecidos como se describe en [Requisito previo para los sistemas de desarrollo, compilación y producción](../deployment/technical-details.md).
- Asegúrese de que todas las siguientes _excluidas_ del control de código fuente:

  - Directorio `vendor` (y subdirectorios)
  - Directorio `generated` (y subdirectorios)
  - Directorio `pub/static` (y subdirectorios)
  - `app/etc/env.php` archivo

- Asegúrese de que `app/etc/config.php` esté _incluido_ en el control de código fuente

Si usa Git, el archivo `.gitignore` proporciona la mayor parte de lo anterior. Ver la referencia [`.gitignore` &#x200B;](../reference/config-reference-gitignore.md).
