---
title: Prácticas recomendadas de administración de código
description: Conozca las prácticas recomendadas de administración de código para la fase de desarrollo de proyectos de Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: 0bff4c7a-1082-4b3e-b19c-bc8ad529b131
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---

# Prácticas recomendadas de administración de código para Adobe Commerce

Este tema se ha diseñado para ayudarle a decidir si desea utilizar Git o Composer para distribuir código personalizado, teniendo en cuenta la gestión de versiones, la complejidad del código y la administración de dependencias.

>[!NOTE]
>
>Estas prácticas recomendadas son las más adecuadas para migraciones e implementaciones, menos para el desarrollo de módulos únicos.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Definiciones

{{$include /help/_includes/gra-definitions.md}}

## Cuándo usar Git o Composer

<table>
<thead>
  <tr>
    <th></th>
    <th>Código administrado principalmente mediante Git</th>
    <th>Código administrado principalmente mediante Composer</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Cuándo se debe utilizar para una configuración de instancia única</td>
    <td>
      <ul>
        <li><strong>Enfoque estándar para administrar código para una configuración de instancia única</strong></li>
        <li>Cuando el código base no forme parte de un GRA multimarca en el futuro</li>
        <li>Cuando todas las marcas se ejecutan en una sola instancia como sitios web</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>Cuando la base de código pueda formar parte de una configuración de varias instancias en el futuro o pueda hacerlo</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>Cuándo se debe utilizar para una configuración de varias instancias</td>
    <td>
      <ul>
        <li>Cuando casi todos los módulos están interrelacionados (no se recomienda)</li>
        <li>Cuando el código lo mantiene un equipo que no está familiarizado con Composer</li>
      </ul>
    </td>
    <td>
      <ul>
        <li><strong>Enfoque estándar para administrar código para una configuración de varias instancias</strong></li>
        <li>Cuando Adobe mantiene el código base o el equipo de mantenimiento está familiarizado con Composer</li>
      </ul>
    </td>
  </tr>
</tbody>
</table>

## Matriz de características

| Función | Git | Compositor |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Repositorio de código principal | Todo el código reside en un único repositorio Git o en unos pocos | Todo el código reside en los paquetes de un repositorio Composer<br>Cada paquete Composer individual está representado por un repositorio Git |
| Ubicación del código | El desarrollo se produce en el directorio `app/` | El desarrollo se produce en el directorio `vendor/` |
| Administración de actualización principal | Adobe Commerce Core se instala y actualiza con Composer y el resultado se confirma en Git | Adobe Commerce Core se instala y actualiza con Composer; el resultado se confirma en Git |
| Administración de módulos de terceros | Los módulos de terceros se instalan en `vendor/` si se instalan a través del mercado o packagist.org. De lo contrario, se instalarán en `app/` | Todos los módulos de terceros están instalados en el directorio `vendor/` |
| Versiones | La liberación se caracteriza por `git merge` y `git pull` o `git checkout` comandos | La liberación se caracteriza por `composer update` y `git pull` o `git checkout` comandos |
| Número de repositorios Git | Pocas | Muchos |
| Complejidad de desarrollo | Sencilla | Complejo |
| Complejidad de solicitud de extracción | Sencilla | Complejo |
| Complejidad de revisión de código | Sencilla | Sencilla |
| Complejidad de la actualización del entorno Dev/QA/UAT | Sencilla | Complejo |
| Compatibilidad con GRA | ![Icono Sí](../../../assets/yes.svg) | ![Icono Sí](../../../assets/yes.svg) |
| Los módulos pueden instalar automáticamente bibliotecas externas | ![Sin icono](../../../assets/no.svg) | ![Icono Sí](../../../assets/yes.svg) |
| Flexibilidad en la composición GRA | ![Sin icono](../../../assets/no.svg) | ![Icono Sí](../../../assets/yes.svg) |
| Administración de dependencias del módulo | ![Icono Sí](../../../assets/yes.svg) Solo a través de `module.xml`, funcionalidad limitada | ![Icono Sí](../../../assets/yes.svg) Administración de dependencias completa a través de `composer.json` |
| Versiones de módulo | ![Icono Sí](../../../assets/yes.svg) Puede definir una versión, pero no puede instalar una versión específica | ![Icono Sí](../../../assets/yes.svg) Compatibilidad con la versión completa |
| Se necesitan servicios de pago | Repositorio de Git | Repositorio Git, Packagist privado (± 600 € al año) |
| Posibilidad de integración de Bitbucket con Jira | ![Icono Sí](../../../assets/yes.svg) | ![Icono Sí](../../../assets/yes.svg) |
| Cambios en el código disponibles instantáneamente para la instalación | ![Icono Sí](../../../assets/yes.svg) | ![Icono Sí](../../../assets/yes.svg) |

## Soluciones que se deben evitar

1. **Compositor combinado y `app/code` para sus módulos**

   Consiga que todas las desventajas de ambos estilos de administración de código se combinen en su proyecto. Añade complejidad, inestabilidad y falta de flexibilidad innecesarias.

   Por ejemplo:
   - Explique los flujos de trabajo de Git y Composer (en lugar de solo uno de ellos) al equipo de desarrollo.
   - Instale módulos incompatibles en `app/code`, ya que no hay nada que impida que esto ocurra.
   - Mover un módulo de `app/code` a Compositor (o a la inversa) es engorroso, especialmente con el desarrollo en curso.

1. **Administrador de paquetes Satis**

   Packagist privado cuesta ± € 600 por año. Este coste es para todo el GRA combinado, no por marca. No trate de evitar estos costos utilizando la solución gratuita Satis. Satis no actualiza automáticamente sus paquetes cada vez que inserta confirmaciones en Git. Además, Satis no tiene una autorización integrada. Debe mantener un servidor web para ejecutar Satis. Usted acaba gastando una multitud de la cuota de suscripción de Packagist privado manteniendo Satis.

1. **Empiece con Git y, a continuación, pase a Composer**

   Elija un método de administración de código al principio del proyecto. Cambiar de Git a Compositor o, a la inversa, con un desarrollo en curso es engorroso y podría provocar la pérdida del código o la pérdida del historial de revisiones.

<!-- Last updated from includes: 2023-08-23 15:56:59 -->
