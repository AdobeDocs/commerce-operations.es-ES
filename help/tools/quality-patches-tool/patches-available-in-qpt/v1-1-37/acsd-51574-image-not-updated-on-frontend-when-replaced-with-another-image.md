---
title: "ACSD-51574: la imagen no se actualiza en el front-end cuando se sustituye por otra imagen"
description: Aplique el parche ACSD-51574 para corregir el problema de Adobe Commerce en el que la imagen no se actualiza en el front-end después de reemplazarla por otra imagen.
feature: Configuration
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-51574: la imagen no se actualiza en el front-end cuando se sustituye por otra imagen

El parche ACSD-51574 corrige el problema en el que la imagen no se actualiza en el front-end después de reemplazarla por otra imagen. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.37. El ID del parche es ACSD-51574. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La imagen no se actualiza en el front-end después de reemplazarla por otra imagen.

<u>Pasos a seguir</u>:

1. Cree un producto con algunas imágenes.
1. Edite el producto y cargue una imagen con un nombre conocido (Ejemplo: *image.jpg*).
1. Guarde el producto.
1. Vuelva a editar el producto, elimine la versión antigua de la imagen y cargue la nueva versión de la imagen con el mismo nombre. **Asegúrese de que la nueva versión sea visiblemente diferente para ver el problema.**
1. Guarde el producto. Tanto el administrador como el front-end muestran las imágenes.
1. Vuelva a editar el producto y vuelva a cargar la misma imagen nueva (con el mismo nombre).
1. Guarde el producto y compruebe la página del producto en el front-end.

<u>Resultados esperados</u>:

La imagen cargada por segunda vez debe ser la nueva imagen, junto con el nombre cambiado de imagen.

<u>Resultados reales</u>:

La imagen cargada por segunda vez es la versión anterior de la imagen que se eliminó anteriormente, en lugar de la misma imagen nueva.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
