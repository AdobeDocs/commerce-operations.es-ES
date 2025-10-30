---
title: '[!DNL Cloud Automation Patching Service (CAPS)]'
description: Obtenga información acerca de  [!DNL Cloud Automation Patching Service (CAPS)], sus usos, cómo tener acceso a él y prácticas recomendadas para aplicar parches automatizados
hide: true
hidefromtoc: true
source-git-commit: 4bb2d597e93379dbe81bae100ccc0b94b39acf26
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# [!DNL Cloud Automation Patching Service (CAPS)]

[!DNL Cloud Automation Patching Service] ([!DNL CAPS]) es una herramienta que automatiza el proceso de aplicar y revertir parches para Adobe Commerce en entornos de nube. Ofrece a los administradores de proyectos de Commerce un flujo de trabajo optimizado para aplicar y revertir parches que incluye validación y comprobaciones de estado integradas para garantizar que los entornos de la nube permanezcan estables y seguros.

Esta guía está diseñada para comerciantes y socios de Adobe Commerce Cloud que deseen optimizar su proceso de aplicación de parches, reducir el riesgo de problemas relacionados con los parches, mejorar la seguridad y estabilidad de su entorno y automatizar las operaciones rutinarias de parches.

## [!DNL CAPS] temas

* **[Cómo acceder](access.md)**
* **[Flujo de trabajo](workflow.md)**
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
   * **Validación**: realiza comprobaciones de estado y garantiza que las funcionalidades críticas no se vean afectadas

* **Características de seguridad**
   * Crea entornos de integración temporales para realizar pruebas
   * Valida la compatibilidad del parche antes de la aplicación
   * Proporciona reversión automática en los errores de validación
   * Aplica parches a la carpeta `m2-hotfixes` con eliminación automática durante la reversión

## Integraciones con Adobe Commerce Cloud

[!DNL CAPS] está totalmente integrado con la infraestructura de Adobe Commerce Cloud y funciona sin problemas con los entornos de nube existentes. Utiliza funciones nativas de la nube para obtener un rendimiento óptimo, proporciona un registro y una monitorización detallados, y se integra con las herramientas de soporte de Adobe Commerce Cloud.

## Tutorial de vídeo

Obtenga información acerca del servicio de parches automatizados de Adobe Cloud y cómo esta herramienta ayuda a los usuarios a encontrar y aplicar rápidamente parches de seguridad. El siguiente vídeo explica cómo acceder a él a través del panel SWAT, elegir el proyecto y el entorno, y aplicar parches con un solo clic.

>[!VIDEO](https://video.tv.adobe.com/v/3476247/?learn=on&enablevpops)

## Casos de uso comunes

* **Parches de seguridad**: aplique rápidamente las actualizaciones de seguridad críticas
* **Reversión de revisión**: revierta de forma segura las revisiones problemáticas aplicadas mediante [!DNL CAPS]
* **Cumplimiento de la seguridad**: mantenga los estándares de seguridad con parches automatizados
* **Estabilidad operativa**: garantice la estabilidad del entorno mediante la validación automatizada.
