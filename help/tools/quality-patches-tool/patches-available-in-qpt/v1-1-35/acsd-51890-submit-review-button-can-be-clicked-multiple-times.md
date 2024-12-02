---
title: 'ACSD-51890: se puede hacer clic en el botón [!UICONTROL Submit review] varias veces'
description: Aplique el parche ACSD-51890 para corregir el problema de Adobe Commerce en el que se puede hacer clic en el botón [!UICONTROL Submit Review] varias veces sin  [!DNL Google reCAPTCHA v3] validación.
feature: Products
role: Admin
exl-id: db69ccdc-c66e-4bdb-9783-772f2af0d33f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51890: se puede hacer clic en el botón **[!UICONTROL Submit Review]** varias veces sin validación de **[!DNL Google reCAPTCHA v3]**

>[!NOTE]
>
>Este parche se reemplazó por [ACSD-55112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

La revisión ACSD-51890 corrige el problema en el cual se puede hacer clic en el botón **[!UICONTROL Submit Review]** varias veces sin validación de **[!DNL Google reCAPTCHA v3]**. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.35. El ID del parche es ACSD-51890. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se puede hacer clic en el botón **[!UICONTROL Submit Review]** varias veces sin la validación **[!DNL Google reCAPTCHA v3]**.

<u>Pasos a seguir</u>:

1. Habilitar **[!DNL Google reCAPTCHA v3]** para la revisión del producto.
1. Abra la página del producto, vaya a la sección **[!UICONTROL Review]** y asegúrese de que [!DNL reCAPTCHA] esté visible.
1. Complete el formulario de revisión y haga clic en el botón **[!UICONTROL Submit Review]** varias veces lo más rápido posible.
1. Abra la sección **[!UICONTROL Review]** desde el Administrador.

<u>Resultados esperados</u>

No se crean revisiones duplicadas.

<u>Resultados reales</u>

Se crean revisiones duplicadas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](</help/tools/quality-patches-tool/usage.md>) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en la guía [!DNL Quality Patches Tool].
