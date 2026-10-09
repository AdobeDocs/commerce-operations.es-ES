---
title: 'ACSD-66233: Los administradores no pueden agregar productos debido a que la lista de productos emergente no responde'
description: Aplique el parche ACSD-66233 para solucionar el problema de Adobe Commerce en el que los administradores no pueden agregar productos a las categorías porque la ventana emergente [!UICONTROL Add Product] de Visual Merchandiser se carga indefinidamente.
feature: Inventory, Merchandising
role: Admin, Developer
type: Troubleshooting
exl-id: 2e01e62d-b6f9-4aa5-9040-7908aa83d422
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%
---
# ACSD-66233: Los administradores no pueden añadir productos debido a que la lista de productos emergente no responde

La revisión ACSD-66233 corrige un problema en el cual los administradores no pueden agregar productos a las categorías debido a que la ventana emergente [!UICONTROL Add Product] en Visual Merchandiser se carga indefinidamente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. El ID del parche es ACSD-66233. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Problema en el cual la ventana emergente [!UICONTROL Add Product] en Visual Merchandiser se carga indefinidamente, lo que impide que los administradores agreguen productos a las categorías.

<u>Pasos a seguir</u>:

1. Instale y habilite los módulos de inventario.
1. Cree un gran número de orígenes de inventario (por ejemplo, 700).
1. Cree varios inventarios de stock (por ejemplo, 12) y asígneles los orígenes de inventario.
1. Cree algunos productos y asígnelos a los orígenes de inventario.
1. Cree una categoría.
1. Expanda la sección [!UICONTROL Products in Category].
1. Haga clic en el botón [!UICONTROL Add Product].
1. Observe la ventana emergente con la lista de productos.

<u>Resultados esperados</u>:

La lista de productos se carga en la ventana emergente en un tiempo razonable.

<u>Resultados reales</u>:

La ventana emergente se carga indefinidamente y no muestra la lista de productos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
