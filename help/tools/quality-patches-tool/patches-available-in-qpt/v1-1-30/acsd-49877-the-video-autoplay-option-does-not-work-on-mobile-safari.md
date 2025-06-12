---
title: 'ACSD-49877: la reproducción automática de vídeo no funciona en dispositivos móviles [!DNL Safari]'
description: Aplique el parche ACSD-49877 para corregir el problema de Adobe Commerce en el que la opción de reproducción automática de vídeo no funciona en dispositivos móviles [!DNL Safari] cuando el vídeo está vinculado directamente a un archivo de vídeo remoto.
feature: CMS
role: Admin
exl-id: aa2557e2-4bed-4004-b9bc-36c59f1e9cdc
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-49877: la reproducción automática de vídeo no funciona en el móvil [!DNL Safari]

ACSD-49877 corrige el problema en el cual la opción de reproducción automática en el móvil [!DNL Safari] no funciona cuando el vídeo está vinculado directamente a un archivo de vídeo remoto. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30. El ID del parche es ACSD-49877. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete [!magento/quality-patch] a la versión más reciente y compruebe la compatibilidad en [[!DNL Quality Patches Tool]: Buscar parches]. Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La reproducción automática de vídeo no funciona en el móvil [!DNL Safari] cuando el vídeo está vinculado directamente a un archivo de vídeo remoto y no a un servicio de streaming.

<u>Requisitos previos</u>:
Se han instalado [!DNL Page Builder] módulos.

<u>Pasos a seguir</u>:

1. Cree una nueva página de CMS y edite **[!UICONTROL Content Value]** con [!DNL Page Builder].
1. Agregue un elemento *Tab* al contenido y agregue un *elemento de vídeo* dentro de *Tab*.
1. Ahora haga clic en el botón de engranaje para editar *el elemento de vídeo*.
1. Agregue un vínculo a un archivo de vídeo mp4 al campo [!UICONTROL Video URL].
1. Marcar el campo **[!UICONTROL Autoplay]** como *Sí*.
1. Haga clic en **[!UICONTROL Save]**.
1. Abra la página creada recientemente en [!DNL Safari] con un iPhone.

<u>Resultados esperados</u>

La opción de reproducción automática funciona en [!DNL Safari] mediante un iPhone.

<u>Resultados reales</u>

La opción de reproducción automática no funciona en [!DNL Safari] con un iPhone.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
