---
title: 'ACSD-63793: los procesos de importación interfieren entre sí en diferentes pestañas del explorador'
description: Aplique el parche ACSD-63793 para corregir el problema de Adobe Commerce donde los procesos de importación interfieren entre sí en diferentes pestañas del explorador.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 60ad8dff5a3f26d0eab536d8824cb6579cb88a5a
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# ACSD-63793: los procesos de importación interfieren entre sí en diferentes pestañas del explorador

El parche ACSD-63793 corrige el problema en el que los procesos de importación interfieren entre sí en diferentes pestañas del explorador. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. El ID del parche es ACSD-63793. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La importación de datos a través de la IU de administración interfiere con otra importación, lo que provoca que los datos de una importación se procesen en otra.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**.
1. Establecer **[!UICONTROL Entity Type]** en *[!UICONTROL Customers and Addresses] (un solo archivo)*.
1. Establezca **[!UICONTROL Import Behavior]** en *[!UICONTROL Add/Update]*.
1. Seleccione un archivo válido para importar.
1. Haga clic en el botón **[!UICONTROL Check Data]**.
1. Mantenga esta pestaña abierta.
1. Abra una pestaña nueva y repita los pasos con un archivo que contenga datos no válidos (por ejemplo, dos correos electrónicos idénticos para diferentes clientes).
1. Vuelva a la primera pestaña.
1. Haga clic en el botón **[!UICONTROL Import]** en la parte inferior.

<u>Resultados esperados</u>:

El proceso de importación no debe interferir entre sí.

<u>Resultados reales</u>:

El proceso de importación finaliza y el archivo de informe está disponible para descargar. Indica un error en la segunda fila y se procesan los datos de otra importación, aunque la validación inicial haya pasado sin errores.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
