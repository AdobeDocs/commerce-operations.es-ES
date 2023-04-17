---
title: Información general sobre el alojamiento propio
description: Obtenga información sobre las prácticas recomendadas de alojamiento propio que debe tener en cuenta. Los temas van desde los elementos de seguridad hasta la recuperación ante desastres de muchos más. Estos temas están aquí para ayudar a una empresa que ha decidido alojar su propia versión de Adobe Commerce. Los artículos presentados no son todos inclusivos, pero deberían proporcionar una buena gama de conceptos para promover un sitio web seguro, estable y flexible.
landing-page-description: Aprenda algunos conceptos y cosas que debe tener en cuenta al alojar Adobe Commerce por su cuenta.
short-description: Aprenda estrategias y conceptos para alojar usted mismo Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: ef89ace2f03d5010384ba759e81695b6ae7e630b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Información general sobre Adobe Commerce de alojamiento propio

Al considerar el paso a una plataforma de comercio electrónico como Adobe Commerce, tiene el lujo de tener opciones. Sin embargo, con estas opciones se incluyen costos, riesgos y pasivos adicionales que considerar. El alojamiento de un sitio de comercio se puede realizar utilizando una solución empaquetada, como [Adobe Commerce en infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}, donde la infraestructura, los servidores, el correo electrónico, los certificados SSL y muchos más están preconfigurados y listos para su uso. Encontrar una buena solución de alojamiento, como Adobe Commerce en la infraestructura de la nube, facilita todo el proceso, por lo que hay razones convincentes para alojarse por su cuenta en el sitio de Comercio. Dentro de las páginas de acompañamiento, hay muchos temas que proporcionan información y orientación sobre los servicios, técnicas y conceptos que proporciona el alojamiento propio. La información aquí no es exhaustiva y no se espera que aplique todas las sugerencias. Sin embargo, estos artículos pueden ayudarle a comprender las ideas y conceptos que pueden hacer que el alojamiento propio de Adobe Commerce sea lo más estable y seguro posible.

Cuando no va con Adobe Commerce en la infraestructura de la nube, los términos utilizados son alojamiento propio o local, o incluso se utilizan in situ. local no solo significa en un centro de datos de un edificio que posee una empresa. Este término representa todo aquello que Adobe Commerce no administre como soporte en su infraestructura. Existen empresas de alojamiento que se ocupan de Adobe Commerce, que también se consideran como alojamiento propio o local.

En cuanto a Adobe Commerce y Magento Open-source, la mayoría de los consejos y sugerencias proporcionados funcionan para cualquiera de las versiones. Aunque no lo indique directamente, se espera que sea aplicable a ambos. En este tema de las opciones de alojamiento propio para Adobe Commerce, se tienen en cuenta ambas versiones. Y finalmente, la mayoría de los temas son relevantes para [Adobe Commerce en infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} se selecciona como proveedor de alojamiento.

## Conjunto de niveles terminológicos

Los siguientes términos se utilizan comúnmente en los artículos de Experience League, cuando se habla con el equipo de DevOps y cuando se trabaja con el soporte técnico de la empresa:

* **Operaciones de desarrollo** es un término que se utiliza para describir los equipos que administran la configuración, la configuración, la administración, los certificados SSL y todo lo demás sobre los servidores y servicios reales utilizados para ejecutar un sitio de Adobe Commerce. Este término se utiliza para ayudar a designar cuándo termina normalmente la responsabilidad de los desarrolladores y dónde comienza la evaluación y el soporte de un equipo de infraestructura.

* **Conceptos de seguridad** engloba varios temas y consideraciones para hacer que el código base de Adobe Commerce, los archivos y el sistema de archivos en los servidores y cualquier configuración o actualización que reduzca la superficie de ataque para muchos patrones de explotación conocidos.

* **Herramientas de monitorización** cubre algunas herramientas y servicios existentes que supervisan los sitios web de Adobe Commerce. Estas herramientas a veces pueden proporcionar sugerencias sobre cómo mejorar las cosas o descubrir problemas y vulnerabilidades de seguridad.

* **Recuperación ante desastres** ayuda a proporcionar algunos conceptos y consideraciones para el desafortunado evento de un proyecto dañado o explotado.

* **Sugerencias de rendimiento** proporcione algunas sugerencias y directrices para que la aplicación de Adobe Commerce tenga el máximo rendimiento posible.

* **Actor malo** es el término que se usa para una persona o equipo que intenta hacer algo malicioso o no autorizado. No se limita a la aplicación de comercio sino que también se extiende a la infraestructura o a cualquier componente relacionado con el sitio web.

* **Cortafuegos de aplicaciones web** (WAF) ayuda al observar cada solicitud que se dirige a la aplicación de comercio y bloquea los patrones y usos conocidos. A menudo, un WAF se utiliza junto con filtros personalizados y reglas para ayudar a administrar los ataques de DDOS.

* **Denegación de servicio distribuida** (DDoS) es un método de ataque para obligar a los servidores que ejecutan el sitio web a consumirse con solicitudes falsas con el volumen suficiente para que ya no puedan responder a solicitudes legítimas.

## ¿Qué sigue?

Estos temas no están en ningún orden o secuencia especial. Están pensados para proporcionar puntos de conversación con un ingeniero de DevOps, el arquitecto de comercio y cualquier otra persona involucrada en tomar esta importante decisión de dónde y cómo alojar Adobe Commerce.

{{$include /help/_includes/hosting-related-links.md}}
