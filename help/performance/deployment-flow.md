---
title: Flujo de implementación
description: Obtenga información sobre los pasos necesarios para implementar Adobe Commerce o Magento Open Source en un entorno de producción.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# Flujo de implementación

La variable [!DNL Commerce] el flujo de implementación de producción ayuda a que el almacén alcance el máximo rendimiento.

## Instalar dependencias

La variable `composer.json` y `composer.lock` administrar archivos [!DNL Commerce] e instale la versión adecuada para cada paquete. Debe instalar las dependencias antes de [instrucciones de inyección de dependencias de preprocesamiento](#preprocess-dependency-injection-instructions) si planea actualizar el [autocargador](#update-the-autoloader).

Para instalar [!DNL Commerce] dependencias:

```bash
composer install --no-dev
```

## Instrucciones para la inyección de dependencia previa al proceso

Cuando preprocese y compile instrucciones de inyección de dependencia (DI), Magento:

* Lee y procesa toda la configuración presente
* Analiza las dependencias entre clases
* Crea archivos autogenerados (incluidos proxies, fábricas, etc.)
* Almacena los datos y la configuración compilados en una caché que ahorra hasta un 25% de tiempo en el procesamiento de solicitudes

Para preprocesar y compilar instrucciones de ID:

```bash
bin/magento setup:di:compile
```

## Actualizar el cargador automático

Una vez finalizada la compilación, confirme que [APCu está habilitado](../performance/software.md#php-settings) y actualizar el cargador automático:

Para actualizar el cargador automático:

>[!INFO]
>
>La variable `-o` convierte la carga automática PSR-0/4 a classmap para obtener un autocargador más rápido. La variable `--apcu` utiliza APCu para almacenar en caché las clases encontradas/no encontradas.

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

La implementación de causas de contenido estático [!DNL Commerce] para realizar las siguientes acciones:

* Analizar todos los recursos estáticos
* Realizar una combinación, minimización y agrupación de contenido
* Leer y procesar datos de temas
* Análisis de la reserva de tema
* Almacenar todo el contenido procesado y materializado en una carpeta específica para un uso posterior

Si el contenido estático no está implementado, [!DNL Commerce] realiza todas las operaciones enumeradas sobre la marcha, lo que provoca un aumento significativo del tiempo de respuesta.

Puede utilizar una variedad de opciones para personalizar las operaciones de implementación según el tamaño del almacén y las necesidades de cumplimiento. El más común es la estrategia de implementación compacta. Consulte [Estrategias de implementación de archivos estáticos](../configuration/cli/static-view-file-strategy.md)

Para implementar contenido estático:

```bash
bin/magento setup:static-content:deploy
```

Este comando permite al Composer reconstruir la asignación a archivos de proyecto para que se carguen más rápido.

## Definir modo de producción

>[!INFO]
>
>La configuración del modo en producción se ejecuta automáticamente `setup:di:compile` y `setup:static-content:deploy`.

Finalmente, debe colocar la tienda en modo Producción. El modo de producción está especialmente optimizado para ofrecer el máximo rendimiento de la tienda. También desactiva todas las funciones específicas del desarrollador. Esto se puede hacer en su `.htaccess` o `nginx.conf` archivo:

`SetEnv MAGE_MODE production`

También puede implementar contenido estático, compilar el contenido y establecer el modo en un comando CLI:

```bash
bin/magento deploy:mode:set production
```

El comando se ejecuta en segundo plano y no permite establecer opciones adicionales en cada paso específico.

## Acciones previas al inicio adicionales

Se recomiendan estos pasos, pero no son obligatorios. Puede realizarlos inmediatamente antes de iniciar la tienda en modo de producción. La lista incluye:

* Reindexe los datos para evitar la presencia de datos incoherentes en sus índices.
* Vaciar la caché para asegurarse de que no queden datos antiguos o incorrectos en la caché.
* Caliente la caché, que llama por adelantado a las páginas de almacenamiento más populares o críticas, de modo que la caché para ellas se genere y almacene. Esta operación se puede realizar con cualquier rastreador de Internet o manualmente, si tiene una tienda pequeña.
