---
title: Prácticas recomendadas de implementación de contenido estático
description: Aprenda a evitar problemas con el contenido estático que no aparece en la tienda de Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Prácticas recomendadas de implementación de contenido estático

Este artículo trata sobre las prácticas recomendadas de implementación de contenido estático (SCD) en Adobe Commerce para evitar problemas en los que el contenido estático no estaría disponible en el sitio web.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

* Adobe Commerce en la infraestructura en la nube
* Adobe Commerce local

## Prácticas recomendadas

Para evitar un problema con el contenido estático no disponible en el sitio web, siga estas prácticas recomendadas para asegurarse de que el contenido estático esté configurado e implementado correctamente:

1. Asegúrese de seguir las directrices de implementación:
   * Para Adobe Commerce local (todas las versiones), consulte [Información general de implementación](../../../configuration/deployment/overview.md) en nuestra documentación para desarrolladores.
   * Para conocer Adobe Commerce sobre la infraestructura en la nube (todas las versiones), consulte [Proceso de implementación en la nube](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) y [Estrategias de implementación de contenido estático](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) en nuestra documentación para desarrolladores.

1. Para Adobe Commerce en la infraestructura en la nube (todas las versiones), asegúrese de que ece-tools está en la versión más reciente. Consulte: [Actualizar la versión de ece-tools](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) en nuestra documentación para desarrolladores.
1. Para Adobe Commerce en la infraestructura en la nube (todas las versiones), asegúrese de que el contenido estático se implementa durante la fase de compilación en lugar de durante la fase de implementación. Consulte: [Administración de configuración para configuración de tienda: rendimiento de implementación de contenido estático](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) en nuestra documentación para desarrolladores.
1. Asegúrese de que no tiene trabajos cron de larga duración y elimine cualquier proceso cron de larga duración. Los trabajos cron de larga duración pueden consumir recursos de CPU y aumentar en gran medida el tiempo de implementación.
1. Para Adobe Commerce local (todas las versiones), compruebe que la variable `php` El proceso en CLI tiene acceso a `pub/static` directorio. De lo contrario, podría encontrar un problema en el que una implementación de contenido estático no pueda escribir archivos en ese directorio. Para obtener más información: [Permisos de acceso a sistemas de archivos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) en nuestra documentación para desarrolladores.
1. Asegúrese de que `generated` El directorio no es un directorio compartido entre compilaciones; de lo contrario, las compilaciones podrían fallar aleatoriamente. Para obtener más información:
   * Adobe Commerce local (todas las versiones): [Detalles técnicos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) en nuestra documentación para desarrolladores.
   * Adobe Commerce en la infraestructura en la nube (todas las versiones): [Proceso de implementación - Fase 2: compilación](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) en nuestra documentación para desarrolladores.

1. Compruebe su estrategia de SCD. El *rápido* La estrategia es la predeterminada. Para obtener más información:
   * Adobe Commerce local (todas las versiones): [Estrategias de implementación de archivos estáticos](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) en nuestra documentación para desarrolladores.
   * Adobe Commerce en la infraestructura en la nube (todas las versiones): [Implementación de variables: SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) en nuestra documentación para desarrolladores.

## Información adicional

En nuestra documentación para desarrolladores:

* [Contenedor de contenido estático](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [Firma de contenido estático](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [Implementar variables: STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [Flujo de implementación](../../../performance/deployment-flow.md)
* [Implementación sin tiempo de inactividad](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [Optimizar implementación en la nube](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)
