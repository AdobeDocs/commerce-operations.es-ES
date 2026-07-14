---
title: Generación de un Informe de Estado de Parches
description: Aprenda a utilizar  [!DNL Commerce Version Tool]  para generar informes de estado de parches de Adobe Commerce en formato JSON o CSV.
TQID: 'https://experienceleague.adobe.com/-lC-20YMpbTM3tTZjbBO5zD5gb9n7cRah5Ycy8wQoyw'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: cb0391ae368b53a795535f3adb636628a339b963
workflow-type: tm+mt
source-wordcount: 590
ht-degree: 2%

---

# Generación de un informe de estado del parche

Use [!DNL Commerce Version Tool] ([!DNL CVT]) para generar un informe de estado de revisión para una instalación de Adobe Commerce. El informe identifica los parches de seguridad mensuales aplicados, no presentes y desconocidos, y devuelve la salida JSON de forma predeterminada.

## Requisitos previos

Antes de ejecutar [!DNL CVT], confirme lo siguiente:

- La instalación de destino utiliza una versión y una edición de Adobe Commerce compatibles.
- `composer.lock` está presente y coincide con el entorno que desea inspeccionar.
- PHP y el sistema binario `patch` están disponibles.
- Puede leer los archivos del proyecto desde el entorno donde ejecuta el comando.
- La herramienta puede escribir en `var/patch_metadata/` y `var/log/` si desea archivos de caché y entradas de registro de auditoría.
- Las credenciales están disponibles a través de `COMPOSER_AUTH` o `auth.json` si se aplican parches con derechos asignados a la instalación.

La herramienta [!DNL CVT] comprueba `COMPOSER_AUTH`, el proyecto de Adobe Commerce `auth.json` y el Compositor global `auth.json` para ver si hay credenciales de revisión con acceso a derechos.

## Generación del informe

Desde la raíz del proyecto de Adobe Commerce, ejecute:

```bash
php vendor/bin/patch-status
```

Para comprobar una instalación de Adobe Commerce diferente, use la opción `--root`:

```bash
php vendor/bin/patch-status --root=/path/to/commerce
```

## Opciones de comando

JSON es el formato de salida predeterminado. La salida CSV es compatible con escáneres, tableros e informes de conformidad.

| Opción | Descripción |
| --- | --- |
| `--root=PATH` | Especifica la ruta de acceso a la raíz de instalación de Adobe Commerce. El valor predeterminado es el directorio actual. |
| `--format=json\|csv` | Establece el formato de salida. El valor predeterminado es `json`. |
| `--no-cache` | Omite las memorias caché del Registro y de diferencias de parches, fuerza nuevas recuperaciones remotas y sale con un error si el Registro remoto no está disponible. |
| `--version`, `-V` | Imprime la versión de la herramienta. |
| `--help`, `-h` | Imprime el mensaje de ayuda. |

{style="table-layout:auto"}

## Revisar la salida JSON y CSV

El siguiente ejemplo muestra la salida JSON predeterminada.

```bash
php vendor/bin/patch-status
```

```json
{
  "base_version": "2.4.7-p9",
  "installed_components": {
    "CE": "2.4.7-p9",
    "EE": "2.4.7-p9",
    "B2B": "1.5.2-p5"
  },
  "applied_patches": [
    "247p9-2026-05-001-CE",
    "247p9-2026-05-001-EE"
  ],
  "missing_patches": [
    "247p9-2026-06-001-CE",
    "247p9-2026-06-001-EE"
  ],
  "unknown_patches": [],
  "vulnerability_status": {
    "CVE-2026-12354": { "status": "PROTECTED" },
    "CVE-2026-67890": { "status": "VULNERABLE" }
  },
  "registry_source": "remote",
  "warnings": []
}
```

Para generar la salida CSV, utilice la opción `--format=csv`:

```bash
php vendor/bin/patch-status --format=csv
```

La salida CSV produce una fila por CVE y es adecuada para hojas de cálculo, escáneres, tableros y herramientas de conformidad.

## Comprender los resultados del informe

Revise los parches que faltan y los desconocidos antes de realizar notificaciones de estado de seguridad.

### Valores de estado de parche

El informe de estado del parche agrupa los resultados del parche por los siguientes valores:

| Estado del parche | Significado |
| --- | --- |
| Aplicado | La herramienta [!DNL CVT] detecta el parche de seguridad mensual en la base de código de Adobe Commerce. |
| Falta | La revisión se aplica a la versión o al componente de Adobe Commerce instalado, pero la herramienta [!DNL CVT] no lo detecta. |
| Desconocido | La herramienta no puede confirmar el estado del parche desde el registro, la comparación de diferencias o el resultado de detección disponibles. |

{style="table-layout:auto"}

### Valores de estado de CVE

La salida JSON informa de los valores de estado de CVE en mayúsculas.

| Estado de CVE | Significado |
| --- | --- |
| `PROTECTED` | Se ha detectado el parche aplicable para el CVE o el componente. |
| `VULNERABLE` | Falta un parche aplicable para el CVE o el componente. |
| `UNKNOWN` | La herramienta [!DNL CVT] no puede determinar el estado de CVE a partir de los datos de detección y registro disponibles. |
| `NOT_APPLICABLE` | El CVE se aplica a un componente que no está instalado, como Adobe Commerce empresa a empresa (B2B), Adobe Commerce Page Builder o Adobe Commerce Inventory. |

{style="table-layout:auto"}

### Campos de salida clave

El informe puede incluir la siguiente información:

- **Versión base de Adobe Commerce**: la versión base instalada detectada de `composer.lock`.
- **Origen del Registro**: Indica si los metadatos de revisión proceden de `remote`, `cache` o `stale_cache`.
- **Componentes instalados**: se detectaron áreas de paquetes de Adobe Commerce en `composer.lock`.
- **Parches aplicados**: se detectaron parches de seguridad mensuales en la base de código de Adobe Commerce.
- **Parches que faltan** - Parches de seguridad mensuales que se aplican pero no se detectan.
- **Parches desconocidos** - Parches que la herramienta [!DNL CVT] no puede clasificar.
- **Estado de vulnerabilidad por CVE**: cobertura CVE asignada a estado protegido, vulnerable, no aplicable o desconocido.
- **Advertencias**: condiciones que podrían afectar a la confiabilidad o integridad del informe.

## Registro y caché de parches

El archivo de registro de revisiones contiene los metadatos de las revisiones que utiliza la herramienta [!DNL CVT] para determinar qué revisiones se aplican a una versión instalada. La herramienta utiliza una nueva caché del Registro cuando está disponible, obtiene el Registro remoto cuando es necesario y puede utilizar una caché obsoleta con una advertencia si la red no está disponible. Use `--no-cache` solo cuando necesite nuevas recuperaciones remotas.

## Temas relacionados

- [Introducción](intro.md)
- [Resolución de problemas](troubleshooting.md)
- [Notas de la versión](release-notes.md)
