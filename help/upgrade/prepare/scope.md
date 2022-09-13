---
title: Comprender el ámbito de actualización
description: Obtenga información sobre los cambios incompatibles con versiones anteriores en una versión que podrían afectar a los módulos personalizados de Adobe Commerce o Magento Open Source o a las extensiones de terceros.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 0%

---


# Comprender el alcance de la actualización

Consulte la [notas de la versión](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) para comprender el alcance de una versión, incluidas las mejoras, las correcciones de errores y los problemas conocidos que podrían afectar a los módulos personalizados y de terceros.

## Cambios incompatibles con versiones anteriores

Las versiones de Adobe Commerce y Magento Open Source pueden contener cambios incompatibles con versiones anteriores. Revise nuestra documentación de cambios incompatibles con versiones anteriores, consulte lo siguiente:

- **[Principales cambios destacados](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/index.html)**: cambios que tienen un impacto importante y requieren explicaciones detalladas e instrucciones especiales para garantizar que los módulos de terceros sigan funcionando.
- **[Referencia de cambios menores](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/reference.html)**: documentación de referencia generada a partir de la base de código que describe cambios menores en las clases, la pertenencia a la API, la base de datos, la inyección de dependencias, las interfaces, los diseños, el sistema y XSD.

## Extensiones de terceros

La nueva política de compatibilidad de Adobe Commerce Marketplace garantiza que _all_ Las extensiones enumeradas son compatibles con la última versión publicada en un plazo de 30 días a partir de la fecha de GA. Por este motivo, es importante obtener las extensiones de terceros, siempre que sea posible, a través de Marketplace.

## Módulos personalizados

Todos los módulos personalizados deben comprobarse con la versión de destino a la que desee actualizar. Este es el proceso de actualización que requiere más tiempo y recursos. Al evaluar los módulos personalizados, debe buscar cambios incompatibles con versiones anteriores y tener en cuenta las nuevas prácticas, como la descomposición del controlador. Puede obtener más información sobre esto en la sección [notas de la versión](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html). Además, asegúrese de que está siguiendo [prácticas recomendadas](https://developer.adobe.com/commerce/php/best-practices/extensions/) para el desarrollo de módulos.

## [!DNL Upgrade Compatibility Tool]

La variable [!DNL Upgrade Compatibility Tool] es una herramienta de línea de comandos que analiza la instancia para detectar posibles problemas de actualización. Comprueba los problemas entre la versión actual que has instalado y la versión a la que estás intentando actualizar.

El uso de esta herramienta reduce el esfuerzo que su equipo necesita para comprender el alcance y el impacto de una actualización. Le ayuda a evitar problemas comunes con el código al actualizar y proporciona una dirección clara sobre cómo resolver los problemas identificados. También ayuda a priorizar los problemas más críticos necesarios para garantizar una actualización exitosa, ahorrando tiempo y costes al realizar la actualización.

Consulte las secciones siguientes para empezar a usar el [!DNL Upgrade Compatibility Tool]. Consulte la [!DNL Upgrade Compatibility Tool] [guía](../upgrade-compatibility-tool/overview.md) para obtener más información técnica y casos de uso avanzados.

### Descargar la herramienta

Use el Compositor para descargar la herramienta. Requiere PHP 7.3 o posterior, al menos 2 GB de RAM, Node.js (si está comprobando la compatibilidad con GraphQL) y una licencia de Adobe Commerce.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Ejecutar la herramienta

Para analizar la instancia y comprobar si hay errores, advertencias y problemas críticos:

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> La variable `<dir>` es el directorio donde se almacena el código base. La variable `-c` compara su base de código con la versión especificada (por ejemplo, 2.4.4).

Para identificar los problemas más críticos que debe abordar su equipo:

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

Algunas opciones más para usar con este comando son:

- `--ignore-current-version-compatibility-issues`: suprime todos los problemas críticos conocidos, errores y advertencias contra su versión actual. Solo proporciona errores en la versión que intenta actualizar.

- `--min-issue-level`: le permite establecer el nivel de problema mínimo para ayudar a priorizar solo los problemas más importantes con la actualización. Las opciones son advertencia, error y crítica en orden ascendente de gravedad.

- `-m | [=MODULE-PATH]`: si desea analizar únicamente un determinado proveedor, módulo o incluso directorio, también puede especificar la ruta como opción.

- `--vanilla-dir`: le permite comprobar si el código principal tiene alguna implementación no estándar de funciones o personalizaciones. Es importante que se limpien previamente. Se descarga automáticamente una instancia de vainilla de su versión como referencia.

   >[!NOTE]
   >
   > Esto también se puede hacer con la variable `core:code:changes` en la herramienta).

### Analizar la salida

La variable [!DNL Upgrade Compatibility Tool] exporta un archivo JSON que identifica el código o los módulos afectados, la gravedad y una descripción del problema para cada problema que encuentra. También genera un informe de resumen con una puntuación de complejidad, que permite a su equipo comprender aproximadamente lo que se necesita para actualizar a la versión más reciente. Cuanto menor sea la puntuación de complejidad, más fácil será realizar la actualización.

El siguiente resultado muestra un informe de resumen de ejemplo:

```console
 ------------------------ --------
  Installed version        2.4.2
  Adobe Commerce version   2.4.3
  Running time             0m:48s
  Checked modules          14
  Core checked modules     0
  Core modified files      0
  % core modified files    0.00
  PHP errors found         109
  PHP warnings found       0
  GraphQL errors found     0
  GraphQL warnings found   0
  Total errors found       109
  Total warnings found     0
  Complexity score         218
 ------------------------ --------
```

### Sugerencias y consejos

Todos los problemas que la herramienta identificó se enumeran en el informe con códigos de error específicos. Utilice la variable [referencia de mensaje de error](../upgrade-compatibility-tool/error-messages.md) para obtener más información sobre cada problema. Adobe también proporciona sugerencias para corregir cada tipo de problema, de modo que pueda planificar los pasos de corrección.

Utilice el informe para calcular la cantidad de esfuerzo que se necesitará para actualizar el código para la actualización. En función de su experiencia, puede calcular el esfuerzo necesario para actualizar en función del número total de problemas identificados y la gravedad de los problemas. Dado que esta es una herramienta de línea de comandos, puede incorporarla a los grupos de comprobación de código y pruebas automatizadas y utilizar la salida JSON para generar sus informes.

Se recomienda guardar los resultados de cada proyecto de actualización para poder comparar los resultados de actualización futuros con los resultados anteriores. Con el uso continuado, empezará a desarrollar un buen sentido del nivel de esfuerzo que se necesita para actualizar a la siguiente versión solo desde el informe de resumen proporcionado por la herramienta.

También le recomendamos que ejecute la herramienta regularmente mientras trabaja en la actualización para tener visibilidad sobre su progreso. El número de problemas debería disminuir a medida que los solucione. Esto también ayuda a su equipo a decidir cuál es el mejor método para distribuir el trabajo.

La variable [!DNL Upgrade Compatibility Tool] se sigue mejorando y las futuras versiones incluirán funciones como autocorrecciones que le ayudarán a solucionar los problemas lo más rápido posible. Las últimas mejoras publicadas en enero de 2022 incluyen pruebas de compatibilidad de PHP 8.1 y funciones de visualización de HTML que le ayudan a identificar rápidamente las áreas que pueden requerir más esfuerzos para actualizarse.
