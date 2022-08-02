---
title: Configuración del sistema de desarrollo
description: Aprenda a configurar un sistema de desarrollo para la aplicación Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# Configuración del sistema de desarrollo

Puede tener cualquier número de sistemas de desarrollo, siempre que lo siguiente sea cierto para todos ellos:

- Todos ejecutan Commerce 2.2 o posterior
- Todo el código de comercio está bajo control de código fuente en el mismo repositorio que los sistemas de construcción y producción
- Cada sistema de desarrollo debe utilizar: [modo predeterminado](../bootstrap/application-modes.md#default-mode) o [modo de desarrollador](../bootstrap/application-modes.md#developer-mode)
- Tiene establecidos permisos y propiedad del sistema de archivos como se describe en [Requisito previo para los sistemas de desarrollo, construcción y producción](../deployment/technical-details.md).
- Asegúrese de que todos los elementos siguientes sean: _Excluido_ desde control de código fuente:

   - `vendor` directorio (y subdirectorios)
   - `generated` directorio (y subdirectorios)
   - `pub/static` directorio (y subdirectorios)
   - `app/etc/env.php` file

- Asegúrese de `app/etc/config.php` es _included_ en control de código fuente

Si utiliza Git, la variable `.gitignore` proporciona la mayor parte de lo anterior. Consulte la [`.gitignore` referencia](../reference/config-reference-gitignore.md).
