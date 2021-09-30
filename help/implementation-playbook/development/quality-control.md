---
title: Control de calidad
description: Obtenga información sobre los procesos de control de calidad del comercio de Adobe relacionados con los proyectos de implementación.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---


# Proceso y herramientas de control de calidad

![Diagrama del proceso de control de calidad](../../assets/playbooks/quality-control-diagram.svg)

El proceso de control de calidad del diagrama anterior se puede describir brevemente de la siguiente manera.

<table>
<thead>
  <tr>
    <th>Proceso de desarrollo de software</th>
    <th>Flujo de trabajo de QC</th>
    <th>QC</th>
    <th>Líder QC</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Desarrollo</td>
    <td>Planificación</td>
    <td></td>
    <td>Revisar y contribuir a los planes de ensayo</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Crear especificaciones de prueba (casos de prueba/escenarios de prueba)</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Preparación y adquisición de datos de prueba</td>
  </tr>
  <tr>
    <td></td>
    <td>Análisis de pruebas y diseño</td>
    <td>Revisar y contribuir a los planes de ensayo</td>
    <td>Inicio de la preparación, especificaciones</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Crear especificaciones de prueba (casos de prueba/escenarios de prueba)</td>
    <td>Escribir o revisar una estrategia de prueba para el proyecto</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Preparación y adquisición de datos de prueba</td>
    <td> Encabezamiento, orientación y supervisión del análisis, diseño</td>
  </tr>
  <tr>
    <td>Pruebas internas</td>
    <td>Implementación y ejecución de pruebas</td>
    <td>Implementa pruebas, ejecuta y registra las pruebas</td>
    <td>Seguimiento de la implementación y ejecución de las pruebas</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Comprobar el rendimiento y analizar la seguridad: evalúe los resultados y las desviaciones con respecto a los resultados esperados</td>
    <td>Garantizar la trazabilidad de las pruebas hasta la base de las pruebas y realizar un seguimiento de los errores en el sistema de seguimiento de errores</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Publicar errores en el sistema de seguimiento de errores (Jira/Redmine/Trello)</td>
    <td>Priorizar/programar pruebas para que se ajusten a la planificación del proyecto definida por el PM</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Volver a probar (prueba de confirmación) después de corregir los errores</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Evaluación e informes</td>
    <td>Informar del progreso de las pruebas a los clientes potenciales y PM de QC</td>
    <td>Evaluación de los resultados y el progreso de las pruebas</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Escribir informes de resumen de prueba basados en la información recopilada durante la prueba</td>
  </tr>
  <tr>
    <td>UAT</td>
    <td>UAT</td>
    <td>Verificación de las fuentes de comentarios del cliente o de las solicitudes de cambio (CR)</td>
    <td>Seguimiento</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Realización de pruebas de repetición y regresión después de cambiar el código fuente</td>
    <td>Control</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Actualización de las especificaciones de prueba</td>
    <td></td>
  </tr>
  <tr>
    <td>Mantenimiento</td>
    <td>Mantenimiento</td>
    <td>Revisar y contribuir a las tareas</td>
    <td>Revisión y estimación del tiempo para las tareas</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Crear/actualizar especificaciones de prueba</td>
    <td>Progreso de las pruebas de seguimiento</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Ejecutar pruebas para estas tareas</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Realizar pruebas de regresión</td>
    <td></td>
  </tr>
</tbody>
</table>

Al igual que las [herramientas](project-management-tools.md) que identificamos para el proceso de desarrollo, hemos seleccionado un puñado de soluciones y plataformas de elección que a menudo utilizamos para las pruebas de control de calidad.

| Objetivo | Herramienta |
|---------------------------|---------------------------------------------------|
| Índice de rendimiento del sitio web | Google PageSpeed, Webpagetest, JMeter |
| Seguridad | Adobe Commerce Security Scan Tool, SonarQube, ZAP |
| Sistema de gestión de problemas | JIRA |
| Pruebas de la interfaz de usuario | Píxel perfecto, Pila de navegador |
| Pruebas de API | Postman, SoapUI |
| Pruebas de automatización | Selenio |


## Índice de rendimiento del sitio web

GooglePageSpeed informa sobre el rendimiento de una página tanto en dispositivos móviles como de escritorio, y proporciona sugerencias sobre cómo se puede mejorar dicha página.

WebPageTest es una herramienta de rendimiento web que utiliza exploradores reales para acceder a páginas web y recopilar métricas de temporización.

JMeter es un proyecto de Apache que puede utilizarse como herramienta de prueba de carga para analizar y medir el rendimiento de una variedad de servicios, con especial atención a las aplicaciones web.

## Seguridad

SonarQube y ZAP se introdujeron en el proceso de desarrollo, pero también lo incluimos aquí con más información sobre cómo está involucrado en el proceso de control de calidad.

SonarQube también se utiliza para la inspección continua de la calidad del código para realizar revisiones automáticas con análisis estáticos del código para detectar errores, olores de código y vulnerabilidades de seguridad.

OWASPZAP (Zed Attack Proxy) está diseñado para ser utilizado por los nuevos usuarios en seguridad de aplicación, así como por los probadores de penetración profesional. Algunas de las funciones integradas incluyen interceptar servidor proxy, rastreadores web tradicionales y AJAX, escáner automatizado, escáner pasivo, navegación forzada, Fuzzier, compatibilidad con WebSocket, lenguajes de scripting y compatibilidad con Plug-n-Hack.

## Pruebas de la interfaz de usuario

Perfect Pixel permite a los desarrolladores y diseñadores de marcas colocar una superposición de imagen semitransparente sobre la parte superior del HTML desarrollado y realizar una comparación de píxeles perfecta entre ellos.

BrowserStack es una plataforma de prueba móvil y web en la nube que permite a los desarrolladores probar sus sitios web y aplicaciones móviles en navegadores bajo demanda, sistemas operativos y dispositivos móviles reales.

## Pruebas de API

Postman es la plataforma de colaboración para el desarrollo de API. Postman simplifica cada paso de la creación de una API y optimiza la colaboración para que pueda crear mejores API.

SoapUI es una aplicación de prueba de servicio web de código abierto para el Protocolo simple de acceso a objetos (SOAP) y las transferencias de estado representativas (REST). Su funcionalidad abarca la inspección del servicio web; invocación, desarrollo, simulación y burla; pruebas funcionales; pruebas de carga y cumplimiento.

## Pruebas de automatización

Selenium se compone de varios componentes (la API de cliente Selenium, Selenium WebDriver), cada uno de los cuales asume un papel específico en el desarrollo de la automatización de pruebas de aplicaciones web.
