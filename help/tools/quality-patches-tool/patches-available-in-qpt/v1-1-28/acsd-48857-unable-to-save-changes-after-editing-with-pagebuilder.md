---
title: 'ACSD-48857: no se pueden guardar los cambios después de editar con  [!DNL Page Builder]'
description: Aplique el parche ACSD-48857 para corregir el problema de Adobe Commerce en el que el usuario no puede guardar los cambios después de editar con  [!DNL Page Builder].
feature: Admin Workspace, CMS, Page Builder
role: Admin
exl-id: b03cd597-8fef-4528-9699-793dc61d34da
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-48857: no se pueden guardar los cambios después de editarlos con [!DNL Page Builder]

La revisión ACSD-48857 corrige el problema en el cual el usuario no puede guardar los cambios después de editarlos con [!DNL Page Builder]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28. El ID del parche es ACSD-48857. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario no puede guardar los cambios después de editar con [!DNL Page Builder].

<u>Pasos a seguir</u>

1. Inicie sesión en el sitio web del administrador.
1. Vaya a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** para crear una página de CMS vacía.
1. Ejecute este script SQL para establecer el siguiente valor de campo **[!UICONTROL Content]**:

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. Volver a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** en Administración.
1. Edite la página.
1. Vaya a la ficha **[!UICONTROL Content]**.
1. Haga clic en **[!UICONTROL Save]**.

<u>Resultados esperados</u>

Se ha implementado el saneamiento de contenido de HTML. Esto elimina [!DNL Page Builder] atributos HTML reservados en el contenido generado por el editor de texto.

<u>Resultados reales</u>

La página permanece sin guardar y el cargador sigue girando. En la consola, se genera el siguiente error:

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
