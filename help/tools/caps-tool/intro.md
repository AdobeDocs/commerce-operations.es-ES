---
title: '[!DNL Adobe Commerce Patching Automation]'
description: Obtenga información acerca de  [!DNL Adobe Commerce Patching Automation], sus usos, cómo tener acceso a él y prácticas recomendadas para aplicar parches automatizados
source-git-commit: d9f6fc714332638ae1dcfa92ac8abe274efe8a0b
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# [!DNL Adobe Commerce Patching Automation]

[!DNL Adobe Commerce Patching Automation] es una herramienta que automatiza el proceso de aplicar y revertir parches para Adobe Commerce en entornos de nube. Ofrece a los administradores de proyectos de Commerce un flujo de trabajo optimizado para aplicar y revertir parches. La validación y las comprobaciones de estado integradas ayudan a garantizar que los entornos de la nube permanezcan estables y seguros.

Esta guía está diseñada para comerciantes y socios de Adobe Commerce Cloud que deseen optimizar su proceso de aplicación de parches, reducir el riesgo de problemas relacionados con los parches, mejorar la seguridad y estabilidad de su entorno y automatizar las operaciones rutinarias de parches.

## [!DNL Patching Automation] temas

* **[Cómo acceder](access.md)**
* **[Resumen del flujo de trabajo](workflow.md)**
* **[Integración de GitHub](github-integration.md)**
* **[Prácticas recomendadas](best-practices.md)**
* **[Solución de problemas](troubleshooting.md)**

## Información general de herramientas

* **Interfaz de usuario**
  * Visualización de la disponibilidad y el estado de los parches en tiempo real para combinaciones específicas de proyecto y entorno
  * Información completa del estado de aplicación de parches que muestra el progreso, los errores y cualquier otro mensaje relevante
  * [!UICONTROL Patch Management Dashboard] para:
    * Visualización de parches disponibles
    * Aplicación de parches con un solo clic
    * Reversión de parches aplicados anteriormente
    * Monitorización del estado y los resultados de las operaciones de parche

* **Servicio de aplicación automatizada de parches con flujo de trabajo estructurado**
  * **Comprobación preliminar**: valida la compatibilidad de parches y la preparación del entorno
  * **Parches**: Aplica o revierte parches automáticamente en entornos de integración
  * **Validación**: realiza una comprobación de estado para confirmar que la aplicación se inicia y que se puede acceder a las conexiones de caché y base de datos

* **Características de seguridad**
  * Valida la compatibilidad del parche antes de la aplicación
  * Aplica primero el parche en un entorno de integración temporal (confirmando que se implementa correctamente y que pasa una comprobación de estado) antes de combinarlo en el entorno de destino y, a continuación, realiza una comprobación de estado final inmediatamente después de la implementación
  * Aplica parches a la carpeta `m2-hotfixes` con eliminación automática durante la reversión

## Integraciones con Adobe Commerce Cloud

[!DNL Patching Automation] está totalmente integrado con la infraestructura de Adobe Commerce Cloud y funciona sin problemas con los entornos de nube existentes. Utiliza funciones nativas de la nube para obtener un rendimiento óptimo, proporciona un registro y una monitorización detallados, y se integra con las herramientas de soporte de Adobe Commerce Cloud.

## Tutorial de vídeo

Obtenga información acerca de [!DNL Adobe Commerce Patching Automation] y cómo esta herramienta ayuda a los usuarios a buscar y aplicar rápidamente parches de seguridad. En el siguiente vídeo se explica cómo acceder a él a través del panel de herramientas de análisis de todo el sitio (SWAT), cómo elegir el proyecto y el entorno, y cómo aplicar parches con un solo clic.

>[!VIDEO](https://video.tv.adobe.com/v/3476250/?captions=spa&learn=on&enablevpops)

## Casos de uso comunes

* **Parches de seguridad**: aplique rápidamente las actualizaciones de seguridad críticas
* **Reversión de parche**: revierta de forma segura los parches problemáticos aplicados a través del servicio
* **Cumplimiento de la seguridad**: mantenga los estándares de seguridad con parches automatizados
* **Estabilidad operativa**: confirma que la aplicación se inicia y pasa una comprobación de estado después de cada operación de revisión
