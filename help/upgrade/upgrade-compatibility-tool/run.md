---
title: Ejecutar  [!DNL Upgrade Compatibility Tool]
description: Siga estos pasos para ejecutar  [!DNL Upgrade Compatibility Tool]  en una interfaz de línea de comandos para su proyecto de Adobe Commerce.
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: bfb952d29bd3d7fc7147107216981e05202e44aa
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# Descargar [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Para comenzar con [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos, descárguela ejecutando el siguiente comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Es posible que deba conceder a la herramienta permisos de ejecutable con el comando `chmod`:

```bash
chmod +x ./uct/bin/uct
```

## [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos

[!DNL Upgrade Compatibility Tool] es una herramienta que compara una instancia personalizada de Adobe Commerce con una versión específica analizando todos los módulos instalados en ella. Devuelve una lista de problemas, errores y advertencias críticos que deben solucionarse antes de actualizar a la versión más reciente de Adobe Commerce.

Vea este [tutorial en vídeo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) para obtener más información acerca de [!DNL Upgrade Compatibility Tool].

Comandos disponibles para [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos:

| **Comando** | **Descripción** |
|----------------|-----------------|
| `upgrade:check` | Este comando ejecuta [!DNL Upgrade Compatibility Tool] analizando todos los módulos instalados en él. |
| `dbschema:diff` | Este comando muestra todas las diferencias del esquema de base de datos entre dos versiones de Adobe Commerce especificadas. |
| `core:code:changes` | Este comando compara la instalación actual de Adobe Commerce con una instalación limpia y sencilla. |
| `refactor` | Este comando corrige automáticamente un conjunto reducido de problemas. |
| `graphql:compare` | Este comando proporciona la opción de inspeccionar dos extremos de GraphQL y comparar sus esquemas. |
| `list` | Este comando devuelve una lista de todos los [!DNL Upgrade Compatibility Tool] comandos disponibles. |
| `help` | Este comando devuelve todas las opciones `help` disponibles para [!DNL Upgrade Compatibility Tool]. Este comando se puede ejecutar, así como una opción con los comandos anteriores. |

## Usar el comando `upgrade:check`

El comando `upgrade:check` comprueba los cambios de código principal de esa instancia de Adobe Commerce específica y todos los cambios de código personalizado instalados en ella.

El comando `upgrade:check` es el comando principal para ejecutar la herramienta:

```bash
bin/uct upgrade:check <dir>
```

Donde el valor `<dir>` es el directorio donde se encuentra la instancia de Adobe Commerce.

Opciones disponibles para el comando `upgrade:check`:

| **Comando** | **Opciones disponibles** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: Devuelve todas las opciones disponibles.</li><li>—current-version: Versión actual de Adobe Commerce. Se utilizará la versión de la instalación de Adobe Commerce si se omite.</li><li>—min-issue-level: puede filtrar problemas según el nivel mínimo de problemas (el valor predeterminado es ADVERTENCIA).</li><li>—ignore-current-version-compatibility-issues (o -i): si no desea incluir en su informe los problemas, errores y advertencias críticos de la versión actual.</li><li>—coming-version (o -c): Dirija una versión de Adobe Commerce específica. Si se omite, se utilizará el último disponible.</li></ul> |

El [!DNL Upgrade Compatibility Tool] le permite ejecutar el comando `upgrade:check` con una opción `--ignore-current-version-compatibility-issues`. Utilice esta opción cuando solo desee obtener nuevos problemas que se introduzcan con la actualización de la versión actual a la versión de destino en el informe [!DNL Upgrade Compatibility Tool]:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Esto solo se aplica a las validaciones de API de PHP.

### Agregando la opción `--coming-version`

Puede comparar su instalación actual de Adobe Commerce con cualquier versión de Adobe Commerce `>=2.3` mediante la opción `--coming-version`.

Debe proporcionar la versión como parámetro al ejecutar el comando `upgrade:check`:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Donde `-c, --coming-version[=COMING-VERSION]` hace referencia a la versión de destino de Adobe Commerce.

Existen algunas limitaciones al ejecutar `--coming-version`:

- Este parámetro hace referencia a cualquier etiqueta que identifique una versión específica de Adobe Commerce.
- Es un requisito proporcionar este explícitamente; proporcionar solo el valor del mismo no funciona.
- Proporcione la versión de la etiqueta sin comillas (ni simples ni dobles): ~~&#39;2.4.1-development&#39;~~.
- NO debe proporcionar versiones anteriores a la instalada, ni anteriores a la 2.3, que es la más antigua admitida en este momento.

## Usar el comando `dbschema:diff`

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

## Usar el comando `core:code:changes`

Puede comparar la instalación actual de Adobe Commerce para comprobar si el código principal de Adobe Commerce se ha modificado para implementar una personalización. Este comando solo muestra una lista de las modificaciones principales:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Donde los argumentos son los siguientes:

- `<dir>`: directorio de instalación de Adobe Commerce.
- `<vanilla dir>`: directorio de instalación de Adobe Commerce vanilla.

Opciones disponibles para el comando `core:code:changes`:

| **Comando** | **Opciones disponibles** |
|----------------|-----------------|
| `core:code:changes` | `--help`: devuelve todas las opciones de `--help` disponibles. |

>[!NOTE]
>
> Se recomienda mantener el código personalizado fuera del código principal. Consulte la [guía de actualización](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) de Adobe Commerce 2.4 para obtener más prácticas recomendadas sobre la actualización.

### Instalación de vainilla

Una instalación de _vanilla_ es una instalación limpia de una rama o etiqueta de versión especificada para una versión específica.

El comando `bin/uct core:code:changes` comprueba si hay una instancia de vainilla en el sistema. Si esta es la primera vez que utiliza una instalación predeterminada, una pregunta interactiva de la línea de comandos le pedirá que descargue el proyecto básico del repositorio de Adobe Commerce (`https://repo.magento.com/`).

Puede ejecutar un comando [!DNL Upgrade Compatibility Tool] con la opción `--vanilla-dir` para especificar el directorio de instalación de Adobe Commerce vanilla.

Consulte el tema [Implementar instancia de vainilla](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) para obtener más información.

## Usar el comando `refactor`

[!DNL Upgrade Compatibility Tool] tiene la capacidad de corregir automáticamente un conjunto reducido de problemas:

- Las funciones que se permitían utilizar sin pasar un argumento, pero con ese uso ahora están en desuso.
- Uso de `$this` en plantillas de Magento.
- Uso de la palabra clave PHP `final` en métodos privados.

Para ello, ejecute el comando `refactor`:

```bash
bin/uct refactor <dir>
```

Donde el valor `<dir>` es el directorio donde se encuentra la instancia de Adobe Commerce.

Opciones disponibles para el comando `refactor`:

| **Comando** | **Opciones disponibles** |
|----------------|-----------------|
| `refactor` | `--help`: devuelve todas las opciones de `--help` disponibles. |

## Usar el comando `graphql:compare`

Este comando proporciona a [!DNL Upgrade Compatibility Tool] la opción de inspeccionar dos extremos de GraphQL y comparar sus esquemas en busca de cambios importantes y peligrosos entre ellos:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Donde los argumentos son los siguientes:

- `<schema1>`: dirección URL de extremo para la instalación existente.
- `<schema2>`: dirección URL de extremo para la instalación predeterminada.

Opciones disponibles para el comando `graphql:compare`:

| **Comando** | **Opciones disponibles** |
|----------------|-----------------|
| `graphql:compare` | `--help`: devuelve todas las opciones de `--help` disponibles. |

## Usar el comando `list`

Para devolver una lista de los [!DNL Upgrade Compatibility Tool] comandos disponibles, ejecute:

```bash
bin/uct list
```

## Usar el comando `help`

Para ver las opciones generales y la ayuda del comando [!DNL Upgrade Compatibility Tool], ejecute:

```bash
bin/uct --help
```

Devuelve una lista con todas las opciones de `help` disponibles para [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos:

```
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

Ejemplo del comando `upgrade:check` con la opción `--help`:

```bash
bin/uct upgrade:check --help
```

Esto devuelve opciones específicas que se pueden ejecutar para el comando `upgrade:check`:

```
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
- Siga los [estándares de codificación](https://developer.adobe.com/commerce/php/coding-standards/) de Adobe Commerce.
- Prácticas recomendadas de Adobe Commerce 2.4 [Guía de actualización](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf).
- Ejecute [!DNL Upgrade Compatibility Tool] desde [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) para los proyectos de [Adobe Commerce en la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank}.

## Optimización de los resultados

El [!DNL Upgrade Compatibility Tool] proporciona un informe que contiene los resultados con todos los problemas identificados en el proyecto de forma predeterminada. Puede optimizar los resultados para centrarse en los problemas que debe corregir para completar la actualización:

- Utilice la opción `--ignore-current-version-compatibility-issues` cuando solo desee obtener nuevos problemas que se introduzcan con la actualización de su versión actual a la versión de destino en su informe [!DNL Upgrade Compatibility Tool].
- Si agrega la opción `--min-issue-level`, esta configuración le permite establecer el nivel mínimo de problema para ayudar a priorizar solamente los problemas más importantes con la actualización.
- [!DNL Upgrade Compatibility Tool] requiere al menos 2 GB de RAM para ejecutarse. Se recomienda esta configuración para evitar problemas debido a una limitación de memoria baja. [!DNL Upgrade Compatibility Tool] muestra una pregunta si ejecuta el comando `upgrade:check` con una configuración de `memory_limit` baja.
