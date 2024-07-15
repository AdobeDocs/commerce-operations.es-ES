---
title: Prácticas recomendadas de gestión de excepciones
description: Conozca los métodos recomendados para registrar excepciones al desarrollar proyectos de Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# Prácticas recomendadas de gestión de excepciones

Si no se escribe una excepción en el archivo `exception.log` con el modelo de excepción como contexto, no se reconoce ni se analiza correctamente en New Relic u otro almacenamiento de registro compatible con el monólogo PSR-3. El registro de solo una parte de la excepción (o el registro en el archivo incorrecto) provoca errores en la producción cuando se pasan por alto las excepciones.

## Tratamiento correcto de excepciones

En la siguiente lista de comprobación se proporcionan ejemplos para mostrar el control correcto de excepciones.

### ![correcto](../../../assets/yes.svg) Escribir en el registro de excepciones

Escriba en el registro de excepciones utilizando el siguiente patrón, independientemente de las acciones posteriores, a menos que haya una razón de peso para no hacerlo.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

Este método guarda automáticamente `$e->getMessage` en el mensaje de registro y el objeto `$e` en el contexto, siguiendo el [estándar de contexto PSR-3](https://www.php-fig.org/psr/psr-3/#13-context). Esto se completó en `\Magento\Framework\Logger\Monolog::addRecord`.

### ![corregir](../../../assets/yes.svg) señales de Silenciar

Silenciar las señales no registrando las excepciones que forman parte del flujo de operaciones deseado. No es necesario realizar ninguna acción de seguimiento cuando se encuentra la excepción, por lo que no es necesario registrarla y analizarla cuando se produce. Añada un comentario que indique el motivo de las señales de silencio y que es intencional. Combinar con `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![corregir](../../../assets/yes.svg) excepciones de downgrade

Degradar excepciones siguiendo el [estándar de contexto PSR-3](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![corregir](../../../assets/yes.svg) El registro siempre es lo primero

Como práctica recomendada, el registro siempre es lo primero en el código para evitar casos en los que se produce otra excepción o error grave antes de escribir en el registro.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![corregir](../../../assets/yes.svg) mensajes de registro y todo el seguimiento de excepciones

Registrar mensajes y todo el seguimiento de excepciones siguiendo el [estándar de contexto PSR-3](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## Tratamiento de excepciones incorrecto

Los siguientes ejemplos muestran un control de excepciones incorrecto.

### ![Lógica incorrecta](../../../assets/no.svg) antes del registro

La lógica anterior al registro puede provocar otra excepción o un error irrecuperable, que impide que se registre la excepción y debe reemplazarse por [ejemplo correcto](#logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![incorrecto](../../../assets/no.svg) `catch` vacío

Los bloques `catch` vacíos pueden ser un signo de silencio no intencionado y deben reemplazarse con el [ejemplo correcto](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![incorrecta](../../../assets/no.svg) Localización doble

Si la excepción localizada detectada aún no se ha traducido, resuelva el problema en el lugar en el que se produce la excepción la primera vez.

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![incorrectos](../../../assets/no.svg) mensajes de registro y seguimiento a diferentes archivos de registro

El siguiente código registra incorrectamente el seguimiento de pila de una excepción como una cadena en un archivo de registro.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

Este método introduce saltos de línea en el mensaje, que no es compatible con PSR-3. La excepción, incluido el seguimiento de pila, debe formar parte del contexto del mensaje para garantizar que se guarda correctamente con el mensaje en New Relic u otro almacenamiento de registro compatible con monólogos PSR-3.

Solucione este problema reemplazando el código que sigue los ejemplos correctos que se muestran en [Escribir en el registro de excepciones](#write-to-the-exception-log) o en [Excepciones de downgrade](#downgrade-exceptions).

### ![incorrectas](../../../assets/no.svg) excepciones de downgrade sin contexto

La excepción se ha degradado a un error, que no permite pasar un objeto, sino sólo una cadena, de ahí el `getMessage()`. Esto hace que se pierda el seguimiento y debe reemplazarse por los ejemplos correctos que se muestran en [Escribir en el registro de excepciones](#write-to-the-exception-log) o en [excepciones de downgrade](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![incorrecto](../../../assets/no.svg) registra solo el mensaje en el registro de excepciones

En lugar de pasar el objeto `$e`, solo se pasa `$e->getMessage()`. Esto hace que se pierda el seguimiento y debe reemplazarse por los ejemplos correctos mostrados [Escribir en el registro de excepciones](#write-to-the-exception-log) o [Bajar de categoría las excepciones](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![incorrecto](../../../assets/no.svg) falta `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

Omitir la línea `phpcs:ignore` genera un déclencheur de advertencia en PHPCS y no debería pasar su CI. Este debe reemplazarse por el ejemplo correcto mostrado en [Señales de silencio](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
