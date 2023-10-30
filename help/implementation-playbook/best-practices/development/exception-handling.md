---
title: Prácticas recomendadas de gestión de excepciones
description: Conozca los métodos recomendados para registrar excepciones al desarrollar proyectos de Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Prácticas recomendadas de gestión de excepciones

Si no se escribe una excepción en `exception.log` con el modelo de excepción como contexto, no se reconoce ni se analiza correctamente en New Relic u otro almacenamiento de registro compatible con monólogos PSR-3. El registro de solo una parte de la excepción (o el registro en el archivo incorrecto) provoca errores en la producción cuando se pasan por alto las excepciones.

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

Este método guarda automáticamente `$e->getMessage` al mensaje de registro y al `$e` objeto al contexto, siguiendo el [Estándar de contexto PSR-3](https://www.php-fig.org/psr/psr-3/#13-context). Esto se hace en `\Magento\Framework\Logger\Monolog::addRecord`.

### ![correcto](../../../assets/yes.svg) Silenciar señales

Silenciar las señales no registrando las excepciones que forman parte del flujo de operaciones deseado. No es necesario realizar ninguna acción de seguimiento cuando se encuentra la excepción, por lo que no es necesario registrarla y analizarla cuando se produce. Añada un comentario que indique el motivo de las señales de silencio y que es intencional. Combinar con `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![correcto](../../../assets/yes.svg) Degradar excepciones

Reduzca las excepciones siguiendo las [Estándar de contexto PSR-3](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![correcto](../../../assets/yes.svg) El registro siempre es lo primero

Como práctica recomendada, el registro siempre es lo primero en el código para evitar casos en los que se produce otra excepción o error grave antes de escribir en el registro.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![correcto](../../../assets/yes.svg) Mensajes de registro y todo el seguimiento de excepciones

Registrar mensajes y todo el seguimiento de excepciones siguiendo el [Estándar de contexto PSR-3](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## Tratamiento de excepciones incorrecto

Los siguientes ejemplos muestran un control de excepciones incorrecto.

### ![incorrecto](../../../assets/no.svg) Lógica antes del registro

La lógica anterior al registro puede provocar otra excepción o error irrecuperable, que impide que se registre la excepción y debe reemplazarse por [ejemplo correcto](#logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![incorrecto](../../../assets/no.svg) Empty `catch`

Empty `catch` Los bloqueos pueden ser un signo de silencio no intencionado y deben reemplazarse por el [ejemplo correcto](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![incorrecto](../../../assets/no.svg) Localización doble

Si la excepción localizada detectada aún no se ha traducido, resuelva el problema en el lugar en el que se produce la excepción la primera vez.

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![incorrecto](../../../assets/no.svg) Registrar mensajes y rastrear en diferentes archivos de registro

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

Para solucionar este problema, sustituya el código siguiente por los ejemplos correctos que se muestran en [Escribir en el registro de excepciones](#write-to-the-exception-log) o [Degradar excepciones](#downgrade-exceptions).

### ![incorrecto](../../../assets/no.svg) Degradar excepciones sin contexto

La excepción se reduce a un error, que no permite que se pase un objeto, sino solo una cadena, por lo que el `getMessage()`. Esto provoca que se pierda el rastro y debe reemplazarse por los ejemplos correctos que se muestran en [Escribir en el registro de excepciones](#write-to-the-exception-log) o [Degradar excepciones](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![incorrecto](../../../assets/no.svg) Registrar solo el mensaje en el registro de excepciones

En lugar de pasar el objeto `$e`, solo `$e->getMessage()` se ha aprobado. Esto provoca que se pierda el rastro y debe reemplazarse por los ejemplos correctos que se muestran [Escribir en el registro de excepciones](#write-to-the-exception-log) o [Degradar excepciones](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![incorrecto](../../../assets/no.svg) Falta `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

Omitir el `phpcs:ignore` line déclencheur una advertencia en PHPCS y no debe pasar su CI. Este debe sustituirse por el ejemplo correcto que se muestra en [Silenciar señales](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
