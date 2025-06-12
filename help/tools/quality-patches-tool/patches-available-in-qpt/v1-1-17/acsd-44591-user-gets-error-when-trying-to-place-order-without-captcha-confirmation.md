---
title: 'ACSD-44591: Errores al realizar un pedido sin confirmación de CAPTCHA'
description: El parche ACSD-44591 resuelve el problema en el que el usuario obtiene errores al intentar realizar un pedido sin confirmación CAPTCHA.
feature: Orders
role: Admin
exl-id: 4b8a8090-a2ba-428c-9a04-7c0842e94a6f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-44591: Errores al realizar un pedido sin confirmación de CAPTCHA

El parche ACSD-44591 resuelve el problema en el que el usuario obtiene errores al intentar realizar un pedido sin confirmación CAPTCHA.
Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17. El ID del parche es ACSD-44591. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario recibe errores al intentar realizar un pedido sin confirmación CAPTCHA.

<u>Pasos a seguir</u>:

1. Configure el Google ReCaptcha v2 (no soy un robot).
1. Active ReCaptcha para el cierre de compra.
1. Intente realizar un pedido sin hacer clic en ReCaptcha.
1. Una vez que reciba el mensaje de error por la falta de ReCaptcha (*Error de validación de ReCaptcha, vuelva a intentarlo*), haga clic en **ReCaptcha** e intente realizar un pedido.

<u>Resultados esperados</u>:

El pedido no se realizará con un ReCaptcha incorrecto.

<u>Resultados reales</u>:

Se obtienen los siguientes errores:

* *Error de validación de ReCaptcha, inténtelo de nuevo*
* *No existe ese carro con id = 1*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
