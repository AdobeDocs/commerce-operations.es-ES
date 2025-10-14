---
title: 'ACSD-66965: La opción [!UICONTROL Print] de la página [!UICONTROL Requisition List] produce un error'
description: Aplique el parche ACSD-66965 para corregir un problema en Adobe Commerce en el que la opción [!UICONTROL Print] de la página [!UICONTROL Requisition List] produce un error.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7682a326a6c703a08dd6d0fac5319ac38e1bc3c8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-66965: La opción **[!UICONTROL Print]** de la página **[!UICONTROL Requisition List]** produce un error

La revisión ACSD-66965 corrige el problema en el que la opción **[!UICONTROL Print]** de la página **[!UICONTROL Requisition List]** produce un error. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. El ID del parche es ACSD-66965. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La opción **[!UICONTROL Print]** de la página **[!UICONTROL Requisition List]** produce un error debido a una referencia de objeto nulo en `Grid.php`.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Establezca **[!UICONTROL Enable Company]**, **[!UICONTROL Enable Shared Catalog]** y **[!UICONTROL Enable Requisition List]** en `Yes`.
1. Cree dos productos simples.
1. Inicie sesión en la tienda y abra la página **[!UICONTROL My Account]**.
1. Crear una lista de solicitudes.
1. Asigne ambos productos a la lista de solicitudes.
1. Acceda a la lista de solicitudes y enumere los productos.
1. Haga clic en **[!UICONTROL Print]**.

<u>Resultados esperados</u>:

La opción **[!UICONTROL Print]** de la página **[!UICONTROL Requisition List]** muestra la vista preliminar sin errores.

<u>Resultados reales</u>:

Aparece el siguiente mensaje de error: *Se produjo un error durante la ejecución de la aplicación. Vea el registro de excepciones para obtener detalles.*

```
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
