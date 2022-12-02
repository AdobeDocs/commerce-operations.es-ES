---
title: Almacenamiento remoto para comercio en infraestructura en la nube
description: Consulte las instrucciones sobre cómo configurar el almacenamiento remoto para Adobe Commerce en la infraestructura de la nube.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Configuración del almacenamiento remoto para Commerce en la infraestructura de Cloud

Si decide utilizar la solución de almacenamiento remoto con un proyecto de infraestructura en la nube de Adobe Commerce, use la variable [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) en la sección _Fly_ documentación para asegurarse de que la Optimización de imágenes Fough funciona con AWS S3.

Prepárese con su [Credenciales de formato](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). En los proyectos Pro, utilice SSH para conectarse al servidor y obtener las credenciales de la variable `/mnt/shared/fastly_tokens.txt` archivo. Los entornos de ensayo y producción tienen credenciales únicas. Debe obtener las credenciales de cada entorno.

Continúe configurando el almacenamiento remoto para proyectos en la nube con las siguientes tareas:

1. Configure un [Integración de back-end más rápida](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Crear lógica de VCL para [Autenticación de AWS S3](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Crear lógica de VCL para [solicitudes de back-end al compartimento de AWS S3](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
