---
title: '[!DNL Commerce Version Tool]'
description: Obtenga información acerca de  [!DNL Commerce Version Tool] for Adobe Commerce y use el estado de proveedor/ubicación/parche para comprobar el estado mensual del parche de seguridad.
TQID: 'https://experienceleague.adobe.com/9lDQtCrcCSIFjt3jUJkqCo-rMlIhhy3tPTtPyT4wt1Q'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 586
ht-degree: 0%

---

# [!DNL Commerce Version Tool]

Los parches de seguridad mensuales para Adobe Commerce no son acumulativos y deben aplicarse en secuencia. [!DNL Commerce Version Tool] ([!DNL CVT]) ayuda a los comerciantes a comprobar la cobertura de los parches informando sobre los parches de seguridad mensuales que están instalados, los parches que faltan y los CVE contra los que está protegida la instalación.

>[!IMPORTANT]
>
>La herramienta [!DNL CVT] es meramente informativa. No aplica parches, revierte parches ni modifica los archivos de origen de Adobe Commerce. Puede escribir archivos de caché, archivos temporales de ejecución en seco y entradas de registro de auditoría para admitir la creación de informes de estado de parche.

## Información general de herramientas

La herramienta [!DNL CVT] es un ejecutable independiente incluido con cada parche de seguridad de Adobe Commerce mensual. Cuando la revisión se aplica a una instalación de Adobe Commerce, la herramienta se instala en `vendor/bin/patch-status`. Requiere PHP 8.1 o posterior y el sistema binario `patch`. No requiere paquetes Composer, extensiones PHP no estándar, bootstrap de Adobe Commerce o un paso de instalación separado.

La herramienta [!DNL CVT] puede ayudarle a:

- Detectar parches de seguridad aplicados en una instalación compatible de Adobe Commerce.
- Identifique los parches que faltan en una secuencia mensual de parches de seguridad aislados.
- Informe del estado de seguridad protegido, vulnerable o desconocido para los registros de Vulnerabilidades y exposiciones comunes (CVE) relacionados con parches.
- Produzca resultados legibles por el equipo, como JSON o CSV, para escáneres, tableros e informes de conformidad.
- Detectar estado de parche para plataformas y componentes compatibles.

## Disponibilidad

La herramienta [!DNL CVT] admite la creación de informes de estado de revisión para las siguientes plataformas y componentes cuando Adobe proporciona metadatos de revisión para la versión instalada en el archivo de registro de revisión.

| Plataforma o componente | Disponibilidad |
| --- | --- |
| Adobe Commerce local | Admitido |
| [!DNL Magento Open Source] | Admitido |
| Adobe Commerce de empresa a empresa (B2B) | Admitido tras la instalación |
| Adobe Commerce Page Builder | Admitido tras la instalación |
| Inventario de Adobe Commerce | Admitido tras la instalación |
| Se detectaron componentes adicionales en `composer.lock` | Compatible cuando se representa en el archivo de registro de parches |

{style="table-layout:auto"}

## Casos de uso comunes

Utilice la herramienta [!DNL CVT] cuando necesite:

- Compruebe si una instalación de Adobe Commerce incluye los parches aislados de seguridad necesarios.
- Confirme si los conjuntos de parches omitidos o incompletos dejan la cobertura de CVE incompleta.
- Genere la salida JSON o CSV para informes internos o análisis automatizado.
- Proporcione información sobre el estado de los parches antes de abrir una solicitud de asistencia o planificar la corrección.

## Directrices para el uso de resultados

Trate el resultado de la herramienta [!DNL CVT] como datos de detección compatibles con la planificación de parches y la revisión de seguridad.

Siga estas directrices:

- Ejecute la herramienta [!DNL CVT] con una instalación de Adobe Commerce estable y compatible.
- Revise los parches que faltan y los desconocidos antes de realizar notificaciones de estado de seguridad.
- Conservar la salida JSON o CSV para facilitar la auditoría y la automatización.
- Tratar la salida de exploración como datos operativos relevantes para la seguridad.
- Comparta únicamente los detalles necesarios para la asistencia o la corrección.

## Detección de parches

La herramienta [!DNL CVT] ejecuta la detección en dos pasos fijos. Ambos pasos se ejecutan siempre que se genera un informe de estado de parche.

- **Detección del compositor:** La herramienta lee el archivo `composer.lock` para determinar la versión base de [!DNL Adobe Commerce] y las áreas de componentes instaladas. Si la herramienta no puede detectar una versión base, existe con el código `1`.

- **Detección de ejecución en seco:** Para cada parche aplicable, la herramienta utiliza una comprobación de ejecución en seco de los cambios del parche para determinar si el parche ya se ha aplicado, si no se ha aplicado o si se desconoce el estado del parche. La herramienta gestiona las dependencias del parche durante esta comprobación para que los resultados reflejen la versión del componente instalada.

El informe solo incluye parches que se aplican a los componentes de instalación detectados e instalados. Si la herramienta no puede confirmar si hay un parche aplicable, clasifica el parche como desconocido.

## Empezar a usar [!DNL CVT]

Utilice estos temas para generar, solucionar problemas y realizar un seguimiento de los informes de estado de los parches:

- [Genere un informe de estado de revisión](generate-report.md) para ejecutar la herramienta [!DNL CVT], revisar las opciones de comandos e interpretar los resultados del informe.
- [[!DNL Commerce Version Tool] solución de problemas](troubleshooting.md) para resolver resultados inesperados o errores de comandos.
- [[!DNL Commerce Version Tool] notas de la versión](release-notes.md) para revisar las actualizaciones de la versión.
