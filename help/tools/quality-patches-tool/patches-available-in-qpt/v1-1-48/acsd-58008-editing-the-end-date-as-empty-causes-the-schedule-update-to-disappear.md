---
title: 'ACSD-58008: si edita la fecha de finalización como *empty*, la actualización de la programación desaparece'
description: Aplique el parche ACSD-58008 para corregir el problema de Adobe Commerce en el que editar la fecha de finalización como *empty* hace que desaparezca la actualización de la programación.
feature: Staging, Page Content
role: Admin, Developer
exl-id: 6d2279e5-6580-4325-b0a8-ed62a95da3c2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-58008: si edita la fecha de finalización como *empty*, la actualización de la programación desaparecerá

El parche ACSD-58008 corrige el problema en el que al editar la fecha de finalización como *empty*, la actualización de la programación desaparece. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48. El ID del parche es ACSD-58008. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Si edita la fecha de finalización como *empty*, la actualización de la programación desaparecerá

<u>Pasos a seguir</u>:

1. Iniciar sesión como [!UICONTROL Admin].
1. Vaya a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** y cree una página.
1. Seleccione la página creada y haga clic en **[!UICONTROL Schedule New Update]**. *(navegue por él en la esquina superior derecha de la página)*.
1. Cree cuatro actualizaciones. *(por ejemplo, como un incremento de* 2 *minutos)*.
1. Actualice la *actualización 2* y cambie la hora a una hora que esté por delante de la última *actualización 4*.
1. Guarde las actualizaciones realizadas.

<u>Resultados esperados</u>:

La actualización de programación muestra la *actualización 3*.

<u>Resultados reales</u>:

La actualización de programación no muestra la *actualización 3*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
