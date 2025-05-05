---
source-git-commit: db78f1339aaa8fab11a5ef7aa4d1fe17d0c3fb0e
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---
# Aspectos destacados del parche de seguridad de febrero de 2025

Esta versión incluye lo siguiente destacado:

* **Administración de claves de cifrado y recifrado de datos**: se ha rediseñado la administración de claves de cifrado para mejorar la facilidad de uso y eliminar las limitaciones y los errores anteriores.<!-- AC-12679 -->

  Los nuevos comandos CLI ya están disponibles para [cambiar](https://experienceleague.adobe.com/es/docs/commerce-admin/systems/security/encryption-key) claves y [volver a cifrar](https://developer.adobe.com/commerce/php/development/security/data-encryption/) ciertas configuraciones del sistema, pagos y datos de campos personalizados. En esta versión ya no se admite el cambio de claves en la IU de administración. Debe utilizar los comandos CLI.

* **Corrección para [CVE-2025-24434](https://nvd.nist.gov/vuln/detail/CVE-2025-24434)**: resuelve una vulnerabilidad de autorización.

  Esta corrección también está disponible como parche aislado. Consulte el [artículo de la base de conocimiento](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08) para obtener más información.<!-- AC-12755 -->
