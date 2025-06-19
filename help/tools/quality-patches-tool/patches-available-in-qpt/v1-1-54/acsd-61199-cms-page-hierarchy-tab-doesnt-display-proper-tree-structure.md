---
title: 'ACSD-61199: La pestaña de la página de CMS [!UICONTROL Hierarchy] no muestra la estructura de árbol adecuada'
description: Aplique el parche ACSD-61199 para corregir el problema de Adobe Commerce en el que la pestaña *[!UICONTROL Hierarchy]* de la página de CMS no muestra una estructura de árbol adecuada al editar una página de CMS con un *[!UICONTROL Hierarchy]* existente.
feature: Page Content
role: Admin, Developer
exl-id: f541d001-9680-431a-9a62-816c2d10b6d5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-61199: La pestaña [!UICONTROL Hierarchy] de la página de CMS no muestra la estructura de árbol adecuada

La revisión ACSD-61199 corrige el problema en el cual la pestaña *[!UICONTROL Hierarchy]* de la página de CMS no muestra una estructura de árbol adecuada al editar una página de CMS con un *[!UICONTROL Hierarchy]* existente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. El ID del parche es ACSD-61199. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La ficha *[!UICONTROL Hierarchy]* de la página de CMS no muestra una estructura de árbol adecuada al editar una página de CMS con un elemento *[!UICONTROL Hierarchy]* existente.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Crear nuevo(a) **[!UICONTROL CMS page]**. Se agrega a la raíz del sitio web en *[!UICONTROL Hierarchy]*.
1. Guarde la página.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Hierarchy]**.
1. Agregue cualquier otra página existente a *[!UICONTROL Hierarchy]*.
1. Guarde *[!UICONTROL Hierarchy]*.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Edite cualquiera de las páginas existentes y abra *[!UICONTROL Hierarchy]*.

<u>Resultados esperados</u>:

*[!UICONTROL Hierarchy]* se carga según lo esperado.

<u>Resultados reales</u>:

*[!UICONTROL Hierarchy]* no se ha cargado en la ficha.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

[[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
