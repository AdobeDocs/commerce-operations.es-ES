---
title: 'ACP2E-3767: La última opción de paquete vuelve a aparecer después de guardar un producto de paquete'
description: Aplique el parche ACP2E-3767 para corregir el problema de Adobe Commerce en el que no se pudo eliminar la última opción de paquete en un producto agrupado.
feature: Products, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f39442925d9cc82087af9e84d91137a0fcd0ec14
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# ACP2E-3767: La última opción de paquete vuelve a aparecer después de guardar un producto de paquete

El parche ACP2E-3767 corrige el problema en el que la última opción de paquete vuelve a aparecer después de guardar el producto del paquete. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACP2E-3767. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se puede eliminar la última opción de paquete de un producto agrupado.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**.
1. Seleccione **[!UICONTROL Simple Product]** de la lista desplegable.
1. Introduzca los datos necesarios y guarde los cambios.
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**.
1. Seleccione **[!UICONTROL Bundle Product]** de la lista desplegable.
1. Introduzca los datos necesarios.
1. En Elementos de paquete, haga clic en **[!UICONTROL Add Option]**.
1. Agregue un título a la nueva opción y luego haga clic en **[!UICONTROL Add Products to Option]**.
1. Seleccione el producto simple creado anteriormente y después **[!UICONTROL Add Selected Products]**.
1. Guardar producto del paquete.
1. Elimine la opción del paquete y guarde los cambios.

<u>Resultados esperados</u>:

1. La opción de paquete se ha eliminado correctamente.
1. Se muestra un mensaje si no se permite la eliminación.

<u>Resultados reales</u>:

1. La opción del paquete permanece activa.
1. No se muestra ningún error o notificación.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
