---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---
# Aspectos destacados del parche de seguridad de agosto de 2024

Esta versión incluye los siguientes aspectos destacados:

* **Limitación de velocidad para[!DNL one-time passwords]**: las siguientes nuevas opciones de configuración del sistema ya están disponibles para habilitar la limitación de velocidad en la validación de [!DNL two-factor authentication (2FA)] [!DNL one-time password (OTP)]:

   * [!UICONTROL **Límite de intentos de reintento para autenticación de doble factor**]
   * [!UICONTROL **Tiempo de bloqueo de autenticación de doble factor (segundos)**]

  Adobe recomienda establecer un umbral para la validación de OTP 2FA a fin de limitar el número de intentos de reintento para mitigar los ataques de fuerza bruta. Consulte [Seguridad > 2FA](https://experienceleague.adobe.com/es/docs/commerce-admin/config/security/2fa) en la _Guía de referencia de configuración_ para obtener más información. <!-- AC-12095 -->

* **Rotación de clave de cifrado**: ya está disponible un nuevo comando de CLI para cambiar la clave de cifrado. Consulte el artículo de la [Solución de problemas con la rotación de clave de cifrado: CVE-2024-34102](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102) Knowledge Base para obtener más información.

* **Corrección para [CVE-2020-27511](https://nvd.nist.gov/vuln/detail/CVE-2020-27511)**: resuelve una vulnerabilidad de seguridad de [!DNL Prototype.js].<!-- AC-11936 -->

* **Corrección para [CVE-2024-39397](https://nvd.nist.gov/vuln/detail/CVE-2024-39397)**: resuelve una vulnerabilidad de seguridad de ejecución de código remoto. Esta vulnerabilidad afecta a los comerciantes que utilizan el servidor web Apache para implementaciones locales o autoalojadas. Esta corrección también está disponible como parche aislado. Consulte la [actualización de seguridad disponible para Adobe Commerce - APSB24-61](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-61) Artículo de la base de conocimiento para obtener más información.<!-- ACSD-60551 -->
