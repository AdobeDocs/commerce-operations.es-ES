---
title: Información general sobre el alojamiento propio
description: Conozca las prácticas recomendadas sobre el alojamiento propio que debe tener en cuenta. Los temas van desde los elementos de seguridad, hasta la recuperación ante desastres y muchos más. Estos temas están aquí para ayudar a una empresa que ha decidido alojar su propia versión de Adobe Commerce. Los elementos presentados no son inclusivos, pero deben proporcionar una buena gama de conceptos para promover un sitio web seguro, estable y resistente.
landing-page-description: Aprenda algunos conceptos y cosas a tener en cuenta al alojar Adobe Commerce por su cuenta.
short-description: Aprenda estrategias y conceptos para alojar Adobe Commerce usted mismo.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 1c63d082-c6fb-4795-81cd-75d097c03e6b
feature: Install
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---

# Información general sobre el alojamiento propio de Adobe Commerce

Cuando considere la posibilidad de pasar a una plataforma de comercio electrónico como Adobe Commerce, puede darse el lujo de elegir entre varias opciones. Sin embargo, con estas opciones vienen costos, riesgos y pasivos adicionales a considerar. Alojar un sitio Commerce se puede hacer con una solución empaquetada, como [Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}, donde la infraestructura, los servidores, el correo electrónico, los certificados SSL y muchos más están preconfigurados y listos para usar. Encontrar una buena solución de alojamiento, como Adobe Commerce en la infraestructura en la nube, facilita todo el proceso. Existen razones de peso para alojar su sitio Commerce de forma automática. Dentro de las páginas que lo acompañan, hay muchos temas que proporcionan perspectiva y orientación sobre los servicios, técnicas y conceptos que proporciona el alojamiento propio. La información aquí no es exhaustiva y no se espera que implemente todas las sugerencias. Sin embargo, estos artículos pueden ayudarle a comprender las ideas y los conceptos que pueden hacer que el alojamiento propio de Adobe Commerce sea lo más estable y seguro posible.

Cuando no utiliza Adobe Commerce en una infraestructura en la nube, los términos utilizados son alojamiento propio o local, o incluso local. Local no solo significa en un centro de datos en un edificio que posee una empresa. Este término representa todo lo que no sea soporte administrado por Adobe Commerce en su infraestructura. Hay empresas de alojamiento web que se ocupan de Adobe Commerce y también se consideran autoalojadas o locales.

En cuanto a Adobe Commerce y Magento Open-source, la mayoría de los consejos y sugerencias proporcionados funcionan para cualquiera de las versiones. Aunque no lo indique directamente, se espera que sea aplicable a ambos. Dentro de este tema de opciones de alojamiento propio para Adobe Commerce, se tienen en cuenta ambas versiones. Y, por último, la mayoría de los temas que son relevantes para [Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} se ha seleccionado como proveedor de alojamiento.

## Nivel de terminología establecido

Los siguientes términos se utilizan comúnmente en todos los artículos de Experience League, cuando se habla con el equipo de DevOps y se trabaja con el soporte de la compañía:

* **DevOps** es un término que se usa para describir a los equipos que administran la instalación, configuración, administración, certificados SSL del servidor y todo lo demás acerca de los servidores y servicios que se usan para ejecutar un sitio de Adobe Commerce. Este término se utiliza para ayudar a designar cuándo suele finalizar la responsabilidad de un desarrollador y dónde comienza la evaluación y la asistencia de un equipo de infraestructura.

* **Conceptos de seguridad** incluyen varios temas y consideraciones para crear la base de código, los archivos y el sistema de archivos de Adobe Commerce en los servidores, así como cualquier configuración o actualización que reduzca la superficie de ataque para muchos patrones de ataque conocidos.

* **Herramientas de supervisión** cubre algunas herramientas y servicios que supervisan sitios web de Adobe Commerce. Estas herramientas a veces pueden proporcionar sugerencias sobre cómo mejorar las cosas o descubrir problemas y vulnerabilidades de seguridad.

* **Recuperación ante desastres** ayuda a proporcionar algunos conceptos y consideraciones para el desafortunado evento de un proyecto dañado o explotado.

* **Consejos de rendimiento** proporciona algunos consejos y sugerencias profesionales para que la aplicación de Adobe Commerce sea lo más eficaz posible.

* **Actor incorrecto** es el término que se usa para referirse a una persona o equipo que intenta hacer algo malintencionado o no autorizado. No se limita a la aplicación de comercio, sino que también se extiende a la infraestructura o cualquier componente relacionado con el sitio web.

* **Firewall de aplicaciones web** (WAF) ayuda a observar cada solicitud que se dirige a la aplicación de comercio y bloquea los patrones y vulnerabilidades conocidos. A menudo, se utiliza un WAF junto con filtros y reglas personalizados para ayudar a administrar los ataques de DDOS.

* **Denegación de servicio distribuida** (DDoS) es un método de ataque para forzar que los servidores que ejecutan el sitio web se consuman con solicitudes falsas con el volumen suficiente como para que ya no puedan responder a solicitudes legítimas.

## ¿Qué sigue?

Estos temas no están en ningún orden o secuencia especial. Están pensados para proporcionar puntos de conversación con un ingeniero de DevOps, el arquitecto de Commerce y cualquier otra persona que participe en la toma de esta importante decisión sobre dónde y cómo alojar Adobe Commerce.

{{$include /help/_includes/hosting-related-links.md}}
