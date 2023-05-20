---
title: Ejecute el [!DNL Upgrade Compatibility Tool]
description: Siga estos pasos para ejecutar el [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos para el proyecto de Adobe Commerce.
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 0%

---

# Descargue la [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Para empezar a usar la [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos, descárguela ejecutando el siguiente comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Es posible que deba conceder a la herramienta permisos de ejecutable con el `chmod` comando:

```bash
chmod +x ./uct/bin/uct
```

## El [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos

El [!DNL Upgrade Compatibility Tool] es una herramienta que compara una instancia personalizada de Adobe Commerce con una versión específica analizando todos los módulos instalados en ella. Devuelve una lista de problemas, errores y advertencias críticos que deben solucionarse antes de actualizar a la versión más reciente de Adobe Commerce.

Ver esto [tutorial de vídeo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) para obtener más información sobre [!DNL Upgrade Compatibility Tool].

Comandos disponibles para [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos:

| **Comando** | **Descripción** |
|----------------|-----------------|
| `upgrade:check` | Este comando ejecuta el [!DNL Upgrade Compatibility Tool] analizando todos los módulos instalados en él. |
| `dbschema:diff` | Este comando muestra todas las diferencias del esquema de base de datos entre dos versiones de Adobe Commerce especificadas. |
| `core:code:changes` | Este comando compara la instalación actual de Adobe Commerce con una instalación limpia y sencilla. |
| `refactor` | Este comando corrige automáticamente un conjunto reducido de problemas. |
| `graphql:compare` | Este comando proporciona la opción de inspeccionar dos extremos de GraphQL y comparar sus esquemas. |
| `list` | Este comando devuelve una lista de todos los [!DNL Upgrade Compatibility Tool] comandos disponibles. |
| `help` | Este comando devuelve todos los disponibles `help`opciones para [!DNL Upgrade Compatibility Tool]. Este comando se puede ejecutar, así como una opción con los comandos anteriores. |

## Utilice el `upgrade:check` mando

El `upgrade:check` El comando comprueba los cambios del código principal de esa instancia de Adobe Commerce específica y todos los cambios de código personalizado instalados en ella.

El `upgrade:check` es el comando principal para ejecutar la herramienta:

```bash
bin/uct upgrade:check <dir>
```

Donde `<dir>` value es el directorio donde se encuentra la instancia de Adobe Commerce.

Opciones disponibles para `upgrade:check` comando:

| **Comando** | **Opciones disponibles** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: Devuelve todas las opciones disponibles.</li><li>—current-version: Versión actual de Adobe Commerce. Este parámetro es obligatorio y siempre debe usarse.</li><li>—min-issue-level: puede filtrar problemas según el nivel mínimo de problemas (el valor predeterminado es ADVERTENCIA).</li><li>—ignore-current-version-compatibility-issues (o -i): si no desea incluir en su informe los problemas, errores y advertencias críticos de la versión actual.</li><li>—coming-version (o -c): Dirija una versión de Adobe Commerce específica. Si se omite, se utilizará el último disponible.</li></ul> |

El [!DNL Upgrade Compatibility Tool] le permite ejecutar el `upgrade:check` con un `--ignore-current-version-compatibility-issues` opción. Utilice esta opción cuando solo desee obtener nuevos problemas que se introduzcan con la actualización de la versión actual a la versión de destino en su [!DNL Upgrade Compatibility Tool] informe:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Esto solo se aplica a las validaciones de API de PHP.

### Añadir el `--coming-version` opción

Puede comparar su instalación actual de Adobe Commerce con cualquier versión de Adobe Commerce `>=2.3` mediante el uso de `--coming-version` opción.

Debe proporcionar la versión como parámetro al ejecutar el `upgrade:check` comando:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Donde `-c, --coming-version[=COMING-VERSION]` hace referencia a la versión de destino de Adobe Commerce.

Existen algunas limitaciones al ejecutar el `--coming-version`:

- Este parámetro hace referencia a cualquier etiqueta que identifique una versión específica de Adobe Commerce.
- Es un requisito proporcionar este explícitamente; proporcionar solo el valor del mismo no funciona.
- Proporcione la versión de la etiqueta sin comillas (ni simples ni dobles): ~~&quot;2.4.1-development&quot;~~.
- NO debe proporcionar versiones anteriores a la instalada, ni anteriores a la 2.3, que es la más antigua admitida en este momento.

## Utilice el `dbschema:diff` mando

Puede recuperar la diferencia entre el esquema de la base de datos de dos versiones de Adobe Commerce.

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Donde los argumentos son los siguientes:

- `<current-version>`: cualquier versión de Adobe Commerce para comparar.
- `<target-version>`: también cualquier versión de Adobe Commerce para comparar.

Ejemplo de ejecución:

```bash
bin/uct dbschema:diff 2.4.3 2.4.3-p3

DB schema differences between versions 2.4.3 and 2.4.3-p3:

Table klarna_payments_quote constraint QUOTE_ID_KLARNA_PAYMENTS_QUOTE_QUOTE_ID_QUOTE_ENTITY_ID is present only in version 2.4.3-p3
Table klarna_payments_quote index KLARNA_PAYMENTS_QUOTE_SESSION_ID is present only in version 2.4.3-p3
Table customer_entity column session_cutoff is present only in version 2.4.3-p3
Table customer_visitor column session_id length value is different. 2.4.3: "64", 2.4.3-p3: "1"
Table customer_visitor column session_id comment value is different. 2.4.3: "Session ID", 2.4.3-p3: "Deprecated: Session ID value no longer used"
Table customer_visitor column created_at is present only in version 2.4.3-p3
Table oauth_consumer column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table oauth_token column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table admin_user_session column session_id nullable value is different. 2.4.3: "false", 2.4.3-p3: "true"
Table admin_user_session column session_id length value is different. 2.4.3: "128", 2.4.3-p3: "1"
Table admin_user_session column session_id comment value is different. 2.4.3: "Session ID value", 2.4.3-p3: "Deprecated: Session ID value no longer used"

Total detected differences between version 2.4.3 and 2.4.3-p3: 11
```

## Utilice el `core:code:changes` mando

Puede comparar la instalación actual de Adobe Commerce para comprobar si el código principal de Adobe Commerce se ha modificado para implementar una personalización. Este comando solo muestra una lista de las modificaciones principales:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Donde los argumentos son los siguientes:

- `<dir>`: directorio de instalación de Adobe Commerce.
- `<vanilla dir>`: directorio de instalación de Adobe Commerce vanilla.

Opciones disponibles para `core:code:changes` comando:

| **Comando** | **Opciones disponibles** |
|----------------|-----------------|
| `core:code:changes` | `--help`: Devuelve todos los disponibles `--help` opciones. |

>[!NOTE]
>
> Se recomienda mantener el código personalizado fuera del código principal. Consulte Adobe Commerce 2.4 [guía de actualización](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) para conocer las prácticas recomendadas de actualización.

### Instalación de vainilla

A _vainilla_ la instalación es una instalación limpia de una rama o etiqueta de versión especificada para una versión específica.

El `bin/uct core:code:changes` El comando comprueba si hay una instancia de vainilla en el sistema. Si es la primera vez que utiliza una instalación predeterminada, una pregunta interactiva de la línea de comandos le pedirá que descargue el proyecto de instalación básica del repositorio de Adobe Commerce (`https://repo.magento.com/`).

Puede ejecutar un [!DNL Upgrade Compatibility Tool] con el comando `--vanilla-dir` para especificar el directorio de instalación de Adobe Commerce vanilla.

Consulte la [Implementar instancia de vainilla](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) para obtener más información.

## Utilice el `refactor` mando

El [!DNL Upgrade Compatibility Tool] tiene la capacidad de corregir automáticamente un conjunto reducido de problemas:

- Las funciones que se permitían utilizar sin pasar un argumento, pero con ese uso ahora están en desuso.
- Uso de `$this` en plantillas de Magento.
- Uso de la palabra clave PHP `final` en métodos privados.

Para ello, ejecute el `refactor` comando:

```bash
bin/uct refactor <dir>
```

Donde `<dir>` value es el directorio donde se encuentra la instancia de Adobe Commerce.

Opciones disponibles para `refactor` comando:

| **Comando** | **Opciones disponibles** |
|----------------|-----------------|
| `refactor` | `--help`: Devuelve todos los disponibles `--help` opciones. |

## Utilice el `graphql:compare` mando

Este comando proporciona la opción al [!DNL Upgrade Compatibility Tool] para inspeccionar dos extremos de GraphQL y comparar sus esquemas en busca de cambios importantes y peligrosos entre ellos:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Donde los argumentos son los siguientes:

- `<schema1>`: URL de extremo para la instalación existente.
- `<schema2>`: URL de extremo para la instalación predeterminada.

Opciones disponibles para `graphql:compare` comando:

| **Comando** | **Opciones disponibles** |
|----------------|-----------------|
| `graphql:compare` | `--help`: Devuelve todos los disponibles `--help` opciones. |

## Utilice el `list` mando

Para devolver una lista de [!DNL Upgrade Compatibility Tool] comandos disponibles, ejecute:

```bash
bin/uct list
```

## Utilice el `help` mando

Para ver la [!DNL Upgrade Compatibility Tool] comando opciones generales y ayuda, ejecute:

```bash
bin/uct --help
```

Devuelve una lista con todos los disponibles `help` opciones para [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos:

```terminal
- --raw             To output raw command list
- --format=FORMAT   The output format (txt, xml, json, or md) [default: "txt"]
- --short           To skip describing commands' arguments
- -h, --help            Display help for the given command. When no command is given display help for the list command
- -q, --quiet           Do not output any message
- -V, --version         Display this application version
- --ansi|--no-ansi  Force (or disable --no-ansi) ANSI output
- -n, --no-interaction  Do not ask any interactive question
- -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```

Es posible ejecutar `--help` como opción al ejecutar un comando específico. Devuelve `--help` opciones para el comando especificado.

Ejemplo de `upgrade:check` comando con `--help` opción:

```bash
bin/uct upgrade:check --help
```

Devuelve las opciones específicas que se pueden ejecutar para `upgrade:check` comando:

```terminal
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --min-issue-level[=MIN-ISSUE-LEVEL]            Minimal issue level you want to see in the report (warning, error or critical). [default: "warning"]
- -i, --ignore-current-version-compatibility-issues  Ignore common issues for current and coming version
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

## Seguir las prácticas recomendadas de Adobe Commerce

- Evite tener dos módulos con el mismo nombre.
- Seguir Adobe Commerce [estándares de codificación](https://developer.adobe.com/commerce/php/coding-standards/).
- Adobe Commerce 2.4 [Guía de actualización](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) prácticas recomendadas.
- Ejecute el [!DNL Upgrade Compatibility Tool] desde el [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) para [Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} proyectos.

## Optimización de los resultados

El [!DNL Upgrade Compatibility Tool] proporciona un informe que contiene los resultados con todos los problemas identificados en el proyecto de forma predeterminada. Puede optimizar los resultados para centrarse en los problemas que debe corregir para completar la actualización:

- Utilice la opción `--ignore-current-version-compatibility-issues` cuando solo desee obtener nuevos problemas que se introduzcan con la actualización de la versión actual a la versión de destino en su [!DNL Upgrade Compatibility Tool] informe.
- Añadir el `--min-issue-level` opción, esta configuración permite establecer el nivel mínimo de problema para ayudar a priorizar solo los problemas más importantes con la actualización.
- El [!DNL Upgrade Compatibility Tool] requiere al menos 2 GB de RAM para ejecutarse. Se recomienda esta configuración para evitar problemas debido a una limitación de memoria baja. El [!DNL Upgrade Compatibility Tool] muestra una pregunta si ejecuta el `upgrade:check` comando con un bajo `memory_limit` configuración.
