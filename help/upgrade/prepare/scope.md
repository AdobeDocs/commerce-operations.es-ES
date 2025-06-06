---
title: Comprender el ámbito de actualización
description: Obtenga información acerca de los cambios incompatibles con versiones anteriores en una versión que podrían afectar a los módulos personalizados de Adobe Commerce o a las extensiones de terceros.
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: 9eeb0e3a1c75b25cc70b092d23f02ebfe355d6bd
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---

# Comprender el ámbito de la actualización

Revise las [notas de la versión](https://experienceleague.adobe.com/es/docs/commerce-operations/release/notes/overview) para comprender el ámbito de una versión, incluidas las mejoras, las correcciones de errores y los problemas conocidos que podrían afectar a los módulos personalizados y de terceros.

## Cambios incompatibles con versiones anteriores

Las versiones de Adobe Commerce pueden contener cambios incompatibles con versiones anteriores. Revise la documentación de cambios incompatibles con versiones anteriores, consulte lo siguiente:

- **[Cambios importantes](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/)**: cambios que tienen un impacto importante y requieren una explicación detallada e instrucciones especiales para garantizar que los módulos de terceros sigan funcionando.
- **[Referencia de cambio menor](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)**: documentación de referencia generada a partir de la base de código que describe cambios menores en las clases, pertenencia a API, base de datos, inyección de dependencias, interfaces, diseños, sistema y XSD.

## Extensiones de terceros

La nueva directiva de compatibilidad de Adobe Commerce Marketplace garantiza que _todas las_ extensiones enumeradas sean compatibles con la última versión publicada en un plazo de 30 días a partir de la fecha de disponibilidad general. Por este motivo, es importante obtener las extensiones de terceros, siempre que sea posible, a través de Marketplace.

## Módulos personalizados

Todos los módulos personalizados deben comprobarse con la versión de destino a la que desee actualizar. Este es el proceso de actualización que requiere más tiempo y recursos. Al evaluar los módulos personalizados, debe buscar cambios incompatibles con versiones anteriores y tener en cuenta las nuevas prácticas, como la descomposición del controlador. Puede obtener más información sobre esto en [notas de la versión](https://experienceleague.adobe.com/es/docs/commerce-operations/release/notes/overview). Además, asegúrese de seguir las [prácticas recomendadas](https://developer.adobe.com/commerce/php/best-practices/extensions/) para el desarrollo de módulos.

## [!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool] es una herramienta de línea de comandos que analiza la instancia en busca de posibles problemas de actualización. Comprueba si hay problemas entre la versión actual que ha instalado y la versión a la que intenta actualizar.

El uso de esta herramienta reduce el esfuerzo necesario por parte de su equipo para comprender el ámbito y el impacto de una actualización. Ayuda a evitar problemas de código comunes al actualizar y proporciona una dirección clara sobre cómo resolver los problemas identificados. También ayuda a priorizar los problemas más importantes necesarios para garantizar una actualización correcta, lo que ahorra tiempo y costes al realizar la actualización.

Consulte las secciones siguientes para comenzar con [!DNL Upgrade Compatibility Tool]. Consulte la [!DNL Upgrade Compatibility Tool] [guía](../upgrade-compatibility-tool/overview.md) para obtener más información técnica y casos de uso avanzados.

### Descargue la herramienta

Use Composer para descargar la herramienta. Requiere PHP 7.3 o posterior, al menos 2 GB de RAM, Node.js (si está comprobando la compatibilidad con GraphQL) y una licencia de Adobe Commerce.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Ejecute la herramienta

Para analizar la instancia y comprobar si hay errores, advertencias y problemas críticos:

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> El argumento `<dir>` es el directorio donde se almacena la base de código. La opción `-c` compara el código base con la versión especificada.

Para identificar los problemas más críticos que debe abordar su equipo:

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

Otras opciones que se pueden utilizar con este comando son:

- `--ignore-current-version-compatibility-issues`: suprime todos los problemas, errores y advertencias críticos conocidos de la versión actual. Solo genera errores en la versión que intenta actualizar.

- `--min-issue-level`: permite establecer el nivel mínimo de problema para ayudar a priorizar únicamente los problemas más importantes con la actualización. Las opciones son advertencia, error y crítico en orden ascendente de gravedad.

- `-m | [=MODULE-PATH]`: si desea analizar únicamente un determinado proveedor, módulo o incluso directorio, también puede especificar la ruta como opción.

- `--vanilla-dir`: permite comprobar el código principal de cualquier implementación no estándar de funciones o personalizaciones. Es importante que estos se limpien de antemano. Se descarga automáticamente una instancia de vainilla de su versión para referencia.

  >[!NOTE]
  >
  > Esto también se puede hacer con el comando `core:code:changes` en la herramienta).

### Analizar la salida

[!DNL Upgrade Compatibility Tool] exporta un archivo JSON que identifica el código o módulos afectados, la gravedad y una descripción del problema para cada problema que encuentre. También genera un informe de resumen con una puntuación de complejidad, que permite a su equipo comprender aproximadamente lo que se necesita para actualizar a la versión más reciente. Cuanto menor sea la puntuación de complejidad, más fácil será realizar la actualización.

El resultado siguiente muestra un informe de resumen de ejemplo:

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

Todos los problemas identificados por la herramienta se enumeran en el informe con códigos de error específicos. Use la [referencia de mensaje de error](../upgrade-compatibility-tool/error-messages.md) para obtener más detalles sobre cada problema. Adobe también proporciona sugerencias para solucionar cada tipo de problema de modo que pueda planificar los pasos de corrección.

Utilice el informe para calcular la cantidad de esfuerzo que se tardará en actualizar el código para la actualización. En función de su experiencia, puede estimar el esfuerzo necesario para actualizar en función del número total de problemas identificados y de la gravedad de los mismos. Como se trata de una herramienta de línea de comandos, puede incorporarla a grupos de pruebas automatizadas y comprobación de código, y utilizar la salida JSON para generar informes.

Se recomienda guardar los resultados de cada proyecto de actualización para poder comparar los resultados futuros de la actualización con los anteriores. Con el uso continuado, comenzará a comprender el nivel de esfuerzo que se necesita para actualizar a la siguiente versión solo a partir del informe de resumen proporcionado por la herramienta.

También le recomendamos que ejecute la herramienta regularmente mientras trabaja en la actualización para tener visibilidad de su progreso. El número de problemas debe disminuir a medida que los soluciona. Esto también ayuda a su equipo a decidir cuál es el mejor enfoque para distribuir el trabajo.

Se sigue mejorando [!DNL Upgrade Compatibility Tool] y las futuras versiones incluirán características como correcciones automáticas para ayudarle a solucionar los problemas lo más rápido posible. Las últimas mejoras publicadas en enero de 2022 incluyen pruebas de compatibilidad con PHP 8.1 y funcionalidades de visualización de HTML que le ayudan a identificar rápidamente las áreas que pueden requerir un mayor esfuerzo para la actualización.
