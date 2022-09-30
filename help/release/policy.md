---
title: Política de versiones
description: Obtenga información sobre los distintos tipos de versiones de Adobe Commerce, como menor, parche, parche de seguridad, función, revisión, parche individual y parche personalizado.
source-git-commit: 79f36e3728e6bc436e8093bd4051143a48e681d6
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 0%

---


# Política de versiones de Adobe Commerce

Uso de Adobe Commerce y Magento Open Source [versionado semántico](https://semver.org/) en el nivel de módulo individual (por ejemplo `magento/framework 101.1.1`), pero no para el número de versión de marketing. Por ejemplo:

- **Versión principal**—2
- **Versión menor**—2,4
- **versión del PATCH**—2.4.1
   - **Lanzamiento del parche de SEGURIDAD**—2.4.1-p1
      - Corrección de errores de seguridad
      - Mejora de la seguridad
- **Versión de funciones**
- **Hotfix**
- **Parche individual**
- **Parche personalizado**

## Versión menor

Las siguientes directrices se aplican a versiones menores:

- Es posible que se produzcan cambios bruscos; es posible que el código escrito para Adobe Commerce 2.2.x ya no funcione con Adobe Commerce 2.3.x. Por ejemplo, las versiones menores pueden introducir compatibilidad con los principales requisitos y dependencias del sistema, como PHP.
- Las versiones de los módulos pueden variar. Por ejemplo, algunos cambios de módulo se introducen en un nuevo parche, mientras que otros se introducen en una versión menor.
- Las versiones menores pueden incluir nuevas funciones que pueden requerir un trabajo adicional por su parte o su socio de soluciones durante la actualización para garantizar la compatibilidad.
- Las versiones menores pueden incluir correcciones para problemas de seguridad y calidad.

## versión del PATCH

Las versiones de parches se centran principalmente en ofrecer correcciones de seguridad, rendimiento, cumplimiento de normas y calidad de alta prioridad para ayudarle a mantener el rendimiento de sus sitios en su punto más alto.

Las siguientes directrices se aplican a las versiones de parches:

- La última versión menor admitida recibe correcciones y mejoras de calidad funcionales completas.
- Se evitan los cambios que podrían dañar las extensiones o la compatibilidad del código. Por ejemplo, el código escrito para la versión 2.2.0 debería seguir funcionando en la versión 2.2.7.
- Excepcionalmente, se pueden publicar cambios o parches o revisiones adicionales para solucionar problemas de seguridad o cumplimiento y problemas de calidad de alto impacto. A nivel de módulo, se trata principalmente de cambios a nivel de PATCH; a veces, cambios de nivel MINOR.

## Lanzamiento del parche de SEGURIDAD

**Corrección de errores de seguridad**: Un cambio en el código de software que resuelve un problema de seguridad identificado y ofrece los resultados esperados en un área de producto afectada. Estas correcciones son generalmente compatibles con versiones anteriores.

**Mejora de seguridad**: Una mejora de software o un cambio de configuración para mejorar proactivamente la seguridad dentro de la aplicación. Estas mejoras de seguridad ayudan a resolver los riesgos de seguridad que afectan a la postura de seguridad de la aplicación Adobe Commerce, pero que pueden ser incompatibles con versiones anteriores.

Con las versiones de parches de seguridad, puede mantener su sitio más seguro sin aplicar correcciones y mejoras de calidad adicionales que se incluyen en una versión trimestral completa de parches. Las versiones de parches de seguridad se agregan con &quot;-pN&quot;, donde N es la versión de parches incremental que comienza con 1 (por ejemplo, 2.3.5-p1). Las versiones de parches de seguridad también pueden incluir revisiones necesarias para solucionar problemas críticos que afectan a la aplicación Adobe Commerce.

Cada versión de parches de seguridad se basa en la versión anterior de parches completos. Contiene correcciones de calidad y seguridad de revisiones anteriores y correcciones de seguridad creadas entre la versión anterior del parche completo y la versión del parche de seguridad.

Con el anuncio de nuestra [nueva estrategia de versión y política de ciclo vital actualizada](https://business.adobe.com/blog/how-to/accelerating-innovation-through-simplified-release-strategy) (16/9/2021), nuestras versiones de parches de seguridad se diferencian según si son aplicables a la última versión menor admitida o a una parte de una línea de versiones menor anterior aún admitida:

- **Versiones de parches de seguridad para la última versión menor admitida**:

   - La versión de parches de seguridad para la última versión menor admitida (actualmente Adobe Commerce 2.4) incluye:

      - Correcciones de errores de seguridad que se han creado desde la versión anterior del parche completo.

      - Estas versiones de parches de seguridad también pueden incluir revisiones necesarias para solucionar problemas críticos que pueden afectar a la aplicación Adobe Commerce.
   - La versión de parches de seguridad para la última versión menor admitida (actualmente Adobe Commerce 2.4) no suele incluir mejoras de seguridad. En su lugar, se incluyen en la versión completa del parche para la última versión menor compatible.


- **Versiones de parches de seguridad para versiones menores anteriores compatibles**:

   - La versión del parche de seguridad para una versión anterior menor que aún se admite (actualmente Adobe Commerce 2.3) incluye:

      - Correcciones de errores de seguridad que se han creado desde la versión anterior del parche o del parche de seguridad, y nuevas mejoras de seguridad.

      - Estas versiones de parches de seguridad también pueden incluir revisiones necesarias para solucionar problemas críticos que afectan a la aplicación Adobe Commerce.

      |  | Error de seguridad | Mejora de seguridad |
      |--------------------------------------------------------------------------------|--------------|----------------------|
      | Versiones de parches de seguridad para la última versión menor admitida (actualmente 2.4) | X |  |
      | Versiones de parches de seguridad para versiones menores anteriores y compatibles (actualmente 2.3) | X | X |


Para obtener información general sobre las versiones de seguridad, consulte [Presentación de la nueva versión de parches de solo seguridad](https://community.magento.com:443/t5/Magento-DevBlog/Introducing-the-New-Security-Patch-Release/ba-p/141287). Para obtener instrucciones sobre cómo descargar y aplicar parches de seguridad, consulte [Instalación rápida](../installation/composer.md).

## Versión de funciones

Las versiones de funciones contienen nuevas funciones y actualizaciones de funciones que se proporcionan como servicios independientes, independientemente de las versiones de parches. Algunos ejemplos son servicios como Recommendations de productos y Live Search, módulos independientes como PWA Studio y Inventory management (MSI) y actualizaciones de nuestros servicios e infraestructuras en la nube.

## Hotfix

Las revisiones son parches que contienen correcciones de calidad o seguridad de alto impacto, como correcciones a vulnerabilidades de cero días que afectan a muchos comerciantes. Adobe publica revisiones para versiones de Adobe Commerce que aún son compatibles y se ven afectadas por problemas críticos de seguridad o calidad, según sea necesario. Las revisiones se publican en el [Sección Problemas conocidos](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) de nuestra Base de Conocimientos. Estas correcciones se incluyen en la siguiente versión de parches planificada.

>[!NOTE]
>
>Las revisiones pueden contener cambios incompatibles con versiones anteriores.

## Parche individual

Los parches individuales contienen correcciones de calidad de bajo impacto para un problema específico. Estas correcciones se aplican a las versiones secundarias compatibles de Adobe Commerce. El Adobe libera parches individuales según sea necesario para Adobe Commerce de acuerdo con nuestra [Política de ciclo de vida del software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Los parches individuales no contienen cambios incompatibles con versiones anteriores.

## Parche personalizado

Creado por personal que no es de Adobe para solucionar un problema o modificar el código de Adobe Commerce por varios motivos. Los parches personalizados se entregan a través de la variable [Herramienta Parches de calidad](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## Temas relacionados

- [Planificación y presupuestos para ciclos de actualización de comercio](https://magento.com/sites/default/files8/2019-08/Magento-Release-Cycle-Infosheet_Aug_2019.pdf)
- [Versiones](https://developer.adobe.com/commerce/php/development/versioning/)
- [Próximas versiones](schedule.md)
- [Política de ciclo de vida del software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
