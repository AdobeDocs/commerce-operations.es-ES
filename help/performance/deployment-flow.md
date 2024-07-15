---
title: Flujo de implementación
description: Obtenga información acerca de los pasos necesarios para implementar Adobe Commerce en un entorno de producción.
feature: Best Practices, Deploy
exl-id: 88da0b1b-5aa7-4f1c-9d01-ae58324b2754
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Flujo de implementación

El flujo de implementación de producción [!DNL Commerce] ayuda a que un almacén alcance el máximo rendimiento.

## Instalar dependencias

Los archivos `composer.json` y `composer.lock` administran las dependencias de [!DNL Commerce] e instalan la versión adecuada para cada paquete. Debe instalar dependencias antes de [instrucciones de inyección de dependencias de preprocesamiento](#preprocess-dependency-injection-instructions) si tiene pensado actualizar el [cargador automático](#update-the-autoloader).

Para instalar dependencias [!DNL Commerce]:

```bash
composer install --no-dev
```

## Instrucciones de inyección de dependencia previa al proceso

Cuando preprocese y compile las instrucciones de inyección de dependencia (ID), Magento:

* Lee y procesa todas las configuraciones presentes
* Analiza las dependencias entre clases
* Crea archivos generados automáticamente (incluidos proxies, fábricas, etc.)
* Almacena los datos compilados y la configuración en una caché que ahorra hasta el 25 % de tiempo en el procesamiento de solicitudes

Para preprocesar y compilar instrucciones de ID:

```bash
bin/magento setup:di:compile
```

## Actualizar el cargador automático

Una vez finalizada la compilación, confirme que [APCu está habilitado](../performance/software.md#php-settings) y actualice el cargador automático:

Para actualizar el cargador automático:

>[!INFO]
>
>La opción `-o` convierte la carga automática de PSR-0/4 en un mapa de clases para obtener un cargador automático más rápido. La opción `--apcu` usa APCu para almacenar en caché las clases encontradas o no encontradas.

```bash
composer dump-autoload -o --apcu
```

Si planea actualizar el cargador automático, debe ejecutar los siguientes comandos en orden:

```bash
composer install --no-dev
```

```bash
bin/magento setup:di:compile
```

```bash
composer dump-autoload -o
```

```bash
bin/magento setup:static-content:deploy
```

## Implementación de contenido estático

La implementación de contenido estático hace que [!DNL Commerce] realice las siguientes acciones:

* Analizar todos los recursos estáticos
* Realizar combinación, minimización y agrupamiento de contenido
* Leer y procesar datos de temáticas
* Analizar reserva de tema
* Almacene todo el contenido procesado y materializado en una carpeta específica para su uso posterior

Si el contenido estático no se implementa, [!DNL Commerce] realiza todas las operaciones enumeradas sobre la marcha, lo que produce un aumento significativo del tiempo de respuesta.

Puede utilizar una variedad de opciones para personalizar las operaciones de implementación en función del tamaño del almacén y las necesidades de satisfacción. El más común es la estrategia de implementación compacta. Ver [estrategias de implementación de archivos estáticos](../configuration/cli/static-view-file-strategy.md)

Para implementar contenido estático:

```bash
bin/magento setup:static-content:deploy
```

Este comando permite al Compositor reconstruir la asignación a los archivos de proyecto para que se carguen más rápido.

## Definir modo de producción

>[!INFO]
>
>Al establecer el modo en producción, se ejecuta `setup:di:compile` y `setup:static-content:deploy` automáticamente.

Por último, debe colocar la tienda en modo de producción. El modo de producción está optimizado específicamente para el máximo rendimiento de su tienda. También desactiva todas las funciones específicas del desarrollador. Esto se puede hacer en el archivo `.htaccess` o `nginx.conf`:

`SetEnv MAGE_MODE production`

También puede implementar contenido estático, compilar el contenido y establecer el modo en un comando CLI:

```bash
bin/magento deploy:mode:set production
```

El comando se ejecuta en segundo plano y no permite establecer opciones adicionales en cada paso específico.

## Acciones adicionales previas al lanzamiento

Se recomiendan estos pasos, pero no son obligatorios. Puede realizarlas inmediatamente antes de lanzar su tienda en modo de producción. La lista incluye:

* Volver a indexar los datos para evitar la presencia de datos incoherentes en los índices.
* Vacíe la caché para asegurarse de que no quedan datos antiguos o incorrectos en la caché.
* Caliente la caché, que llama a las páginas de tienda más populares o críticas por adelantado, para que la caché para ellos se genere y almacene. Esta operación se puede realizar con cualquier rastreador de Internet o manualmente, si tiene una tienda pequeña.
