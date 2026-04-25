---
title: Release policy
description: Learn about the different types of Adobe Commerce releases.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: e0905f357c5ab84b30304eeaad00d9ae4ec0c168
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 0%

---

# Adobe Commerce release policy

Adobe Commerce uses [semantic versioning](https://semver.org/) on the individual module level (for example `magento/framework 101.1.1`), but not for the marketing version number. Por ejemplo:

- **MAJOR release**—2
- **MINOR release**—2.4
- **PATCH release**—2.4.8
   - **SECURITY patch release**—2.4.8-p1
      - Security bug fix
      - Security enhancement
- **ALPHA patch release**—2.4.8-alpha1
- **BETA patch release**—2.4.8-beta1
- **Extensibility, Infrastructure, and Services release**
- **Hotfix**
- **Individual patch**
- **Custom patch**

## MINOR release

The following guidelines apply to minor releases:

- Breaking changes are possible; code written for Adobe Commerce 2.2.x may no longer work with Adobe Commerce 2.3.x. For example, minor releases can introduce support for major system requirements and dependencies, such as PHP.
- Module versions can vary. For example, some module changes are introduced in a new patch whereas others are introduced in a minor release.
- Minor releases can include new features that may require additional work by you or your solution partner during an upgrade to ensure compatibility.
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

Las revisiones son parches que contienen correcciones de alta calidad o seguridad de impacto, como correcciones a vulnerabilidades de día cero, que afectan a muchos comerciantes. Adobe publica revisiones (según sea necesario) para las versiones de Adobe Commerce admitidas cuando surjan problemas críticos de seguridad o calidad. Las revisiones se entregan a través de la [herramienta Parches de calidad](../tools/quality-patches-tool/usage.md). Estas correcciones se incluyen en la próxima versión planificada del parche.

>[!NOTE]
>
>Las revisiones pueden contener cambios incompatibles con versiones anteriores.

## Parche individual

Los parches individuales contienen correcciones de calidad de bajo impacto para un problema específico. Estas correcciones se aplican a las versiones secundarias compatibles de Adobe Commerce. Adobe publica parches individuales según sea necesario para Adobe Commerce de acuerdo con la [Política de ciclo de vida del software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf). Se entregan a través de la [herramienta Parches de calidad](../tools/quality-patches-tool/usage.md).

>[!NOTE]
>
>Los parches individuales no contienen cambios incompatibles con versiones anteriores.

## Parche personalizado

Creado por personal que no es de Adobe para solucionar un problema o modificar el código de Adobe Commerce por varios motivos.

<!-- Last updated from includes: 2026-04-20 10:12:04 -->
