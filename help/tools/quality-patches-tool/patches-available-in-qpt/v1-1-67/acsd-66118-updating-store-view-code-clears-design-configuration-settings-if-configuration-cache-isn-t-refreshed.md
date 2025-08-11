---
title: 'ACSD-66118: al actualizar [!UICONTROL Store View Code], se borra la configuración de [!UICONTROL Design Configuration] si [!UICONTROL Configuration Cache] no se actualiza'
description: Aplique el parche ACSD-66118 para solucionar el problema de Adobe Commerce donde al actualizar [!UICONTROL Store View Code] se borra [!UICONTROL Design Configuration] (tema y configuración personalizada) si [!UICONTROL Configuration Cache] no se actualiza correctamente.
feature: Cache, Configuration, Themes
role: Admin, Developer
type: Troubleshooting
source-git-commit: ef4d6e420f304b0229c54c8ec7bd5500039bcb6b
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# ACSD-66118: al actualizar **[!UICONTROL Store View Code]**, se borra la configuración de **[!UICONTROL Design Configuration]** si **[!UICONTROL Configuration Cache]** no se actualiza

La revisión ACSD-66118 corrige el problema en el cual al actualizar **[!UICONTROL Store View Code]** se borra la configuración de **[!UICONTROL Design Configuration]** si **[!UICONTROL Configuration Cache]** no se actualiza. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. El ID del parche es ACSD-66118. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La configuración de **[!UICONTROL Design Configuration]** (como el tema y la configuración personalizada) se borra al actualizar el campo **[!UICONTROL Store View Code]**, si **[!UICONTROL Configuration Cache]** no se actualiza.

<u>Pasos a seguir</u>:

1. Inicie sesión en el panel **[!UICONTROL Admin]**.
2. Vaya a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**.
3. Editar una vista de tienda que tenga un tema personalizado configurado en **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]**.
4. Cambie el campo **[!UICONTROL Code]** (por ejemplo, de `storeview_1` a `storeview_main`).
5. Haga clic en **[!UICONTROL Save Store View]** para guardar los cambios.
6. Actualice o vuelva a abrir la página **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]** para el **[!UICONTROL Store View]** actualizado y no se seleccionará ningún tema.

<u>Resultados esperados</u>:

Después de actualizar **[!UICONTROL Store View Code]**, **[!UICONTROL Design Configuration]** (incluido el tema y la configuración personalizada) debe permanecer intacto.

<u>Resultados reales</u>:

Se ha borrado **[!UICONTROL Design Configuration]**. La temática vuelve a los valores predeterminados y se pierde la configuración personalizada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
