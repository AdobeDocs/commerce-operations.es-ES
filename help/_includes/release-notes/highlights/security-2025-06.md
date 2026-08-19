---
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---
# Aspectos destacados del parche de seguridad de junio de 2025

Esta versión incluye los siguientes aspectos destacados:

* **Mejora del rendimiento de la API**: resuelve la degradación del rendimiento en los extremos de API web asincrónicos masivos que se introdujeron después de la revisión de seguridad anterior.<!-- AC-14078 -->

* **Corrección de acceso de bloques de CMS**: resuelve un problema en el cual los usuarios administradores con permisos restringidos (como acceso de solo comercialización) no podían ver la página de listado [!UICONTROL CMS Blocks].

  Anteriormente, estos usuarios encontraban un error debido a la falta de parámetros de configuración después de instalar las revisiones de seguridad anteriores.<!-- AC-14087 -->

* **Compatibilidad con límites de cookies**: resuelve un cambio incompatible con versiones anteriores que implica la constante `MAX_NUM_COOKIES` en el marco de trabajo. Esta actualización restaura el comportamiento esperado y garantiza la compatibilidad de las extensiones o personalizaciones que interactúan con los límites de las cookies.<!-- AC-14475 -->

* **Operaciones asincrónicas**: operaciones asincrónicas restringidas para anular pedidos de clientes anteriores.<!-- AC-13917 -->

* **Corrección para CVE-2025-47110**: resuelve una vulnerabilidad de las plantillas de correo electrónico.<!-- AC-14695 -->

>[!BEGINSHADEBOX]

La corrección para CVE-2025-47110 también está disponible como parche aislado. Consulte el [artículo de la Base de conocimiento](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-27181) para obtener detalles.

>[!ENDSHADEBOX]