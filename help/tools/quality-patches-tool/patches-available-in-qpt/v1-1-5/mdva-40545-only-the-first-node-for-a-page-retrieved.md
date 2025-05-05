---
title: 'MDVA-40545: Solo se recupera el primer nodo de una página'
description: El parche MDVA-40545 resuelve el problema de que solo se recupera el primer nodo de una página, aunque haya más de un nodo para la misma página. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5. El ID del parche es MDVA-40545. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: CMS, Cache
role: Admin
exl-id: f87344e9-5a63-4c38-af2b-1500ef053dec
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-40545: Solo se recupera el primer nodo de una página

El parche MDVA-40545 resuelve el problema de que solo se recupera el primer nodo de una página, aunque haya más de un nodo para la misma página. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5. El ID del parche es MDVA-40545. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Solo se recupera el primer nodo de una página, aunque haya más de un nodo para la misma página.

<u>Pasos a seguir</u>:

1. En el Panel de administración, vaya a **Jerarquía** y agregue dos elementos/nodos de menú.
1. Agregue la misma página de CMS a cada nodo.
1. Borre la caché y compruebe el front-end.
1. Compruebe los vínculos y las rutas de exploración del primer submenú añadido.
1. Compruebe los vínculos y las rutas de exploración para el segundo submenú añadido.

<u>Resultados esperados</u>:

Las rutas de exploración y el vínculo del segundo submenú son relevantes para el segundo nodo.

<u>Resultados reales</u>:

Las rutas de exploración y los vínculos del segundo submenú son los mismos que el del primero.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
