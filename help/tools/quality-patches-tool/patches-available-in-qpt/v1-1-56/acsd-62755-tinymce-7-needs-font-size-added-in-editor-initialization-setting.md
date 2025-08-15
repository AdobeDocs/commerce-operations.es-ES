---
title: 'ACSD-62755: [!DNL TinyMCE] 7 necesita que se agreguen el tamaño y la fuente a la configuración de inicialización del editor'
description: Aplique el parche ACSD-62755 para corregir el problema de Adobe Commerce donde  [!DNL TinyMCE] 7 requiere que *tamaño de fuente* y *familia de fuentes* se agreguen específicamente dentro de la configuración de inicialización del editor.
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
exl-id: f61dc7b6-ac6b-45eb-a0a2-f3f0bff4422b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# ACSD-62755: [!DNL TinyMCE] 7 necesita que se agreguen el tamaño y la fuente a la configuración de inicialización del editor

El parche ACSD-62755 corrige el problema en el que [!DNL TinyMCE] 7 requiere que se agreguen específicamente selectores de *tamaño de fuente* y *familia de fuentes* dentro de la configuración de inicialización del editor. Este parche está disponible con [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 instalado. El ID del parche es ACSD-62755. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.5-p10

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!DNL TinyMCE] 7 requiere que los selectores *tamaño de fuente* y *familia de fuentes* se agreguen específicamente en la configuración de inicialización del editor.

<u>Pasos a seguir</u>:

Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Content]** y seleccione *[!UICONTROL Show Editor]*.

<u>Resultados esperados</u>:

Los selectores *Tamaño de fuente* y *familia de fuentes* están visibles en el editor de WYSIWYG.

<u>Resultados reales</u>:

Falta el selector *Tamaño de fuente* en el editor de WYSIWYG.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
