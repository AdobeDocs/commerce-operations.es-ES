---
title: "ACSD-47106: el nuevo atributo personalizado de la página de creación de la empresa no se ha guardado"
description: Aplique el parche ACSD-47106 para corregir el problema de Adobe Commerce en el que un valor no se puede guardar en un nuevo atributo personalizado en una página de creación de empresa.
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47106: no se ha guardado el nuevo atributo personalizado de la página de creación de la empresa

El parche ACSD-47106 corrige el problema en el que un valor no se puede guardar en un nuevo atributo personalizado en una página de creación de empresa. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.22. El ID del parche es ACSD-47106. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se puede guardar un valor en un nuevo atributo personalizado de una página de creación de empresa.

<u>Requisitos previos</u>:

* Los módulos B2B están instalados.

<u>Pasos a seguir</u>:

1. Vaya a Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Customer]** > **[!UICONTROL Add New Attribute]**.
1. Crear nuevo atributo: _Prueba 01_.
1. Vaya a Administración de Commerce > **[!UICONTROL Customers]** > **[!UICONTROL Companies]** > y cree una nueva compañía con todos los detalles necesarios.
1. Intente agregar un valor al atributo personalizado _Prueba 01_.
1. Intente actualizar el valor del atributo personalizado _Prueba 01_.

<u>Resultados esperados</u>:

Los cambios se guardan.

<u>Resultados reales</u>:

Los cambios no se guardan.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].