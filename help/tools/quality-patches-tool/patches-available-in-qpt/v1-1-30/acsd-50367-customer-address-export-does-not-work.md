---
title: 'ACSD-50367: la exportación de direcciones de clientes no funciona con atributos de selección múltiple'
description: Aplique el parche ACSD-50367 para solucionar el problema de Adobe Commerce en el que la exportación de direcciones de clientes no funciona cuando se crea un atributo **&grave;Customer Address&grave;** de selección múltiple sin valores.
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
exl-id: 3f33a590-e7c2-424e-aacd-2df7ab893c3e
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-50367: La exportación de direcciones de clientes no funciona

El parche ACSD-50367 corrige el problema en el que la exportación de direcciones de clientes no funciona cuando se crea un atributo **`Customer Address`** de selección múltiple sin valores. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30. El ID del parche es ACSD-50367. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La exportación de direcciones de clientes no funciona cuando se crea un atributo **`Customer Address`** de selección múltiple sin valores.

<u>Requisitos previos</u>:

Cree un cliente con una dirección.

<u>Pasos a seguir</u>:

1. Crear un atributo **`Customer Address`** de selección múltiple en **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]** y seleccione **`Customer Address`** tipo de entidad.
1. Exportar las direcciones de los clientes. Verá que no se exporta nada.
1. Elimine el atributo **`Customer Address`** de selección múltiple y vuelva a exportar las direcciones de los clientes. Esta vez se genera el archivo CSV de las direcciones.

<u>Resultados esperados</u>:

Las direcciones de clientes se pueden exportar como un archivo CSV cuando se crea un atributo **`Customer Address`** de selección múltiple.

<u>Resultados reales</u>:

Las direcciones de clientes no se pueden exportar como archivo CSV cuando se crea un atributo **`Customer Address`** de selección múltiple.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
