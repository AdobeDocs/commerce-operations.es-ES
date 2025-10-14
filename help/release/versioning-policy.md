---
title: Directiva de versión
description: Obtenga información acerca de los distintos tipos de versiones de Adobe Commerce.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: bf7049ad5b805397f823e7e4cb430e9ecca5965e
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---

# directiva de versión de Adobe Commerce

Adobe Commerce usa [versiones semánticas](https://semver.org/) en el nivel de módulo individual (por ejemplo `magento/framework 101.1.1`), pero no para el número de versión de marketing. Por ejemplo:

- **Versión principal**—2
- **Versión menor**—2.4
- **Versión de PATCH**—2.4.8
   - **Versión del parche de SEGURIDAD**—2.4.8-p1
      - Corrección de errores de seguridad
      - Mejora de seguridad
- **Versión de parche de ALPHA**—2.4.8-alpha1
- **Versión de parche de BETA**—2.4.8-beta1
- **Extensibilidad, infraestructura y servicios**
- **Revisión**
- **Parche individual**
- **Parche personalizado**

## Versión secundaria

Las siguientes directrices se aplican a versiones secundarias:

- Es posible que se produzcan cambios importantes; es posible que el código escrito para Adobe Commerce 2.2.x ya no funcione con Adobe Commerce 2.3.x. Por ejemplo, las versiones menores pueden introducir compatibilidad con los principales requisitos y dependencias del sistema, como PHP.
- Las versiones de los módulos pueden variar. Por ejemplo, algunos cambios de módulo se introducen en un nuevo parche, mientras que otros se introducen en una versión secundaria.
- Las versiones menores pueden incluir nuevas funciones que pueden requerir un trabajo adicional por parte suya o de su socio de soluciones durante una actualización para garantizar la compatibilidad.
- Las versiones menores pueden incluir correcciones para problemas de seguridad y calidad.

## Versión de PATCH

Las versiones de parches se centran principalmente en ofrecer correcciones de calidad de alta prioridad, seguridad, rendimiento y conformidad para ayudarle a mantener el rendimiento de sus sitios en su punto máximo.

Las siguientes directrices se aplican a las versiones de parches:

- La última versión secundaria admitida recibe correcciones y mejoras de calidad funcional completas.
- Se evitan los cambios que podrían interrumpir las extensiones o la compatibilidad del código. Por ejemplo, el código escrito para la versión 2.2.0 debería seguir funcionando en la versión 2.2.7.
- Excepcionalmente, se pueden lanzar cambios importantes o parches o revisiones adicionales para solucionar problemas de seguridad o cumplimiento y problemas de calidad de alto impacto. En el nivel de módulo, estos cambios son principalmente de nivel PATCH; a veces de nivel MINOR.

### Versión del parche de SEGURIDAD

{{$include /help/_includes/release-notes/security-patch-overview.md}}

## Versión del parche de Alpha

Las versiones anteriores a Beta de las funciones de Adobe Commerce se ponen a disposición de todos los clientes de Adobe Commerce y socios de Adobe. Las versiones de Alpha están pensadas para recibir comentarios anticipados y evaluar las funciones que aún están en desarrollo. Estas versiones proporcionan una oportunidad para realizar pruebas tempranas y planificar la integración antes de las versiones de Beta y General Availability.

Las versiones de Alpha pueden estar incompletas y es probable que contengan defectos. Se proporcionan &quot;TAL CUAL&quot; sin garantía de ningún tipo. Adobe no tiene obligación de mantener, corregir, actualizar, cambiar, modificar o dar otro tipo de soporte (a través de los servicios de soporte de Adobe o de otro modo) a las versiones de Alpha. Los clientes no deben confiar en el funcionamiento o el rendimiento correctos de las versiones de Alpha ni de la documentación o los materiales adjuntos. El uso de las versiones de Alpha es totalmente bajo el propio riesgo del cliente.

## Versión del parche de Beta

Versiones de disponibilidad generales previas de las funciones de Adobe Commerce se ponen a disposición de todos los clientes de Adobe Commerce y socios de Adobe. Permite un tiempo adicional antes de la disponibilidad general para revisar el código y los componentes afectados.

Las versiones de Beta pueden contener defectos y se proporcionan &quot;TAL CUAL&quot; sin garantía de ningún tipo. Adobe no tiene obligación de mantener, corregir, actualizar, cambiar, modificar o dar otro tipo de soporte (a través de los servicios de soporte de Adobe o de otro modo) a las versiones de Beta. Los clientes no deben confiar en el funcionamiento o el rendimiento correctos de las versiones de Beta ni de la documentación o los materiales adjuntos. Por lo tanto, cualquier uso de las Versiones de Beta es bajo el propio riesgo del cliente.

## Revisión

Las revisiones son parches que contienen correcciones de alta calidad o seguridad de impacto, como correcciones a vulnerabilidades de día cero, que afectan a muchos comerciantes. Adobe publica revisiones (según sea necesario) para las versiones de Adobe Commerce admitidas cuando surjan problemas críticos de seguridad o calidad. Las revisiones se han publicado en la [sección Problemas conocidos](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) de la Base de conocimiento. Estas correcciones se incluyen en la próxima versión planificada del parche.

>[!NOTE]
>
>Las revisiones pueden contener cambios incompatibles con versiones anteriores.

## Parche individual

Los parches individuales contienen correcciones de calidad de bajo impacto para un problema específico. Estas correcciones se aplican a las versiones secundarias compatibles de Adobe Commerce. Adobe publica parches individuales según sea necesario para Adobe Commerce de acuerdo con la [Política de ciclo de vida del software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Los parches individuales no contienen cambios incompatibles con versiones anteriores.

## Correcciones de seguridad aisladas

Los parches aislados son correcciones de seguridad no acumulativas publicadas independientemente de un parche de seguridad completo para permitir una implementación más rápida. Cada corrección de seguridad aislada soluciona un problema de seguridad específico y se incluye en la última revisión de seguridad o en una revisión de seguridad completa prevista. Los detalles sobre el problema se proporcionan en el boletín de seguridad relacionado, que vincula a un artículo de la Base de conocimiento (KB) que contiene los detalles de la corrección, cómo aplicarla e información adicional.

Consulta el [Centro de seguridad](https://helpx.adobe.com/security/products/magento.html) para ver las últimas actualizaciones de seguridad disponibles para Adobe Commerce.

## Parche personalizado

Creado por personal que no es de Adobe para solucionar un problema o modificar el código de Adobe Commerce por varios motivos. Los parches personalizados se entregan a través de la [Herramienta de parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).

<!-- Last updated from includes: 2025-10-09 22:53:22 -->
