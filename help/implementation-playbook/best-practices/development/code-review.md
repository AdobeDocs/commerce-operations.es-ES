---
title: Prácticas recomendadas de revisión de código
description: Obtenga información sobre las prácticas recomendadas de revisión de código para la fase de desarrollo de proyectos de Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 0%

---


# Prácticas recomendadas de revisión de código para Adobe Commerce

El objetivo principal de la revisión del código es validar que la funcionalidad implementada cumple los requisitos de una manera óptima desde las perspectivas de rendimiento, arquitectura y seguridad.

Además, la revisión del código tiene por objeto garantizar que cumple con las prácticas recomendadas de desarrollo de Adobe Commerce, es fácil de entender y mantener, y sigue los estándares de codificación. La mayoría de los estándares de codificación deben comprobarse automáticamente con las herramientas adecuadas.

## Proceso de revisión de código recomendado

En un nivel superior, el proceso de revisión del código debe consistir en los siguientes pasos:

1. Rama de características de cierre de compra en el entorno de desarrollo local.
1. Si ha pasado algún tiempo desde que se envió el código para su revisión, combine los cambios más recientes de la rama de destino (normalmente la rama de control de calidad) y las actualizaciones push en la rama de características remotas (si las hay).
1. Realice una revisión de alto nivel para validar que el código implementa todos los requisitos. Si hay discrepancias importantes, póngase en contacto con el desarrollador para obtener una aclaración.
1. La ejecución del código es opcional, pero si tiene dudas sobre si el código funciona según lo esperado o si facilita la eficacia del proceso, pruebe que la funcionalidad implementada funcione según lo esperado en los principales escenarios de uso. Si hay problemas importantes, detenga el proceso de revisión y vuelva a abrir el ticket con los comentarios correspondientes.
1. Realice una revisión exhaustiva para validar que el código implementa todos los requisitos. Si hay algún problema, añada los comentarios correspondientes a la solicitud de extracción y vuelva a abrir el ticket.
1. Si todo parece correcto, combine la solicitud de extracción (o pásela al siguiente nivel de revisión de código si se ha establecido uno).

Además, tenga en cuenta los siguientes puntos al implementar procesos de revisión de código:

- La revisión de código es una herramienta principal para la comunicación y la transferencia de conocimientos dentro de un equipo. Incluso si una solicitud de extracción no contiene problemas importantes e implementa la lógica empresarial necesaria, puede utilizarla como una oportunidad para sugerir más mejoras después de fusionarla.

- En promedio, la revisión de código no debería llevar más del 10 % al 20 % del esfuerzo de desarrollo. Suponiendo que el equipo de desarrollo esté formado por ingenieros sénior que trabajen bien juntos. Si la revisión del código tarda más, puede afectar al presupuesto del proyecto y a la cronología.

- Solucione los problemas con un esfuerzo excesivo necesario para las revisiones de código identificando la causa raíz. Por lo general, se debe a que o bien los requisitos se traducen mal en tickets de desarrollo (debido a problemas de comunicación, historias de usuarios pobres) o es un problema de coaching. En el primer caso, la mitigación recomendada es asegurarse de que los tickets tengan información suficiente para que los integrantes del equipo entreguen los requisitos de forma eficiente. En el segundo caso, es posible que tenga que ajustar la estructura del equipo para incluir ingenieros de mayor antigüedad o obtener la aprobación fuera de la tutoría y el coaching.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Qué buscar en la revisión de código

### Estilo

El estilo se puede probar automáticamente ejecutando la inspección de PhpStorm (ver a continuación).

Asegúrese de configurar [PHPMD y PHPCS](https://developer.adobe.com/commerce/php/best-practices/phpstorm/code-inspection/) y para ejecutar el [Codificación estándar](https://github.com/magento/magento-coding-standard) de la CLI (también a continuación). Hay cierta superposición, pero ambas también tienen pruebas únicas.

### Convención y estructura

Las revisiones de convención y estructura se realizan manualmente.

- ¿La funcionalidad de clase está limitada a una sola responsabilidad?
- ¿Tiene sentido la estructura del directorio?
- Es una funcionalidad realizada en el nivel adecuado (servidor, cliente, CSS, JS, base de datos, marco de trabajo, infraestructura).
- ¿Son correctas las versiones?
- ¿Tiene el código un aspecto poco convencional o parece que intenta evitar un problema de manera incorrecta?
- ¿Se aplica correctamente la convención de nombres para el nombre del módulo, el nombre del paquete y el nombre del repositorio?
- Compruebe que los estilos CSS globales se aplican correctamente y no se utilizan en exceso.

### Integridad

Las revisiones para comprobar que todo está completo se realizan manualmente.

- ¿Puede la configuración habilitar o deshabilitar el código y todo el código necesario se comporta según lo esperado?
- ¿Está presente toda la configuración que se menciona en el ticket? Compruebe el ámbito, el tipo de datos, la validación, la traducción y los valores predeterminados.
- ¿La configuración siempre se recupera en el nivel más bajo posible (nivel de vista de tienda, nivel de sitio web o nivel global)? La recuperación de la configuración debe coincidir con la definición de ámbito de la `system.xml` archivo.
- ¿Están cubiertas todas las rutas del diagrama de flujo de la especificación técnica? ¿Están cubiertas todas las demás especificaciones técnicas?
- ¿Se han definido ACL para la nueva funcionalidad?
- ¿PhpDocs está claro? ¿Los mensajes de compromiso son claros?
- ¿Hay algún código comentado o se ve código de depuración?

### Rendimiento

Las revisiones de rendimiento se realizan manualmente, lo que puede resultar útil cuando hay dudas.

- ¿Las consultas se ejecutan en bucle? Este bucle puede estar fuera de los archivos editados.
- ¿Puedes ver algo? `cachable="false"` ¿atributos? ¿Se aplican correctamente?

### Seguridad

Las revisiones de seguridad se realizan manualmente, lo que se puede ayudar con la búsqueda de texto. Parte de la comprobación de seguridad se realiza mediante pruebas automatizadas.

- ¿Se registran excepciones cuando es necesario? ¿Se utilizan los tipos de excepciones correctos?
- Puede `around` ¿Se pueden evitar los complementos?
- ¿Los complementos devuelven los tipos de datos correctos?
- ¿Puede encontrar cualquier consulta SQL sin procesar que deba crearse con la capa de abstracción de la base de datos?
- ¿Hay algún nuevo tipo de datos expuesto a cualquier tipo de usuario, administrador o front-end? ¿Es esa exposición un riesgo para la seguridad?
- ¿Se validan los datos generados por el usuario? Todo lo que proviene del explorador se considera generado por el usuario, incluidos los valores de cookies y los encabezados de servidor.

### Privacidad y RGPD

Revisiones de privacidad y [RGPD](../../../security-and-compliance/privacy/gdpr.md) se realizan manualmente.

- ¿El código gestiona los datos de los clientes o los correos electrónicos? Preste especial atención.
- Si este código se puede ejecutar en un bucle, ¿puede filtrar los datos de los clientes de un ciclo de bucle a otro?
- Los indicadores de un riesgo son las importaciones, los trabajos cron, los correos electrónicos transaccionales y los controladores de cola por lotes.
- Asegúrese del aislamiento de los datos de usuario en bucles. El Adobe recomienda utilizar fábricas o repositorios para crear modelos en el ciclo de bucle, a los que no se puede acceder fuera del bucle.

### Tutoría

Las revisiones para la tutoría se realizan manualmente.

- Busca lugares donde compartir conocimientos con el objetivo de formar al equipo.
- Si su comentario es puramente educativo, pero no es crítico para cumplir con los estándares, indique que no es obligatorio que el autor lo resuelva.
- Si ves algo bonito, dile al desarrollador, especialmente cuando se dirigieron a uno de tus comentarios de una manera genial. Las revisiones de código a menudo se centran en los errores, pero también deben ofrecer estímulo y reconocimiento por las buenas prácticas. A veces es incluso más valioso, en términos de tutoría, decirle a un desarrollador lo que hizo bien que decirles lo que hizo mal.

## Automatización

Los desarrolladores pueden utilizar la automatización para revisar la compilación de ID, el esquema de base de datos, la validación del compositor y el cumplimiento de los estándares de codificación:

- Compilación de ID: ejecute los siguientes comandos de CLI para ver si el código se puede compilar sin problemas.

  ```bash
  bin/magento module:disable -n -q --all || exit;
  bin/magento module:enable -n -q --all || exit;
  bin/magento cache:enable -n -q || exit;
  bin/magento cache:flush -n -q || exit;
  rm -rf generated/*
  rm -rf var/view_preprocessed/*
  rm -rf pub/static/*
  rm -rf var/cache/*
  bin/magento deploy:mode:set --skip-compilation production || exit;
  bin/magento setup:di:compile -vv || exit;
  bin/magento setup:static-content:deploy en_US || exit;
  bin/magento deploy:mode:set developer || exit;
  ```

- Esquema de base `whitelist.json`: ejecute el siguiente comando CLI y valide que la variable `db_schema_whitelist.json` no se ha agregado ni alterado el archivo.

  ```bash
  bin/magento setup:db-declaration:generate-whitelist --module-name[=MODULE-NAME]
  ```

- Validación del compositor: valida la variable `composer.json` ejecutando el siguiente comando CLI en el directorio que contiene el `composer.json` archivo.

  ```bash
  composer validate
  ```

- Estándar de codificación (Coding standard): permite instalar y ejecutar la herramienta Estándar de codificación y ejecutarla en el módulo. El siguiente archivo muestra cómo habilitarlo para que se ejecute en cualquier lugar escribiendo `mcs ./app/code/Vendor/Module/`.

  ```bash
  #!/usr/bin/env bash
  $HOME/web/magento/magento-coding-standard/vendor/bin/phpcs --standard=Magento2 "$@"
  ```

- Phpstan

  ```bash
  ./vendor/bin/phpstan analyze app/code/Vendor/Module
  ```

- Inspección de PhpStorm

- Detector de copiar/pegar de PhpStorm PHP
