---
title: "ACSD-48661: problema de validación del separador de comas del límite de crédito de la empresa"
description: Aplique el parche ACSD-48661 para corregir el problema de Adobe Commerce en el que, cuando el límite de crédito de la empresa es mayor que 999, el separador de comas impide que se guarde la empresa debido a un error de validación.
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-48661: problema de validación del separador de comas del límite de crédito de la empresa

El parche ACSD-48661 corrige el problema en el que cuando el límite de crédito de la empresa es mayor que 999, el separador de comas impide el guardado de la empresa debido a un error de validación. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26. El ID del parche es ACSD-48661. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando el límite de crédito de la empresa es mayor que 999, el separador de comas impide que la empresa guarde debido a un error de validación.

<u>Pasos a seguir</u>:

1. Habilite la característica Compañía en **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Cree una empresa y agregue un límite de crédito superior a 999 en la ficha **[!UICONTROL Company Credit]**.
1. Guarde la compañía.
1. Edite la empresa e intente guardarla de nuevo.

<u>Resultados esperados</u>:

Puede salvar a la empresa sin fijar el límite de crédito. La coma no es compatible con los campos de entrada para las cantidades y los precios.

<u>Resultados reales</u>:

No puede guardar la compañía debido a un error de validación en el campo *[!UICONTROL Credit Limit]*. Adobe Commerce agrega automáticamente separadores de coma para los límites de crédito aunque el campo [!UICONTROL Credit Limit] no acepte comas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
