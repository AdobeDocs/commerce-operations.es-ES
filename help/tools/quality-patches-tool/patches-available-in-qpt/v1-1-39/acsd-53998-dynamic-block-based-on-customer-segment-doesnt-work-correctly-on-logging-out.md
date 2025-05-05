---
title: 'ACSD-53998: El bloque dinámico basado en el segmento del cliente funciona incorrectamente después de cerrar sesión'
description: Aplique el parche ACSD-53998 para solucionar el problema de Adobe Commerce en el que un bloque dinámico basado en un segmento de clientes no funciona correctamente después de cerrar sesión en una cuenta de cliente.
feature: Customers, Page Builder, Personalization
role: Admin, Developer
exl-id: aa7001c7-bb35-4e5c-8ac9-3ed84b75d7cd
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-53998: El bloque dinámico basado en el segmento del cliente funciona incorrectamente después de cerrar sesión

El parche ACSD-53998 corrige el problema de que un bloque dinámico basado en un segmento de clientes no funciona correctamente después de cerrar sesión en una cuenta de cliente. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.39. El ID del parche es ACSD-53998. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2 - 2.4.4-p6, 2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un bloque dinámico basado en un segmento de cliente no funciona correctamente después de cerrar sesión en una cuenta de cliente.

<u>Requisitos previos</u>:

Instale y habilite [!DNL Page Builder] módulos.

<u>Pasos a seguir</u>:

1. Cree dos segmentos de cliente sin ninguna condición.
1. Cree dos bloques dinámicos para cada segmento.
1. Cree un bloque que incluya los dos bloques dinámicos como [!DNL Page Builder] bloques dinámicos.
1. Cree un widget que incluya el bloque anterior y haga que el bloque sea visible en la sección de pie de página de todas las páginas.
1. Borre las cachés.
1. Abra la página principal.
1. Inicie sesión como cliente.
1. Cerrar sesión.

<u>Resultados esperados</u>:

El banner creado para los clientes que iniciaron sesión no se muestra para los usuarios invitados.

<u>Resultados reales</u>:

El banner creado para el segmento de clientes conectados se muestra incluso después de cerrar sesión en la cuenta de cliente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
