---
title: Pasos posteriores al lanzamiento
description: Utilice nuestra lista de comprobación posterior al lanzamiento para garantizar una implementación sin problemas del sitio de comercio de Adobe.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---


# Pasos posteriores al lanzamiento

Una vez que el sitio web esté activo, estas actividades se realizarán lo antes posible para garantizar que el sitio se inicie correctamente:

- Habilite la herramienta de monitorización de tiempo activo (New Relic), active las comprobaciones y supervise el sitio para asegurarse de que todos los servicios y acceso estén en verde
- Habilitar el análisis de seguridad de Adobe Commerce periódicamente
- Etiquete el clúster como activo y cree un ticket de soporte para activar la supervisión de SLA alto
- El CSE (ingeniero de éxito de los clientes) y TAM (administrador de cuentas técnicas) realizan las siguientes tareas en cuanto se completa la migración:
   - Etiquete el clúster como High SLA para el cliente de Adobe Commerce y cree un ticket de soporte para activarlo
   - Activar las comprobaciones de reino para los nombres de dominio
   - Revise el estado de supervisión y asegúrese de que todos los elementos estén en verde
   - Mantenga informadas a las partes interesadas de la duración y los parámetros de la garantía por correo electrónico en el día de lanzamiento

![Diagrama de la fase 4 del proceso de lanzamiento](../../assets/playbooks/launch-steps-4.svg)
