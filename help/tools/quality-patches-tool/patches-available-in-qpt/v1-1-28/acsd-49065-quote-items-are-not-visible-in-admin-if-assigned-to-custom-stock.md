---
title: 'ACSD-49065: Los elementos de cotización no son visibles en el administrador'
description: Aplique el parche ACSD-49065 para corregir el problema de Adobe Commerce en el que los elementos de oferta no son visibles en el administrador si solo están asignados al stock personalizado.
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
exl-id: fc3bea92-305b-4598-9915-3422d61c76ec
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-49065: Los elementos de cotización no son visibles en el administrador

El parche ACSD-49065 corrige el problema en el que los elementos de cotización no son visibles en el administrador si solo están asignados al stock personalizado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28. El ID del parche es ACSD-49065. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los elementos de oferta no son visibles en el administrador si solo se asignan al stock personalizado.

Requisitos previos:

Se deben instalar los módulos **[!UICONTROL B2B]** y **[!UICONTROL Inventory]**.

<u>Pasos a seguir</u>:

1. Habilite **[!UICONTROL Company]** y **[!UICONTROL B2B Quote]** en **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Crear un(a) **[!UICONTROL Inventory Source]** secundario(a) y asignarlo a un(a) **[!UICONTROL Inventory Stock]** secundario.
1. Cree un nuevo producto asignando solamente el secundario (no predeterminado) **[!UICONTROL Inventory Source]**.
1. Vaya a la tienda y cree una nueva cuenta de empresa. Inicie sesión como **[!UICONTROL Company Admin]** y agregue el producto creado al carro de compras.
1. Vaya al carro y *[!UICONTROL Request a Quote]*.
1. Vaya al administrador y vea la cotización solicitada en **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.

<u>Resultados esperados</u>:

Los artículos son visibles en la nueva oferta creada con los nuevos productos sin volver a guardarlos.

<u>Resultados reales</u>:

La sección *[!UICONTROL Items Quoted]* está vacía. Si vuelve a guardar el producto recién creado, los elementos aparecerán.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
