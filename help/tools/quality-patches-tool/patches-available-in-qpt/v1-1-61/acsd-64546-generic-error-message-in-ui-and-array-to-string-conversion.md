---
title: 'ACSD-64546: mensaje de error genérico en la excepción de conversión de IU y matriz a cadena durante la creación de etiquetas UPS'
description: Aplique el parche ACSD-64546 para corregir el problema de Adobe Commerce donde aparece un mensaje de error genérico en la interfaz de usuario y la excepción de conversión de matriz a cadena se registra durante la creación de etiquetas UPS. El parche garantiza que se muestre el error correcto en la interfaz de usuario y en los registros.
feature: Shipping/Delivery
role: Admin, Developer
source-git-commit: f50da09cec35b3a72208f17b6832e3068de9c874
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---


# ACSD-64546: mensaje de error genérico en la interfaz de usuario y excepción *Array to string conversion* durante la creación de etiquetas UPS

El parche ACSD-64546 corrige el problema en el que aparece un mensaje de error genérico en la interfaz de usuario y se registra la excepción *Array to string conversion* durante la creación de la etiqueta UPS, lo que garantiza que se muestre el error correcto en la interfaz de usuario y en los registros. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. El ID del parche es ACSD-64546. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Aparece un mensaje de error genérico en la interfaz de usuario y se produce la excepción *Array to string conversion* durante la creación de la etiqueta UPS.

<u>Pasos a seguir</u>:

1. Cree una cuenta de cliente con una dirección válida.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL GENERAL]** > **[!UICONTROL General]** > **[!UICONTROL Store Information]** y agregue una dirección válida.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Shipping settings]** > **[!UICONTROL Origin]** y agregue una dirección válida.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Delivery methods]** > **[!UICONTROL UPS]** y configure UPS.
1. Realizar un pedido con [!UICONTROL UPS].
1. Quite el identificador de usuario y la contraseña de UPS de `core_config_data` en la base de datos.
1. Limpie la caché de configuración.
1. Abra el pedido creado en **[!UICONTROL Admin]**.
1. Cree un nuevo envío.
   1. Seleccione la casilla de verificación **[!UICONTROL Create Shipping Label]**.
   1. Haga clic en **[!UICONTROL Submit shipment]**.
   1. Añada el producto a un paquete. Especifique el tamaño del paquete (longitud, anchura y altura).
   1. Haga clic en **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

El mensaje de error real se muestra en la interfaz de usuario y en los registros.

<u>Resultados reales</u>:

* El siguiente error aparece en la interfaz de usuario:
  *Error al crear la etiqueta de envío.*
* La excepción *Array to string conversion* evita que el mensaje de error real se muestre o se almacene en los registros.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:
* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura en la nube: Actualizaciones y parches > Aplicar parches en la guía de Commerce en la infraestructura en la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:
* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
