---
title: Notas de la versión [!DNL Commerce Version Tool]
description: Obtenga información acerca de  [!DNL Commerce Version Tool] versiones de, incluidos los nuevos informes de estado de parches, el estado de protección CVE, la salida CSV y el comportamiento de la caché.
feature: Release Notes
TQID: 'https://experienceleague.adobe.com/38I3U5y9rmurP5gVhalfUq7DlcUb-JpF5eUam1nwEyk'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 180
ht-degree: 2%

---

# [!DNL Commerce Version Tool] notas de la versión

Estas notas de la versión describen actualizaciones para [!DNL Commerce Version Tool] ([!DNL CVT]).

## Versión 1.0.0: junio de 2026 {#version-1-0-0}

### Nuevas funciones

- **Informes de estado de parches**: Informes sobre los parches de seguridad mensuales de Adobe Commerce que se han aplicado, no se han encontrado o no se han podido clasificar para una instalación de Adobe Commerce.
- **Estado de protección CVE** - Asigna los resultados de la revisión a los valores de estado de protección por CVE: `PROTECTED`, `VULNERABLE`, `UNKNOWN` y `NOT_APPLICABLE`.
- **Compatibilidad con varios componentes**: detecta los componentes de Adobe Commerce instalados de `composer.lock`, incluidos Adobe Commerce de empresa a empresa (B2B), Adobe Commerce Page Builder, Adobe Commerce Inventory y otros componentes representados en el archivo de registro de parches.
- **Salida JSON y CSV**: proporciona salida JSON de forma predeterminada para el consumo mediante programación y salida CSV para hojas de cálculo, escáneres, tableros y herramientas de conformidad.
- **Comportamiento de caché sin conexión** - Almacena en caché el archivo de registro de parches localmente después de cada recuperación correcta. Si el Registro remoto no está disponible, la herramienta [!DNL CVT] puede utilizar el Registro almacenado en caché con una advertencia.
- **Envío en paquete**: se envía dentro de los archivos mensuales de parches de seguridad de Adobe Commerce. Al aplicar la revisión se instala [!DNL CVT] en `vendor/bin/patch-status` sin ningún paso de instalación aparte.

## Temas relacionados

- [Introducción](intro.md)
- [Generación de un informe de estado del parche](generate-report.md)
- [Resolución de problemas](troubleshooting.md)
