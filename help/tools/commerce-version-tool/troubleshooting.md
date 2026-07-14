---
title: '[!DNL Commerce Version Tool] solución de problemas'
description: Obtenga información sobre cómo solucionar problemas de detección de  [!DNL Commerce Version Tool] Composer, comprobaciones internas de ejecución en seco, caché del Registro, salida JSON y registro de auditoría.
TQID: 'https://experienceleague.adobe.com/JwRSy7pfM89WoifYUzTVPhR-WrDIvj2A2B8SaEnmyWM'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 1222
ht-degree: 0%

---

# [!DNL Commerce Version Tool] solución de problemas

Utilice esta página para solucionar problemas comunes de [!DNL Commerce Version Tool] ([!DNL CVT]) con la detección del Compositor, la carga del Registro, la detección de parches de ejecución seca interna, la generación de resultados y el registro de auditoría.

## Pasos rápidos de solución de problemas

Si la herramienta [!DNL CVT] no devuelve el informe de estado de parche esperado:

- Confirme que la instalación de destino utiliza una versión y una edición de Adobe Commerce compatibles.
- Confirme que `composer.lock` está presente y coincide con el entorno que desea inspeccionar.
- Confirme que PHP y el sistema binario `patch` están disponibles.
- Confirme que [!DNL CVT] puede leer el archivo de registro de revisiones.
- Revise `warnings`, `missing_patches` y `unknown_patches` en el resultado.
- Compruebe `var/log/patch_status.log` el resumen de auditoría de la ejecución, si se ha creado el archivo de registro.

>[!TIP]
>
> El archivo de registro es muy útil cuando necesita comprender por qué no se puede clasificar un parche. Para cada parche desconocido, el registro registra la salida sin procesar de los intentos de ejecución en seco hacia delante y hacia atrás, incluidos los errores o errores de agrupamiento.
>
> Si tiene problemas para recuperar los archivos de registro o de revisión, compruebe el campo de advertencias en el informe. Estos detalles no aparecen en el registro.

## Problemas y soluciones comunes

### No se puede detectar la versión base

Si la herramienta [!DNL CVT] no encuentra la versión base de Adobe Commerce, compruebe estas condiciones:

**Comprobación:**

- Falta `composer.lock`.
- El comando `patch-status` se está ejecutando fuera de la raíz del proyecto de Adobe Commerce (o `--root` señala a la ruta de acceso incorrecta), por lo que no se encuentra `composer.lock`.
- `composer.lock` existe pero no es un archivo JSON válido o no se puede leer.
- `composer.lock` no contiene ninguno de los paquetes base reconocidos (`magento/product-enterprise-edition`, `magento/product-community-edition`, `magento/magento2-base`).

**Mensajes de advertencia:**

Si `composer.lock` existe pero no se puede leer, analizar o no contiene un paquete base reconocido, la herramienta emite una de las siguientes cadenas en el campo de salida advertencias:

```shell-session
No recognized Commerce base package found in composer.lock
composer.lock exists but could not be read
composer.lock could not be parsed as JSON
```

>[!NOTE]
>
> Si falta `composer.lock` por completo, la herramienta informa de `base_version: "unknown"` con **ningún mensaje de advertencia**. Compruebe siempre `base_version` directamente en la salida. No confíe en la presencia de una advertencia para encontrar este problema.

Cualquiera de las condiciones mencionadas anteriormente indica que la herramienta no puede detectar la versión base. La herramienta se cierra con el código `1` y no se realiza ninguna detección de revisión.

**Acciones:**

- Ejecute el comando `patch-status` desde la raíz del proyecto [!DNL Adobe Commerce] o pase el `--root` correcto.
- Confirme que `composer.lock` está presente, que es un JSON actual y que es válido.
- Confirme que la instalación utiliza una edición compatible de Adobe Commerce, de modo que `composer.lock` contenga uno de los paquetes base reconocidos.

### No se aplican parches a la versión instalada

Si [!DNL CVT] informa de que `base_version` es válido pero `applied_patches`, `missing_patches` y `unknown_patches` están vacíos, la versión instalada no está cubierta por el registro de parches actual.

**Comprobación:**

- La versión [!DNL Adobe Commerce] instalada no se representa en el archivo de registro de revisiones. Por ejemplo, una versión más reciente que las entradas más recientes del Registro.

**Mensajes de advertencia:**

```shell-session
No patches found in registry for installed component versions (CE=2.4.7-p9)
```

Esta advertencia es diferente de &quot;no se puede detectar la versión base&quot;. `base_version` es correcto, la herramienta sale de `0` y no hay nada en el Registro con lo que comparar.

**Acciones:**

- Confirme `base_version` en el resultado que espera.
- Confirmar que `registry_source` es `remote` o un(a) `cache` reciente, no uno obsoleto.
- Póngase en contacto con el servicio de asistencia de Adobe Commerce si la versión ya debería estar cubierta.

### No se puede recuperar el registro de parches

Si la herramienta [!DNL CVT] no puede obtener el archivo de registro de parches más reciente, compruebe la configuración de la caché y la red:

**Comprobación:**

- La red no está disponible.
- La solicitud de extremo de parche de Adobe agota el tiempo de espera.
- Se usó `--no-cache` y no se puede tener acceso al Registro remoto.
- `PATCH_REGISTRY_URL` señala a un registro no disponible o no es una dirección URL HTTPS válida.
- Si la herramienta [!DNL CVT] no puede obtener el archivo de registro de parches más reciente, compruebe la configuración de la caché y la red:

>[!NOTE]
>
>Si falta el archivo de registro o ha caducado, la herramienta descarga el registro más reciente del host remoto.

**Mensajes de advertencia:**

La herramienta emite las siguientes cadenas en el campo de salida advertencias para este escenario:

```shell-session
Remote registry fetch failed (HTTP 403). Check PATCH_REGISTRY_URL (if set) and network connectivity.
Remote registry response was not valid JSON; ignoring.
Could not load remote registry. Using cached registry (3 hours old). CVE coverage may be incomplete.
Patch registry could not be loaded.
Could not fetch remote registry and --no-cache was set; aborting.
```

El mensaje de caché obsoleto incluye la antigüedad real en horas, por ejemplo, `(3 hours old)`.

Las advertencias `patch registry could not be loaded` y `could not fetch remote registry` indican que la herramienta se cerró sin ejecutar la detección de parches.

**Acciones:**

- Vuelva a ejecutar el comando `patch-status` cuando la conectividad de red esté disponible.
- Permitir que la herramienta [!DNL CVT] utilice el registro almacenado en caché si se acepta una advertencia de caché obsoleta para el análisis.
- Elimine `--no-cache` a menos que necesite recuperaciones remotas nuevas.
- Confirme que la herramienta [!DNL CVT] puede escribir en `var/patch_metadata/` si desea reutilizar la caché del Registro.

### La diferencia del parche no se puede recuperar ni verificar

Si la herramienta [!DNL CVT] no puede probar uno o más parches aplicables, compruebe el acceso de diferencia de parches:

**Comprobación:**

- No se puede descargar una diferencia de parche desde el extremo del parche de Adobe.
- Faltan las credenciales necesarias para las descargas de parches autenticadas o no son válidas.
- `PATCH_DIFF_BASE_URL` señala a un origen de diferencia de parche no disponible o no es una dirección URL HTTPS válida.
- Falta la comparación de diferencias del parche en caché o no es legible.
- La verificación SHA-256 falla para una comparación de diferencias de parche descargada.
- La herramienta [!DNL CVT] no puede escribir en `var/patch_metadata/.patch_diffs/`.

**Mensajes de advertencia:**

La herramienta emite las siguientes cadenas en el campo de salida advertencias para este escenario:

```shell-session
Patch 247p9-2026-05-001-EE requires authentication. Set credentials via COMPOSER_AUTH or auth.json.
Could not fetch patch 247p9-2026-05-001-EE (HTTP 401). Check credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch 247p9-2026-05-001-EE (HTTP 404).
Could not fetch or verify patch 247p9-2026-05-001-EE. Check network connectivity and credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch file for 247p9-2026-05-001-EE.
SHA-256 verification failed for patch 247p9-2026-05-001-EE; discarding download.
```

El Id. de revisión de cada mensaje es el Id. de entrada del Registro real, por ejemplo `247p9-2026-05-001-EE`. `SHA-256 verification failed` significa que un archivo de parche recién descargado no coincide con la suma de comprobación esperada. La herramienta lo descarta sin almacenar en caché y clasifica el parche `unknown` para esta ejecución. Se ha detectado una entrada de caché *local* dañada, que se ha recuperado silenciosamente en la misma ejecución sin previo aviso. En ambos casos, no es necesaria una limpieza manual de la caché.

**Acciones:**

- Confirme la conectividad de red y vuelva a intentar el comando.
- Confirme que están configuradas las credenciales necesarias para las descargas de parches autenticadas.
- Confirme que la herramienta [!DNL CVT] puede escribir en `var/patch_metadata/.patch_diffs/`.
- Conservar la advertencia y los detalles de salida si el parche sigue clasificado como desconocido.

### Se informa de parches faltantes o desconocidos

Si el informe contiene valores `missing_patches` o `unknown_patches` inesperados, revise los detalles de instalación y salida:

**Comprobación:**

- Los parches mensuales se aplicaban fuera de secuencia.
- Falta un parche específico de un componente, como Adobe Commerce de empresa a empresa (B2B) o Adobe Commerce Page Builder.
- `composer.lock` informa de una versión de componente instalada que requiere la revisión.
- Una comparación de diferencias de parche no está disponible o el resultado de la detección no es concluyente.

**Mensajes de advertencia:**

La herramienta emite las siguientes cadenas en el campo de salida advertencias para este escenario:

```shell-session
No file_name or sha256 for 247p9-2026-05-001-EE
Registry entry '247p9-2026-05-001-EE' requires unknown patch '247p9-2026-04-001-EE'; skipping.
descendant diffs unavailable for 247p9-2026-06-001-EE; dry-run for 247p9-2026-05-001-EE may be inaccurate
Failed to reverse-apply 247p9-2026-06-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
Failed to forward-apply prerequisite 247p9-2026-04-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
```

Cuando aparece `may be inaccurate` en una advertencia, la comprobación de ejecución en seco se sigue ejecutando, pero con confianza reducida. El parche aún se puede categorizar en `applied_patches` o `missing_patches`, no necesariamente en `unknown_patches`.

Para parches desconocidos específicos, `var/log/patch_status.log` registra la salida de ejecución en seco de parche sin procesar (hacia adelante y hacia atrás), lo que indica qué archivos y fragmentos no coinciden.

Si aparece la advertencia &quot;No se encontraron parches&quot;, consulte [no se aplican parches a la versión instalada](#no-patches-apply-to-the-installed-version) para obtener instrucciones.

**Acciones:**

- Revise los campos `applied_patches`, `missing_patches` y `unknown_patches`.
- Confirme si los parches que faltan se aplican a la edición y los componentes instalados.
- Compare el resultado con las notas de la versión del parche de seguridad relevantes.
- Confirme que la base de código inspeccionada coincide con el entorno implementado sobre el que desea informar.
- Póngase en contacto con el servicio de asistencia de Adobe Commerce si el estado desconocido bloquea la planificación de correcciones.

### La salida no se genera

Si la herramienta [!DNL CVT] se completa pero falta la salida JSON o CSV esperada, compruebe la sintaxis del comando y la salida de terminal:

**Acciones:**

- Utilice la salida JSON predeterminada si no se requiere la salida CSV.
- Use `--format=csv` para generar la salida CSV.
- Confirme que el shell, script o escáner que ejecuta la herramienta [!DNL CVT] no redirige ni descarta la salida del comando.
- Buscar `stderr` mensajes de error `patch-status:`.
- Si se redirige el resultado a un archivo, por ejemplo `patch-status > report.json`, confirme que el shell tiene permiso de escritura para ese destino. La herramienta solo escribe en `stdout`.
- Confirme que la herramienta [!DNL CVT] puede escribir en `var/log/patch_status.log`.
- Vuelva a ejecutar el comando y capture la salida del terminal para la resolución de problemas.

## Obtención de ayuda

Al ponerse en contacto con el servicio de asistencia de Adobe Commerce, proporcione solo los detalles necesarios para investigar el problema.

Incluir:

- Versión y edición de Adobe Commerce
- [!DNL CVT] versión de herramienta
- Origen del Registro de la salida de la herramienta [!DNL CVT]
- Valores `applied_patches`, `missing_patches` y `unknown_patches` relevantes
- Advertencias relevantes
- Mensaje de error o salida de comando

No incluya secretos, credenciales, claves privadas ni datos de clientes no relacionados en los registros o archivos adjuntos compartidos.

## Temas relacionados

- [Introducción](intro.md)
- [Generación de un informe de estado del parche](generate-report.md)
- [Notas de la versión](release-notes.md)
