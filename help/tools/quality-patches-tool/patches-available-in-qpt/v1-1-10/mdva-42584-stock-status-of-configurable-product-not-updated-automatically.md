---
title: 'MDVA-42584: El estado de stock del producto configurable no se actualiza automáticamente'
description: El parche MDVA-42584 resuelve el problema en el que el estado de stock del producto configurable no se actualiza automáticamente cuando se actualiza su producto simple. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. El ID del parche es MDVA-42584. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Configuration, Orders, Products
role: Admin
exl-id: 6311f069-f08f-4d58-9f4b-fa1246c02640
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%
---
# MDVA-42584: El estado de stock del producto configurable no se actualiza automáticamente

El parche MDVA-42584 resuelve el problema en el que el estado de stock del producto configurable no se actualiza automáticamente cuando se actualiza su producto simple. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.10. El ID del parche es MDVA-42584. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
