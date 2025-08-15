---
title: 'ACSD-49835: la casilla de verificación [!UICONTROL Use Default Value] no se ha guardado'
description: Aplique el parche ACSD-49835 para corregir el problema de Adobe Commerce en el que la casilla de verificación [!UICONTROL Use Default Value] no se guarda correctamente en un nivel de almacén para un atributo de selección múltiple.
feature: Storefront
role: Admin
exl-id: e8d5a95f-b17d-49fc-a6d3-e03554667438
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# ACSD-49835: la casilla de verificación [!UICONTROL Use Default Value] no se ha guardado

El parche ACSD-49835 corrige el problema en el que la casilla de verificación [!UICONTROL Use Default Value] no se guarda correctamente en un nivel de almacén para un atributo de selección múltiple. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-49835. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La casilla de verificación [!UICONTROL Use Default Value] no se ha guardado correctamente en un nivel de almacén para un atributo de selección múltiple.

<u>Pasos a seguir</u>:

1. Cree un(a) **[!UICONTROL Multiple-select Attribute]** en **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** y agréguelo a un conjunto de atributos.
1. Vaya a **[!UICONTROL Product]** y guarde **[!UICONTROL Values]** en **[!UICONTROL All Store Views (Default Scope)]**.
1. Vaya a un(a) **[!UICONTROL Store View Scope]** específico(a) y guarde el producto.
1. Vaya a **[!UICONTROL Store View Scope]** y marque la casilla **[!UICONTROL Use Default Value]**.

<u>Resultados esperados</u>:

Los valores de atributos de selección múltiple se guardan correctamente al marcar la casilla de verificación [!UICONTROL Use Default Value] en [!UICONTROL Store View Scope].

<u>Resultados reales</u>:

Los valores de atributos de selección múltiple no se guardaron correctamente al marcar la casilla de verificación [!UICONTROL Use Default Value] en [!UICONTROL Store View Scope].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
