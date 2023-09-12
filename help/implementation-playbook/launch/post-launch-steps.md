---
title: Pasos posteriores al lanzamiento
description: Utilice nuestra lista de comprobación posterior al lanzamiento para garantizar una implementación sin problemas del sitio de Adobe Commerce.
exl-id: 0c3162d9-6475-4b34-9278-e5aea39bd0f9
feature: Deploy
source-git-commit: ce41158f900fad27e3e7b8157f5c64ac988bbabf
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Pasos posteriores al lanzamiento

Una vez que el sitio web esté activo, estas actividades se realizarían lo antes posible para garantizar que el sitio se haya iniciado correctamente:

- Habilite la herramienta de monitorización del tiempo de actividad (New Relic), active las comprobaciones y supervise el sitio para asegurarse de que todos los servicios y accesos estén en verde
- Activar análisis de seguridad de Adobe Commerce periódicamente
- Etiquete el clúster como activo y cree un ticket de asistencia para activar la monitorización de alto nivel de SLA
- El CSE (ingeniero de éxito del cliente) y TAM (administrador técnico de cuentas) realizan las siguientes tareas en cuanto se completa el cambio:
   - Etiquete el clúster como Alto SLA para el cliente de Adobe Commerce y cree un ticket de asistencia para activarlo
   - Activar el **interno** PKingdom comprueba los nombres de dominio (el acceso público a PKingdom no está disponible)
   - Revise el estado de monitorización y asegúrese de que todos los elementos estén en verde
   - Mantenga a las partes interesadas informadas por correo electrónico de la duración y los parámetros de la garantía en el día de lanzamiento

![Diagrama que muestra la fase 4 del proceso de lanzamiento](../../assets/playbooks/launch-steps-4.svg)
