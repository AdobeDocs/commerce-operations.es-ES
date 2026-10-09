---
title: 'ACSD-60811: corrige la limitación al actualizar el estado del pedido a valores personalizados'
description: Aplique el parche ACSD-60811 para solucionar el problema de Adobe Commerce donde la actualización del estado del pedido con un valor o comentario personalizado solo es posible si el estado actual es "Procesando" o "Fraude".
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 6d5391b3-7014-4d0a-b4ab-799f0733bbca
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '394'
ht-degree: 0%
---
# ACSD-60811: corrige la limitación al actualizar el estado del pedido a valores personalizados

La revisión ACSD-60811 corrige el problema en el que la actualización del estado del pedido con un valor o comentario personalizado solo es posible si el estado actual es &#39;[!UICONTROL Processing]&#39; o &#39;[!UICONTROL Suspected Fraud]&#39;. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. El ID del parche es ACSD-60811. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7. 2.4.7-p1, 2.4.7-p2, 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Actualizar el estado del pedido con un valor o comentario personalizado solo es posible si el estado actual es *procesando* o *fraude*. El estado del pedido permanece sin cambios cuando se selecciona y se envía un nuevo estado.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Order Status]** para crear un estado de pedido personalizado en el panel de administración.
1. Haga clic en **[!UICONTROL Assign Status to State]** para asignar el estado personalizado al estado del pedido.
1. Cambie el estado del pedido desde la página de vista de pedidos del panel de administración.

<u>Resultados esperados</u>:

El usuario administrador debe poder cambiar el estado del pedido a un estado de pedido personalizado en el panel de administración.

<u>Resultados reales</u>:

El estado del pedido sigue siendo el mismo cuando se selecciona y se envía un nuevo estado de pedido.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
