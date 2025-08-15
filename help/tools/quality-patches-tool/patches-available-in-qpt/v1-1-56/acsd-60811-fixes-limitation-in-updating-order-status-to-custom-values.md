---
title: 'ACSD-60811: corrige la limitación al actualizar el estado del pedido a valores personalizados'
description: Aplique el parche ACSD-60811 para solucionar el problema de Adobe Commerce donde la actualización del estado del pedido con un valor o comentario personalizado solo es posible si el estado actual es "Procesando" o "Fraude".
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 6d5391b3-7014-4d0a-b4ab-799f0733bbca
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
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
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
