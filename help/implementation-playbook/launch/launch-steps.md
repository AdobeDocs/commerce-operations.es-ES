---
title: Pasos del inicio
description: Utilice nuestra lista de comprobación de inicio para garantizar una implementación sin problemas del sitio de Adobe Commerce.
exl-id: d7807b2f-85c0-4e3e-a473-c65dbec44d28
feature: Configuration, Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Pasos del inicio

Después de probar y completar la lista de comprobación previa al lanzamiento, podemos iniciar los pasos finales para el lanzamiento en el momento de la migración. Estos pasos incluyen la introducción de tickets de lanzamiento del sitio (lanzamiento), el corte del acceso y, finalmente, la prueba de las tiendas cuando están activas.

El personal de soporte de Adobe Commerce trabajará con usted durante todo el proceso, comprobando el estado y ayudando a abordar cualquier pregunta o problema que se produzca. Todos los problemas deben seguirse con tickets para capturar mejor lo que ha sucedido y cómo se ha resuelto. Cuando empiece a implementar continuas iteraciones de actualizaciones en la tienda iniciada, es posible que vuelvan a producirse problemas similares. Estos tickets pueden ayudar a identificar los problemas y a ajustar las tareas de implementación.

- Configurar la aplicación para la URL base
   - Cambiar DNS al nuevo sitio
   - Acceso al servicio DNS
   - Actualice los registros A y CNAME para los dominios y nombres de host
   - Espere a que pase el tiempo TTL y acceda a su tienda

- Pruebas completas en producción
   - Verificación de todas las funciones del sitio web
   - Comprobando caché de CDN
   - Verificación de todos los servicios integrados de terceros
   - Verificación de todos los sistemas de terceros

- Póngase en contacto con la línea directa de Adobe Commerce por si algún problema bloquea el lanzamiento

![Diagrama que muestra la fase 3 del proceso de lanzamiento](../../assets/playbooks/launch-steps-3.svg)
