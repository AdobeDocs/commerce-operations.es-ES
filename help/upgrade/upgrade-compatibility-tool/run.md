---
title: "Ejecute el [!DNL Upgrade Compatibility Tool]"
description: Siga estos pasos para ejecutar el [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos para su proyecto de Adobe Commerce.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1072'
ht-degree: 0%

---


# Descargue el [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Para empezar con el [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos, descárguela ejecutando el siguiente comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Es posible que tenga que dar a la herramienta permisos ejecutables con la variable `chmod` comando:

```bash
chmod +x ./uct/bin/uct
```

## La variable [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos

La variable [!DNL Upgrade Compatibility Tool] es una herramienta que comprueba una instancia personalizada de Adobe Commerce con una versión específica analizando todos los módulos instalados en ella. Devuelve una lista de problemas, errores y advertencias críticos que deben solucionarse antes de actualizar a la versión más reciente de Adobe Commerce.

Consulte esta [tutorial de vídeo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) para obtener más información sobre la variable [!DNL Upgrade Compatibility Tool].

Los comandos disponibles para la variable [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos:

| **Comando** | **Descripción** |
|----------------|-----------------|
| `upgrade:check` | Este comando ejecuta el [!DNL Upgrade Compatibility Tool] analizando todos los módulos instalados en él. |
| `dbschema:diff` | Este comando muestra todas las diferencias de esquema de base de datos entre dos versiones de Adobe Commerce especificadas. |
| `core:code:changes` | Este comando compara la instalación actual de Adobe Commerce con una instalación de vainilla limpia. |
| `refactor` | Este comando corrige automáticamente un conjunto reducido de problemas. |
| `graphql:compare` | Este comando proporciona la opción de inspeccionar dos extremos de GraphQL y comparar sus esquemas. |
| `list` | Este comando devuelve una lista de todos los [!DNL Upgrade Compatibility Tool] comandos disponibles. |
| `help` | Este comando devuelve todos los valores disponibles `help`para las [!DNL Upgrade Compatibility Tool]. Este comando se puede ejecutar así como una opción con los comandos anteriores. |

## Utilice la variable `upgrade:check` command

La variable `upgrade:check` comprueba los cambios en el código principal de esa instancia de Adobe Commerce específica y todos los cambios en el código personalizado instalados en ella.

La variable `upgrade:check` es el comando principal para ejecutar la herramienta:

```bash
bin/uct upgrade:check <dir>
```

Donde `<dir>` es el directorio donde se encuentra la instancia de Adobe Commerce.

Las opciones disponibles para la variable `upgrade:check` comando:

| **Comando** | **Opciones disponibles** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—ayuda: Devuelve todas las opciones disponibles.</li><li>—min-issue-level: Puede filtrar los problemas según el nivel de problema mínimo (el valor predeterminado es ADVERTENCIA).</li><li>—ignore-current-version-compatibility-issues (o -i): Si no desea incluir problemas críticos, errores y advertencias de la versión actual en el informe.</li><li>—coming-version (o -c): Oriente una versión específica de Adobe Commerce.</li></ul> |

La variable [!DNL Upgrade Compatibility Tool] permite ejecutar el `upgrade:check` con un `--ignore-current-version-compatibility-issues` . Utilice esta opción cuando solo desee obtener problemas nuevos que se introduzcan con la actualización de la versión actual a la versión de destino de [!DNL Upgrade Compatibility Tool] informe:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Esto solo se aplica a las validaciones de la API PHP.

### Adición de la variable `--coming-version` option

Puede comparar su instalación actual de Adobe Commerce con cualquier versión de Adobe Commerce `>=2.3` usando la variable `--coming-version` .

Debe proporcionar la versión como parámetro al ejecutar el `upgrade:check` comando:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Donde `-c, --coming-version[=COMING-VERSION]` hace referencia a la versión de destino de Adobe Commerce.

Existen algunas limitaciones al ejecutar el `--coming-version`:

- Este parámetro hace referencia a cualquier etiqueta que identifique una versión específica de Adobe Commerce.
- Es un requisito que se proporcione explícitamente; proporcionar solo el valor de no funciona.
- Proporcione la versión de la etiqueta sin comillas (ni simple ni doble): ~~&quot;2.4.1-desarrollar&quot;~~.
- NO debe proporcionar versiones anteriores a la que tiene instalada actualmente, ni anteriores a la 2.3, que es la más antigua compatible en este momento.

## Utilice la variable `dbschema:diff` command

Puede recuperar la diferencia entre el esquema de base de datos de dos versiones de Adobe Commerce.

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

## Utilice la variable `core:code:changes` command

Puede comparar la instalación actual de Adobe Commerce para validar si el código principal de Adobe Commerce se modificó para implementar una personalización. Este comando solo muestra una lista de modificaciones principales:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Donde los argumentos son los siguientes:

- `<dir>`: directorio de instalación de Adobe Commerce.
- `<vanilla dir>`: Directorio de instalación de vainilla de Adobe Commerce.

Las opciones disponibles para la variable `core:code:changes` comando:

| **Comando** | **Opciones disponibles** |
|----------------|-----------------|
| `core:code:changes` | `--help`: Devuelve todos los `--help` opciones. |

>[!NOTE]
>
> Se recomienda mantener el código personalizado fuera del código principal. Consulte Adobe Commerce 2.4 [guía de actualización](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) para obtener más información sobre las prácticas recomendadas de actualización.

### Instalación de vainilla

A _vainilla_ la instalación es una instalación limpia de una rama o etiqueta de versión especificada para una versión específica.

La variable `bin/uct core:code:changes` comprueba si hay una instancia de vainilla en el sistema. Si es la primera vez que se utiliza una instalación de vainilla, una pregunta interactiva de la línea de comandos le pedirá que descargue el proyecto de vainilla del repositorio de Adobe Commerce (`https://repo.magento.com/`).

Puede ejecutar un [!DNL Upgrade Compatibility Tool] con la variable `--vanilla-dir` para especificar el directorio de instalación de Adobe Commerce vainilla.

Consulte la [Implementar instancia de vanilla](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) para obtener más información.

## Utilice la variable `refactor` command

La variable [!DNL Upgrade Compatibility Tool] tiene la capacidad de corregir automáticamente un conjunto reducido de problemas:

- Funciones que se permitieron usar sin pasar un argumento, pero que ahora están en desuso.
- Uso de `$this` en plantillas de Magento.
- Uso de la palabra clave PHP `final` en métodos privados.

Para ello, ejecute el `refactor` comando:

```bash
bin/uct refactor <dir>
```

Donde `<dir>` es el directorio donde se encuentra la instancia de Adobe Commerce.

Las opciones disponibles para la variable `refactor` comando:

| **Comando** | **Opciones disponibles** |
|----------------|-----------------|
| `refactor` | `--help`: Devuelve todos los `--help` opciones. |

## Utilice la variable `graphql:compare` command

Este comando proporciona la opción de [!DNL Upgrade Compatibility Tool] para introspeccionar dos extremos de GraphQL y comparar sus esquemas buscando cambios dañinos y peligrosos entre ellos:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Donde los argumentos son los siguientes:

- `<schema1>`: Dirección URL del extremo para la instalación existente.
- `<schema2>`: Dirección URL de extremo para la instalación de vainilla.

Las opciones disponibles para la variable `graphql:compare` comando:

| **Comando** | **Opciones disponibles** |
|----------------|-----------------|
| `graphql:compare` | `--help`: Devuelve todos los `--help` opciones. |

## Utilice la variable `list` command

Para devolver una lista de [!DNL Upgrade Compatibility Tool] comandos disponibles, ejecutar:

```bash
bin/uct list
```

## Utilice la variable `--help` command

Para ver el [!DNL Upgrade Compatibility Tool] comando opciones generales y ayuda, ejecute:

```bash
bin/uct --help
```

Que devuelve una lista con todas las disponibles `help` para las [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos:

```terminal
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

Sin embargo, es posible ejecutar `--help` como opción al ejecutar un comando específico. Esto devolverá un valor específico `--help` para ese comando específico.

Ejemplo de `upgrade:check` comando con `--help` opción:

```bash
bin/uct upgrade:check --help
```

Esto devuelve opciones específicas que se pueden ejecutar para la variable `upgrade:check` comando:

```terminal
--min-issue-level.
-i, --ignore-current-version-compatibility-issues.
```

## Siga las prácticas recomendadas de Adobe Commerce

- Evite tener dos módulos con el mismo nombre.
- Seguir Adobe Commerce [normas de codificación](https://developer.adobe.com/commerce/php/coding-standards/).
- Adobe Commerce 2.4 [Guía de actualización](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) prácticas recomendadas.

## Optimizar los resultados

La variable [!DNL Upgrade Compatibility Tool] proporciona un informe con resultados con todos los problemas identificados en el proyecto de forma predeterminada. Puede optimizar los resultados para centrarse en los problemas que debe corregir para completar la actualización:

- Utilice la opción `--ignore-current-version-compatibility-issues` cuando solo desee obtener problemas nuevos que se introduzcan con la actualización de su versión actual a la versión de destino en su [!DNL Upgrade Compatibility Tool] informe.
- Adición de la variable `--min-issue-level` , esta configuración permite establecer el nivel mínimo de problema para ayudar a priorizar solo los problemas más importantes con la actualización.
- La variable [!DNL Upgrade Compatibility Tool] requiere al menos 2 GB de RAM para ejecutarse. Se recomienda esta configuración para evitar problemas debido a una limitación de memoria baja. La variable [!DNL Upgrade Compatibility Tool] muestra una pregunta si ejecuta la variable `upgrade:check` comando con un valor bajo `memory_limit` configuración.
