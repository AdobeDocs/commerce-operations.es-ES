---
source-git-commit: c71367c553dce66c146540389461f36eaa529bfc
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---
# Aspectos destacados del parche de seguridad de octubre de 2024

Esta versión incluye los siguientes aspectos destacados:

* **Actualización de TinyMCE**: el [editor de WYSIWYG](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/editor) del administrador ahora usa la última versión de la dependencia de TinyMCE (7.3&#x200B;).

   * TinyMCE 7.3 ofrece una experiencia de usuario mejorada, una mejor colaboración y una mayor eficiencia. TinyMCE 5 se ha eliminado en la línea de versión 2.4.8&#x200B;

   * Dado que se informó de una vulnerabilidad de seguridad ([CVE-2024-38357](https://nvd.nist.gov/vuln/detail/CVE-2024-38357)) en TinyMCE 5.10, la dependencia también se actualizó para todas las líneas de versión admitidas actualmente y se incluyó en todos los parches de seguridad de octubre de 2024:

      * 2.4.7-p3
      * 2.4.6-p8
      * 2,4,5-p10
      * 2.4.4-p11

* **Requerir actualización.js**: Adobe Commerce ahora utiliza la última versión de Requerir.js (2.3.7).

   * Dado que se notificó una vulnerabilidad de seguridad ([CVE-2024-38999](https://nvd.nist.gov/vuln/detail/CVE-2024-38999)) en Require.js 2.3.6, la dependencia también se actualizó para todas las líneas de versión admitidas actualmente y se incluyó en todos los parches de seguridad de octubre de 2024:

      * 2.4.7-p3
      * 2.4.6-p8
      * 2,4,5-p10
      * 2.4.4-p11

>[!NOTE]
>
>Estas actualizaciones son compatibles con versiones anteriores y no deben afectar a las personalizaciones y extensiones&#x200B;
