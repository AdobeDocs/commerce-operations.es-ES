---
source-git-commit: 6ca34e8713f4f138961786de206cd360f0bc1be7
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---
# Aspectos destacados del parche de seguridad de febrero de 2025

Esta versión incluye los siguientes aspectos destacados:

* **Administración de claves de cifrado y recifrado de datos**: se ha rediseñado la administración de claves de cifrado para mejorar la facilidad de uso y eliminar las limitaciones y los errores anteriores.<!-- AC-12679 -->

  Los nuevos comandos CLI ya están disponibles para [cambiar](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key) claves y [volver a cifrar](https://developer.adobe.com/commerce/php/development/security/data-encryption/) ciertas configuraciones del sistema, pagos y datos de campos personalizados. En esta versión ya no se admite el cambio de claves en la IU de administración. Debe utilizar los comandos CLI.

* **Corrección para [CVE-2025-24434](https://nvd.nist.gov/vuln/detail/CVE-2025-24434)**: resuelve una vulnerabilidad de autorización.

  Esta corrección también está disponible como parche aislado. Consulte el [artículo de la base de conocimiento](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08) para obtener más información.<!-- AC-12755 -->

* **Degradación de versión de TinyMCE**: la dependencia de TinyMCE se ha degradado de la versión 7 a la 6.8.5 para resolver problemas de compatibilidad de licencias.

  Este cambio garantiza el cumplimiento continuo, mientras que Adobe evalúa un editor WYSIWYG de código abierto alternativo.
