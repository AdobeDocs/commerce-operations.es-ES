---
title: 'MDVA-39305: Problema de inicio de sesión con Google reCAPTCHA habilitado'
description: Aplique el parche MDVA-39305 para solucionar el problema de Adobe Commerce en el que los clientes registrados no pueden iniciar sesión cuando Google reCAPTCHA está habilitado.
feature: Console
role: Admin
exl-id: c40fd84a-73dc-42bd-8cda-58738615fbba
source-git-commit: 007fcb1308ba2c5b42755ee4c4c2ca598eb0e62e
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-39305: Problema de inicio de sesión con Google reCAPTCHA habilitado

>[!NOTE]
>
>Este parche se ha actualizado y la última ID del parche es MDVA-39305-V3. El nuevo parche se crea para las versiones de Adobe Commerce 2.4.4, 2.4.5-p2 y 2.4.7. Para obtener más información, consulte el artículo del parche [MDVA-39305-V3](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/mdva-39305-v3-login-issue-with-enabled-google-recaptcha).

El parche MDVA-39305 soluciona el problema de que los clientes registrados no pueden iniciar sesión cuando Google reCAPTCHA está habilitado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1. El ID del parche es MDVA-39305. Tenga en cuenta que el problema se solucionó en las versiones 2.4.4 y 2.4.7 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.4.2-p1, 2.4.3-p3, 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1-p1 - 2.4.3-p3, 2.4.4-p1 - 2.4.4-p5, 2.4.5 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los clientes registrados no pueden iniciar sesión con el reCAPTCHA de Google habilitado.

<u>Pasos a seguir</u>:

1. Vaya a **Tienda** > **Configuración** > **Seguridad** > **Tienda Google reCAPTCHA** y habilite **Google reCAPTCHA**.
1. Vaya a **FrontEnd**.
1. Abra **Developer Tool Console** en el explorador.

<u>Resultados esperados</u>:

No hay advertencias de CSP en la consola.

<u>Resultados reales</u>:

Advertencias de CSP en la consola.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
