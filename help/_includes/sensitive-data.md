---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---
# Datos confidenciales

Adobe Commerce y Magento Open Source usan su clave de cifrado para cifrar lo siguiente:

* Información de tarjeta de crédito
* Nombres de usuario y contraseñas especificados en la configuración de administración (por ejemplo, inicios de sesión en puertas de enlace de pago)
* Valores CAPTCHA enviados a través de la red

Adobe Commerce y Magento Open Source lo hacen *no* cifrar:

* Nombres de usuario y contraseñas administrativos y de clientes (estas contraseñas tienen un cifrado hash)
* Dirección
* Número de teléfono
* Otros tipos de información de identificación personal excepto números de tarjetas de crédito
