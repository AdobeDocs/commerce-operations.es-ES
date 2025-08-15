---
title: 'ACSD-63326: corrija el problema de redirección de administradores después de realizar un pedido desde el backend'
description: Aplique el parche ACSD-63326 para corregir el problema de Adobe Commerce en el que el administrador es redirigido a una página rota después de realizar un pedido desde el backend de.
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 8fffc3ad-11a4-4e62-b747-1c4c7b493ada
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63326: corrija el problema de redirección de administradores después de realizar un pedido desde el backend

El parche ACSD-63326 corrige el problema en el que el administrador es redirigido a una página rota después de realizar un pedido desde el servidor. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. El ID del parche es ACSD-63326. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los administradores son redirigidos a una página con un diseño roto después de realizar correctamente un pedido de un cliente desde el backend.

<u>Pasos a seguir</u>:

1. Vaya a la sección **[!UICONTROL Customers]** en el panel de administración.
1. Seleccione cualquier cliente y haga clic en **[!UICONTROL Edit]**.
1. En la página de detalles del cliente, haga clic en **[!UICONTROL Create Order]** en el menú superior.
1. Seleccione la tienda [!UICONTROL FR French] y agregue cualquier producto disponible al pedido.
1. Complete los detalles necesarios al finalizar la compra y haga clic en **[!UICONTROL Get shipping methods and rates]**.
1. Haga clic en **[Enviar pedido]** para realizar el pedido.

<u>Resultados esperados</u>:

Se redirige al administrador a la página de confirmación de pedido o de agradecimiento con el diseño correcto.

<u>Resultados reales</u>:

Se redirige al administrador a una página con un diseño roto. El diseño solo se corrige después de actualizar la página.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
