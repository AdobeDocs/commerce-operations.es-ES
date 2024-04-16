---
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 1%

---
# Datos confidenciales

Adobe Commerce utiliza su clave de cifrado para cifrar lo siguiente:

* Información de tarjeta de crédito
* Nombres de usuario y contraseñas especificados en la configuración de administración (por ejemplo, inicios de sesión en puertas de enlace de pago)
* Valores CAPTCHA enviados a través de la red

Adobe Commerce do *no* cifrar:

* Nombres de usuario y contraseñas administrativos y de clientes (estas contraseñas tienen un cifrado hash)
* Dirección
* Número de teléfono
* Otros tipos de información de identificación personal excepto números de tarjetas de crédito
