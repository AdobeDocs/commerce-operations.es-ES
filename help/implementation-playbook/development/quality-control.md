---
title: Control de calidad
description: Obtenga información sobre los procesos de control de calidad de Adobe Commerce relacionados con los proyectos de implementación.
exl-id: 0eb62b24-21f6-4cec-8ef9-eeaa1ee6ae52
feature: Build
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# Proceso y herramientas de control de calidad

![Diagrama del proceso de control de calidad](../../assets/playbooks/quality-control-diagram.svg)

El proceso de control de calidad en el diagrama anterior se puede describir brevemente de la siguiente manera.

<table>
<thead>
  <tr>
    <th>Proceso de desarrollo de software</th>
    <th>Flujo de trabajo de QC</th>
    <th>QC</th>
    <th>QC Leader</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Desarrollo</td>
    <td>Planificación</td>
    <td></td>
    <td>Revisar y contribuir a los planes de prueba</td>
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
    <td>Análisis y diseño de pruebas</td>
    <td>Revisar y contribuir a los planes de prueba</td>
    <td>Iniciar la preparación, especificaciones</td>
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
    <td> Liderar, guiar y supervisar el análisis, diseño</td>
  </tr>
  <tr>
    <td>Pruebas internas</td>
    <td>Implementación y ejecución de pruebas</td>
    <td>Implementa pruebas, las ejecuta y las registra</td>
    <td>Monitorización de la implementación y ejecución de las pruebas</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Compruebe el rendimiento y la seguridad del análisis: evalúe los resultados y las desviaciones con respecto a los resultados esperados</td>
    <td>Garantizar la trazabilidad de las pruebas a la base de prueba y realizar un seguimiento de los errores en el sistema de seguimiento de errores</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Errores de Post al sistema de seguimiento de errores (Jira/Redmine/Trello)</td>
    <td>Priorizar/programar pruebas para alinearlas con la planificación del proyecto definida por el PM</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Volver a realizar la prueba (prueba de confirmación) después de corregir el error</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Evaluación y creación de informes</td>
    <td>Informe del progreso de la prueba al cliente potencial y PM de control de calidad</td>
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
    <td>Verificar los comentarios de los clientes o las solicitudes de cambio (CR)</td>
    <td>Seguimiento</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Realice pruebas de nueva prueba y regresión después de cambiar el código fuente</td>
    <td>Controlando</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Actualizar especificaciones de prueba</td>
    <td></td>
  </tr>
  <tr>
    <td>Mantenimiento</td>
    <td>Mantenimiento</td>
    <td>Revisar y contribuir a tareas</td>
    <td>Revisar y calcular el tiempo de las tareas</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Crear/actualizar especificaciones de prueba</td>
    <td>Progreso de la prueba de seguimiento</td>
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

De manera similar a las [herramientas](project-management-tools.md) que identificamos para el proceso de desarrollo, hemos seleccionado un puñado de soluciones y plataformas preferidas que solemos utilizar para las pruebas de control de calidad.

| Finalidad | Herramienta |
|---------------------------|---------------------------------------------------|
| Índice de rendimiento del sitio web | Google PageSpeed, Webpagetest, JMeter |
| Seguridad | Escáner de seguridad de Adobe Commerce, SonarQube, ZAP |
| Sistema de administración de problemas | JIRA |
| Pruebas de IU | Píxel perfecto, BrowserStack |
| Pruebas de API | Postman, IU de SOAP |
| Pruebas de automatización | Selenio |


## Índice de rendimiento del sitio web

GooglePageSpeed informa sobre el rendimiento de una página tanto en dispositivos móviles como de escritorio y proporciona sugerencias sobre cómo se puede mejorar esa página.

WebPageTest es una herramienta de rendimiento web que utiliza exploradores reales para acceder a páginas web y recopilar métricas de temporización.

JMeter es un proyecto Apache que puede utilizarse como herramienta de prueba de carga para analizar y medir el rendimiento de una variedad de servicios, con un enfoque en aplicaciones web.

## Seguridad

SonarQube y ZAP se introdujeron en el proceso de desarrollo, pero también lo incluimos aquí con más información sobre cómo está involucrado en el proceso de control de calidad.

SonarQube también se utiliza para la inspección continua de la calidad del código para realizar revisiones automáticas con análisis estático del código para detectar errores, olores del código y vulnerabilidades de seguridad.

OWASPZAP (Zed Attack Proxy) está destinado a ser utilizado tanto por aquellos nuevos en la seguridad de la aplicación, así como los probadores profesionales de penetración. AJAX Algunas de las funciones incorporadas incluyen interceptación del servidor proxy, rastreadores Web tradicionales y de la red, escáner automatizado, escáner pasivo, exploración forzada, Fuzzier, compatibilidad con WebSocket, lenguajes de scripts y compatibilidad con Plug-n-Hack.

## Pruebas de IU

Perfect Pixel permite a los desarrolladores y diseñadores de marcado colocar una superposición de imagen semitransparente sobre el HTML desarrollado y realizar una comparación de píxeles perfectos entre ellos.

BrowserStack es una plataforma de pruebas móviles y web en la nube que permite a los desarrolladores probar sus sitios web y aplicaciones móviles en exploradores, sistemas operativos y dispositivos móviles reales bajo demanda.

## Pruebas de API

Postman es la plataforma de colaboración para el desarrollo de API. Postman simplifica cada paso de la creación de una API y optimiza la colaboración para que pueda crear mejores API.

SoapUI es una aplicación de prueba de servicio web de código abierto para Simple Object Access Protocol SOAP () y transferencias de estado representacionales (REST). Su funcionalidad abarca la inspección de servicios web; invocación, desarrollo, simulación y burla; pruebas funcionales; pruebas de carga y conformidad.

## Pruebas de automatización

Selenium está compuesto por varios componentes (API de cliente de Selenium, Selenium WebDriver), cada uno de los cuales asume una función específica como ayuda en el desarrollo de la automatización de las pruebas de aplicaciones web.
