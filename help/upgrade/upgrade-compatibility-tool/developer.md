---
title: '"[!DNL Upgrade Compatibility Tool] Información para desarrolladores"'
description: Personalice el [!DNL Upgrade Compatibility Tool] uso de la integración de índice de API.
source-git-commit: 97295df89fda393c8cf8675f8f4be92ac6f38a6a
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] información para desarrolladores

Este tema contiene información para los desarrolladores que trabajan estrechamente con el código Adobe Commerce y desean obtener información detallada sobre la variable [!DNL Upgrade Compatibility Tool]. Puede utilizar este conocimiento para personalizar los componentes de la herramienta.

## Integración del índice de la API de Adobe Commerce

La integración del índice de la API de Adobe Commerce es una solución de integración interna que incluye un conjunto de herramientas para explorar las extensiones de Adobe Commerce desarrolladas por Adobe, socios de Adobe Commerce y proveedores de terceros en función del análisis del código estático.

La integración con el índice de API de Adobe Commerce se realiza mediante:

`sut\Domain\MRay\MRayInterface`

Se implementa a través del `config/services.yaml` archivo. Su valor decide dónde responde a los métodos `api()` y `modules()` viene de.

Edite este archivo para personalizar la respuesta según su instalación. Reemplace el valor asignado a `sut\Domain\MRay\MRayInterface`:

### Ejemplo de un valor personalizado

`sut\Domain\MRay\MRayInterface : "@sut_mray_mock"`

En el ejemplo anterior, la variable [!DNL Upgrade Compatibility Tool] uses `@sut_mray_mock` como el `MRayInterface` implementación. Las respuestas de `api()` y `modules()` los métodos provienen de los siguientes archivos:

- `dev/mray_mock_files/api.json`
- `dev/mray_mock_files/modules.json`

>[!NOTE]
>
>Al cambiar la variable `services.yaml` elimine el `var/cache/` para aplicar correctamente los cambios.

## Pruebas de unidad

Para ejecutar las pruebas unitarias, ejecute uno de los siguientes comandos:

- `vendor/bin/phpunit tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist --testsuite=unit-tests`

## Pruebas de integración

Para ejecutar las pruebas de integración, ejecute uno de los siguientes comandos:

- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist tests/integration`
- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist --testsuite=integration-tests`

## Pruebas de aceptación

1. Antes de ejecutar las pruebas de aceptación, debe establecer la URL de Adobe Commerce en la variable `phpunit` archivo de configuración.
1. Copiar el valor predeterminado `tests/acceptance/phpunit.xml` (sin el sufijo .dist).
1. Cambie el `TESTS_BASE_URL` para que apunte a la URL de Adobe Commerce que desea probar.
1. Para ejecutar las pruebas de aceptación, ejecute uno de los siguientes comandos:

   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml tests/acceptance`
   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml --testsuite=acceptance-tests`

## Prueba de unidades GraphQL y análisis de código ESLint

### Requisitos

>[!NOTE]
>
>Debe tener Node.js en el sistema, consulte la [Documentación de Node.js](https://nodejs.dev/learn/how-to-install-nodejs).

Las siguientes instrucciones están destinadas a los sistemas MacOS:

1. Abra un terminal y vaya al directorio raíz del proyecto.
1. Instalar dependencias del proyecto:

   ```bash
   npm install
   ```

### Prueba de unidades de GraphQL

La variable [Jest](https://jestjs.io/docs/getting-started) se utilizó framework para crear estas pruebas unitarias JS:

Las pruebas están dentro de `dev/tests/Js`.

Los esquemas de cadena para pruebas se encuentran dentro de `dev/tests/Acceptance/_files/graphql_schemas`.

Ejecute pruebas unitarias o `jest` de la siguiente manera:

```bash
./node_modules/.bin/jest --verbose --rootDir=dev/tests/Js/
```

### Análisis de código ESLint

[ESLint](https://eslint.org/docs/user-guide/getting-started) es una herramienta de análisis de código estático para identificar patrones problemáticos que se encuentran en el código JavaScript, con el objetivo de hacer que el código sea más coherente y evitar errores.

Ejecutar `eslint` análisis de código de la siguiente manera:

```bash
./node_modules/.bin/eslint -c dev/tests/Static/.eslintrc --rulesdir vendor/magento/magento-coding-standard/eslint/rules path/to/analyse
```

## Puntuación de complejidad

La variable **puntuación de complejidad** es una cifra que indica lo difícil que podría ser una actualización de la versión actual a la nueva. Los números más bajos indican actualizaciones más sencillas.

>[!NOTE]
>
>Las puntuaciones de complejidad varían entre 0 y∞.

Esta puntuación se basa en los resultados extraídos del análisis:

- Número de problemas identificados
- Gravedad de las cuestiones identificadas

La variable [!DNL Upgrade Compatibility Tool] calcula esta puntuación según la fórmula de puntuación de complejidad que se muestra a continuación.

### Fórmula de puntuación de complejidad

`Complexity Score = (Critical issues * 3) + (Errors *2) + Warnings`

>[!WARNING]
>
>Son valores absolutos.
