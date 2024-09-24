---
title: "MDVA-42584: El estado de stock del producto configurable no se actualiza automáticamente"
description: El parche MDVA-42584 resuelve el problema en el que el estado de stock del producto configurable no se actualiza automáticamente cuando se actualiza su producto simple. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10. El ID del parche es MDVA-42584. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-42584: El estado de stock del producto configurable no se actualiza automáticamente

El parche MDVA-42584 resuelve el problema en el que el estado de stock del producto configurable no se actualiza automáticamente cuando se actualiza su producto simple. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10. El ID del parche es MDVA-42584. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado de stock del producto configurable en el backend no se actualiza automáticamente cuando su producto simple se establece en **En stock** mediante API o importación.

<u>Requisitos previos</u>:

MSI instalado.

<u>Pasos a seguir</u>:

1. Cree un producto configurable, **InvCheck001**, con dos opciones: **InvCheck001-M** e **InvCheck001-L**.
1. Ambos productos simples deben tener Cantidad y deben estar **En stock** para que el producto configurable también esté **En stock** en el servidor.
1. Actualice los productos simples y establezca la cantidad en **0** y el estado de las existencias en **Agotado**.
1. Actualice el producto configurable y verifique que el estado de las existencias se actualice a **Agotado**.
1. Use el siguiente extremo de API y establezca el producto simple **InvCheck001-M** en **En existencia** con Cantidad > 0.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. Vaya al servidor y verifique la cantidad y el estado de stock del producto simple **InvCheck001-M**. Se ha actualizado a **En stock**.
1. Actualice el producto configurable y compruebe el estado de las existencias.

<u>Resultados esperados</u>:

El estado de existencias del producto configurable **InvCheck001** en el servidor se actualiza automáticamente a **En existencias**.

<u>Resultados reales</u>:

El estado de existencias del producto configurable sigue siendo **Agotado**.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
