---
title: Configuración del sistema de desarrollo
description: Aprenda a configurar un sistema de desarrollo para la aplicación de Commerce.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Configuración del sistema de desarrollo

Puede tener cualquier número de sistemas de desarrollo, siempre que lo siguiente sea válido para todos ellos:

- Todos ejecutan Commerce 2.2 o posterior
- Todo el código de Commerce está bajo control de código fuente en el mismo repositorio que los sistemas de compilación y producción
- Cada sistema de desarrollo debe utilizar [modo predeterminado](../bootstrap/application-modes.md#default-mode) o [modo de desarrollador](../bootstrap/application-modes.md#developer-mode)
- Tiene la propiedad del sistema de archivos y los permisos establecidos, tal como se describe en [Requisito previo para los sistemas de desarrollo, compilación y producción](../deployment/technical-details.md).
- Asegúrese de que todas las opciones siguientes son _excluido_ desde el control de código fuente:

   - `vendor` directorio (y subdirectorios)
   - `generated` directorio (y subdirectorios)
   - `pub/static` directorio (y subdirectorios)
   - `app/etc/env.php` archivo

- Asegúrese de `app/etc/config.php` es _incluido_ en el control de código fuente

Si utiliza Git, la variable `.gitignore` proporciona la mayoría de lo anterior. Consulte la [`.gitignore` reference](../reference/config-reference-gitignore.md).
