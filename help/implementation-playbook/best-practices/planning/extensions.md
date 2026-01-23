---
title: Prácticas recomendadas sobre extensiones
description: Obtenga información sobre cómo evitar problemas de rendimiento causados por extensiones de Adobe Commerce de terceros.
role: Admin
feature: Best Practices, Extensions
exl-id: 95d2c7bf-fd2f-4c98-8293-96d69b86341f
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---

# Prácticas recomendadas sobre extensiones

Las extensiones de terceros de Adobe Commerce (módulos) pueden causar varios problemas que pueden afectar negativamente al rendimiento de la tienda. Puede evitar estos problemas siguiendo estas prácticas recomendadas:

- Desarrolle sus integraciones y personalizaciones de Commerce usando [extensibilidad fuera de proceso](https://developer.adobe.com/commerce/extensibility/) siempre que sea posible para facilitar el mantenimiento y la actualización.
- Descargue y compre extensiones de terceros de una fuente de confianza, como [Commerce Marketplace](https://commercemarketplace.adobe.com//extensions.html).
- Actualice todas las extensiones de terceros a la versión más reciente.
- Si no puede mantener actualizadas las extensiones de terceros, considere la posibilidad de utilizar diferentes extensiones.
- Cuando planee una actualización a una nueva versión de Adobe Commerce, compruebe que las extensiones de terceros instaladas sean compatibles con la nueva versión y actualice las extensiones si es necesario.

>[!NOTE]
>
> Todas las extensiones disponibles en Adobe Commerce Marketplace son necesarias para mantener la compatibilidad con las nuevas versiones de Commerce. Consulte [Compatibilidad de la versión](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases/).

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Más información

- [Prácticas recomendadas para planificar las actualizaciones](../../../upgrade/prepare/best-practices.md)
- Uso de extensiones de terceros con Adobe Commerce en infraestructuras en la nube
   - [Tecnologías y requisitos: desarrollo y pruebas](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-devtest)
   - [¿Por qué probar completamente en integración y ensayo?](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/launch/overview#why-test-fully-in-integration-staging-and-production)
