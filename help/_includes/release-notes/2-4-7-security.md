---
source-git-commit: 4ed23e2a8319ff97f8206f752cf1cbe2e73ea5c5
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---
# 2.4.7 mejoras de seguridad

* **Se agregó compatibilidad con Integridad de los subrecursos (SRI)** cumplir con los requisitos de PCI 4.0 para la verificación de la integridad de las secuencias de comandos en las páginas de pago. La compatibilidad con la Integridad de los subrecursos (SRI) proporciona hashes de integridad para todos los recursos JavaScript que residen en el sistema de archivos local. La función SRI predeterminada solo se implementa en las páginas de pago de las áreas de administración y tienda. Sin embargo, los comerciantes pueden ampliar la configuración predeterminada a otras páginas. Consulte [Integridad de subrecursos](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) en el _Guía para desarrolladores de Commerce PHP_.<!--AC-1153-->

* **Cambios en la Política de seguridad de contenido (CSP)**: actualizaciones y mejoras de configuración de las Políticas de seguridad de contenido (CSP) de Adobe Commerce para cumplir con los requisitos de PCI 4.0. Para obtener más información, consulte [Políticas de seguridad de contenido](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) en el _Guía para desarrolladores de Commerce PHP_. <!--AC-11513-->

   * La configuración predeterminada CSP para páginas de pago para áreas de administración y tienda de Commerce es ahora `restrict` modo. Para las demás páginas, la configuración predeterminada es `report-only` modo.  En las versiones anteriores a 2.4.7, el CSP se configuraba en `report-only` modo para todas las páginas.

   * Se ha agregado un proveedor nonce para permitir la ejecución de scripts en línea en un CSP. El proveedor nonce facilita la generación de cadenas nonce únicas para cada solicitud. A continuación, las cadenas se adjuntan al encabezado CSP.

   * Se han añadido opciones para configurar URI personalizados para que informen de infracciones de CSP en la página Crear pedido de la página Administrador y Cierre de compra de la tienda. Puede agregar la configuración desde el Administrador o agregando el URI al `config.xml` archivo.

     >[!NOTE]
     >
     >Actualizar la configuración de CSP a `restrict` Este modo podría bloquear los scripts en línea existentes en las páginas de pago de la administración y de la tienda, lo que provoca el siguiente error en el explorador cuando se carga una página: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Corrija estos errores actualizando la configuración de la lista blanca para permitir los scripts necesarios. Consulte [Solución de problemas](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) en el _Guía para desarrolladores de Commerce PHP_.
