---
source-git-commit: 5ef5c2dedbbef2858a6bbc6c0aca13fd9adae0c8
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# Revisiones incluidas en los parches de seguridad de octubre (excepto 2.4.4)

Esta versión incluye una revisión para resolver un problema con la pasarela de pago del Braintree.

El sistema ahora incluye los campos necesarios para cumplir con los requisitos del mandato VISA 3DS cuando se utiliza el Braintree como pasarela de pago. Esto garantiza que todas las transacciones cumplan con los últimos estándares de seguridad establecidos por VISA. Anteriormente, estos campos adicionales no se incluían en la información de pago enviada, lo que podría haber llevado al incumplimiento de los nuevos requisitos de VISA.

<!--
BUNDLE-3360
-->