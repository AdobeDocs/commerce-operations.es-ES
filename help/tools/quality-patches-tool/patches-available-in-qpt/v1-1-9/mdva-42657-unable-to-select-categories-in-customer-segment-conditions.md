---
title: 'MDVA-42657: No se pueden seleccionar categorías en las condiciones de segmentos del cliente'
description: El parche MDVA-42657 resuelve el problema en el que el usuario administrador no puede seleccionar categorías en las condiciones del segmento de cliente. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9. El ID del parche es MDVA-42657. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Categories, Console, Customer Service
role: Admin
exl-id: 115bad99-a603-4940-897e-034974ed1a6c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-42657: No se pueden seleccionar categorías en las condiciones de segmentos del cliente

El parche MDVA-42657 resuelve el problema en el que el usuario administrador no puede seleccionar categorías en las condiciones del segmento de cliente. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9. El ID del parche es MDVA-42657. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador no puede seleccionar categorías en las condiciones del segmento del cliente.

<u>Pasos a seguir</u>:

1. Vaya a **Clientes** > **Segmentos**.
1. Cree un nuevo segmento.
1. Vaya al segmento recién creado y haga clic en **Condiciones** en la navegación del lado izquierdo.
1. Haga clic en el signo más verde.
1. Seleccione Historial de productos en Productos.
1. Cambie &quot;visto&quot; por &quot;ordenado&quot;.
1. Cambie &quot;TODO&quot; por &quot;CUALQUIERA&quot;.
1. Haga clic en el signo más verde anidado y seleccione Categoría.
1. Haga clic en el signo **...** y, a continuación, haga clic en el icono del selector (a la izquierda de la marca de verificación).
1. Abra la consola de desarrollo del explorador.
1. Marque las casillas de verificación de una o varias categorías y observe el error de JavaScript producido en la consola.
1. Haga clic en el botón **Guardar**.
1. Vuelva a la condición y compruebe si se han guardado las categorías seleccionadas.

<u>Resultados esperados</u>:

Las categorías seleccionadas se guardan y seleccionan al ver o editar las condiciones del segmento.

<u>Resultados reales</u>:

Faltan las categorías seleccionadas y no se han guardado correctamente. Recibe el siguiente error en la consola:

```
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
