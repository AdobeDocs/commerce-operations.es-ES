---
title: 'ACSD-57045: las reescrituras de URL provocan bucles de página infinitos después de que [!UICONTROL Website Root] se desmarque de [!UICONTROL Hierarchy]'
description: Aplique el parche ACSD-57045 para corregir el problema de Adobe Commerce donde las reescrituras de URL causan bucles de página infinitos después de que [!UICONTROL Website Root] esté desmarcado de [!UICONTROL Hierarchy].
feature: CMS
role: Admin, Developer
exl-id: 7beaee40-a392-4644-917e-c507e79bddcc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# ACSD-57045: las reescrituras de URL provocan bucles de página infinitos después de que [!UICONTROL Website Root] se desmarque de [!UICONTROL Hierarchy]

El parche ACSD-57045 corrige el problema en el que las reescrituras de URL causan bucles de página infinitos después de que **[!UICONTROL Website Root]** esté desmarcado de **[!UICONTROL Hierarchy]**. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49. El ID del parche es ACSD-57045. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las reescrituras de URL provocan bucles de página infinitos después de que **[!UICONTROL Website Root]** se deseleccione de **[!UICONTROL Hierarchy]**.

<u>Pasos a seguir</u>:

1. Cree una página de CMS llamada *Test-Parent*.
1. Cree una página denominada *Test-Child* y, en la sección **[!UICONTROL Hierarchy]**, seleccione **[!UICONTROL Website Root]** > **[!UICONTROL Parent]** y guarde los cambios.
1. Ir a **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**.
1. Tenga en cuenta que hay dos nuevas reescrituras:
   * Ruta de solicitud a *Test-Parent* que apunta a *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*
   * Ruta de solicitud a *Test-Child* que señala a *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*
1. Visita la tienda y agrega *test-child* a la URL. Debería ver la página secundaria.
1. Haga lo mismo, pero agregue *test-parent/test-child/* a la dirección URL y vea la misma página.
1. Vaya a **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** y seleccione **[!UICONTROL Add URL Rewrite]**. Elija la siguiente configuración:
   * Tipo: *Personalizado*
   * Ruta de solicitud: *test-parent/test-child*
   * Ruta de destino: *test-child*
   * Tipo de redirección: *Permanente (301)*
1. Visite la ruta *test-parent/test-child* y se le debería redirigir a *test-child*.
1. Edite la página secundaria (**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** > Elegir elemento secundario y seleccione **[!UICONTROL Edit]**).
1. En la sección **[!UICONTROL Hierarchy]**, mantenga seleccionado *Test-Parent*, pero anule la selección de **[!UICONTROL Website Root]** y guarde los cambios.
1. Vaya a **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** y observe que falta el redireccionamiento original de *test-child* a *cms/page/view/page_id*, que en ese momento está sustituido por una ruta que señala a *test-child* a *test-parent/test-child*.
1. Visita la tienda e intenta visitar la página *Test-Child*.

<u>Resultados esperados</u>:

Se abre la página *Test-Child*.

<u>Resultados reales</u>:

La página *Test-Child* no está abierta. El explorador intenta abrir la página *test-parent/test-child* en un bucle infinito.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
