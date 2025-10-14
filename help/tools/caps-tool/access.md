---
title: Cómo acceder a  [!DNL Cloud Automation Patching Service (CAPS)]
description: Obtenga información sobre cómo acceder y utilizar  [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: ca388bd78affd4def19a5539d8529f2563d35e8c
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# Cómo acceder a [!DNL Cloud Automation Patching Service (CAPS)]

## Requisitos previos

[!DNL CAPS] utiliza el control de acceso basado en roles de Adobe Commerce Cloud. Su nivel de acceso en Cloud Console determina lo que puede hacer con [!DNL CAPS].

### Quién puede usar [!DNL CAPS]

* **Administrador de proyecto**: puede aplicar o revertir parches en todos los entornos
* **Colaborador**: puede aplicar o revertir parches en los entornos asignados
* **Visor**: solo se puede ver el proyecto y los entornos, no se permiten acciones

### Solicitud de acceso a un proyecto

Si no ve ningún proyecto en la interfaz de usuario de [!DNL CAPS], debe solicitar acceso a la persona adecuada:

* Póngase en contacto con el propietario de la cuenta o el administrador del proyecto
* Ellos le otorgarán la función adecuada a través de la consola de Cloud
* Una vez concedido el acceso, puede iniciar sesión en la consola de Cloud para usar [!DNL CAPS]

>[!NOTE]
>
>[!DNL CAPS] sigue el mismo modelo de permisos que Adobe Commerce Cloud, por lo que el nivel de acceso en Cloud Console determina lo que puede hacer con [!DNL CAPS].

## Acceder a [!DNL CAPS]

La herramienta CAPS está disponible en el panel de herramientas de análisis de todo el sitio en [https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/). En la pestaña Automatización de parches, puede seleccionar el proyecto y el entorno.

1. Vaya a la herramienta de análisis de todo el sitio en [https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/).
1. Haga clic en la ficha [!UICONTROL Patching Automation] de la interfaz.
1. Seleccione el proyecto y el entorno en el que desea aplicar los parches.
1. Revise los parches disponibles y su estado de compatibilidad.
1. Seleccione parches para aplicar o revertir.

## Acceso al entorno de producción

Para entornos de producción, se aplican garantías adicionales:

* **Modo de mantenimiento** - Debe estar habilitado
* **Trabajos cron** - Deben deshabilitarse
* **Cuadro de diálogo de confirmación** - Debe completarse antes de continuar

>[!IMPORTANT]
>
>La aplicación de parches en el entorno de producción requiere una preparación adecuada y medidas de seguridad para evitar interrupciones accidentales.

## Temas relacionados

* [Introducción a CAPS](intro.md)
* [Flujo de trabajo](workflow.md)
* [Prácticas recomendadas](best-practices.md)
* [Resolución de problemas](troubleshooting.md)
