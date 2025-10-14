---
title: 'ACSD-51471: el usuario administrador no puede guardar la actualización programada para el producto agrupado'
description: Aplique el parche ACSD-51471 para corregir el problema de Adobe Commerce en el que un usuario administrador no puede guardar una actualización programada para un producto agrupado que utiliza un producto simple con una actualización programada.
exl-id: d8134111-63f0-4476-a407-677bda52fa90
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-51471: el usuario administrador no puede guardar la actualización programada para el producto agrupado

El parche ACSD-51471 corrige el problema en el que un usuario administrador no puede guardar una actualización programada para un producto agrupado que utiliza un producto simple con una actualización programada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33. El ID del parche es ACSD-51471. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios administradores no pueden guardar una actualización programada para un producto agrupado que utiliza un producto simple que tiene una actualización programada.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Agregue una actualización programada para el producto simple con solo la *Fecha de inicio* y sin *Fecha de finalización*.
1. Una vez aplicada la actualización, cambie el SKU del producto.
1. Cree un producto agrupado y añada el producto simple creado en el paso 1 como producto secundario.
1. Cree una actualización programada para el producto agrupado para habilitar el producto agrupado. Proporcione *Fecha de inicio* y *Fecha de finalización* para la actualización programada.
1. Guarde la actualización programada.

<u>Resultados esperados</u>:

La actualización programada se ha guardado correctamente.

<u>Resultados reales</u>:

El siguiente error se produce al guardar la actualización programada: *El producto solicitado no existe. Compruebe el producto y vuelva a intentarlo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
