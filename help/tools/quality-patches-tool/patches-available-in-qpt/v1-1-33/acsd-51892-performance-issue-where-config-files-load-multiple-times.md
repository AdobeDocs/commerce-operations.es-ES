---
title: "ACSD-51892: Problema de rendimiento donde los archivos de configuración se cargan varias veces"
description: Aplique el parche ACSD-51892 para solucionar el problema de rendimiento de Adobe Commerce, donde los archivos de configuración se cargan varias veces durante la implementación.
feature: Observability
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51892: Problema de rendimiento donde los archivos de configuración se cargan varias veces

La revisión ACSD-51892 corrige el problema de rendimiento que se produce al cargar los archivos `app/etc/env.php` y `app/etc/config.php` cada vez que se accede a los valores de configuración de implementación dentro de una única solicitud. La lectura excesiva de archivos ejerce una presión sobre el sistema, lo que provoca un deterioro en el rendimiento general. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.33. El ID del parche es ACSD-51892. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6-p2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Hay un problema de rendimiento en el que los archivos de configuración se cargan varias veces.

<u>Pasos a seguir</u>:

1. Realice la implementación o actualización a Adobe Commerce 2.4.6 o posterior.
1. Compruebe los registros del sistema de archivos para obtener acceso a los archivos `app/etc/env.php` y `app/etc/config.php` mientras se ejecuta la implementación.

<u>Resultados esperados</u>:

La implementación se realiza correctamente dentro del marco de tiempo normal.

<u>Resultados reales</u>:

* Los servidores tienen dificultades para responder a cualquier comando que introduzca. Esto provoca *Error 503 de tiempo de espera de primer byte* al acceder al sitio web.
* Hay varias entradas en los archivos de registro con acceso a `app/etc/env.php` y `app/etc/config.php` archivos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
