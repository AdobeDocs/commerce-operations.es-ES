---
title: Prácticas recomendadas para la implementación de contenido estático
description: Aprenda a evitar problemas con el contenido estático que no aparece en su tienda de Adobe Commerce o Magento Open Source.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---


# Prácticas recomendadas para la implementación de contenido estático

Este artículo trata sobre las prácticas recomendadas de implementación de contenido estático (SCD) en Adobe Commerce para ayudar a evitar problemas en los que el contenido estático no estaría disponible en el sitio web.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

* Adobe Commerce en infraestructura en la nube
* Adobe Commerce local
* Magento Open Source

## Prácticas recomendadas

Para evitar un problema con contenido estático que no está disponible en el sitio web, siga estas prácticas recomendadas para asegurarse de que el contenido estático esté configurado y se implemente correctamente:

1. Asegúrese de seguir las directrices de implementación:
   * Para Adobe Commerce local y Magento Open Source (todas las versiones), consulte [Información general sobre la implementación](../../../configuration/deployment/overview.md) en nuestra documentación para desarrolladores.
   * Para Adobe Commerce sobre la infraestructura de nube (todas las versiones), consulte [Proceso de implementación en la nube](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) y [Estrategias de implementación de contenido estático](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) en nuestra documentación para desarrolladores.

1. Para Adobe Commerce en infraestructura de nube (todas las versiones), asegúrese de que ceda herramientas en la versión más reciente. Consulte: [Actualizar la versión de las herramientas de lanzamiento](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) en nuestra documentación para desarrolladores.
1. Para Adobe Commerce en infraestructura de nube (todas las versiones), asegúrese de que el contenido estático se implementa durante la fase de compilación en lugar de durante la fase de implementación. Consulte: [Administración de configuración para ajustes de tienda: rendimiento de implementación de contenido estático](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) en nuestra documentación para desarrolladores.
1. Asegúrese de que no tiene trabajos cron de larga duración y de que elimina cualquier proceso cron de larga duración. Los trabajos cron de larga duración pueden absorber recursos de CPU y aumentar considerablemente el tiempo de implementación.
1. Para Adobe Commerce local y Magento Open Source (todas las versiones), compruebe que la variable `php` proceso en CLI tiene acceso a `pub/static` directorio. De lo contrario, podría encontrarse con un problema en el que una implementación de contenido estático no podría escribir archivos en ese directorio. Para obtener más información: [Permisos de acceso de sistemas de archivos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) en nuestra documentación para desarrolladores.
1. Asegúrese de que la variable `generated` El directorio no es un directorio compartido entre compilaciones; de lo contrario, las compilaciones podrían fallar aleatoriamente. Para obtener más información:
   * Adobe Commerce local y Magento Open Source (todas las versiones): [Detalles técnicos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) en nuestra documentación para desarrolladores.
   * Adobe Commerce en infraestructura de nube (todas las versiones): [Proceso de implementación - Fase 2: versión](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) en nuestra documentación para desarrolladores.

1. Compruebe su estrategia de SCD. La variable *quick* es la estrategia predeterminada. Para obtener más información:
   * Adobe Commerce local y Magento Open Source (todas las versiones): [Estrategias de implementación de archivos estáticos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) en nuestra documentación para desarrolladores.
   * Adobe Commerce en infraestructura de nube (todas las versiones): [Implementar variables: SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) en nuestra documentación para desarrolladores.

## Información adicional

En nuestra documentación para desarrolladores:

* [Contenedor de contenido estático](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [Firma de contenido estático](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [Implementar variables: STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [Flujo de implementación](../../../performance/deployment-flow.md)
* [Implementación sin downtime](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [Optimización de la implementación en la nube](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)

