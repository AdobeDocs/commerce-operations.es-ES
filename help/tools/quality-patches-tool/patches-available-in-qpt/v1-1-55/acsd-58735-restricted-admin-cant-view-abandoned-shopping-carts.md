---
title: 'ACSD-58735: el administrador restringido no puede ver los carros de compras abandonados en la cuenta de cliente del sitio web asociado'
description: Aplique el parche ACSD-58735 para solucionar el problema de Adobe Commerce en el que un administrador restringido no puede ver los carros de compras abandonados en la página de cuenta del cliente en el Administrador de Commerce de un sitio web asociado.
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
exl-id: b5dcc12f-325d-4de5-bae5-ff938ec77b13
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-58735: el administrador restringido no puede ver los carros de compras abandonados en la cuenta de cliente del sitio web asociado

El parche ACSD-58735 corrige el problema en el que un usuario administrador con una función restringida no puede ver los carros de compras de los clientes abandonados desde la pestaña Commerce **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** > **[!UICONTROL Select Cart]** > **[!UICONTROL Shopping Cart]**.

El problema se produce porque, al mostrar la vista de cuadrícula para varios sitios web, si un carro de compras abandonado se carga de forma predeterminada en el panel Administración, no se obtiene el ID de tienda asociado para mostrar.

Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. El ID del parche es ACSD-58735. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los administradores restringidos no pueden ver los carros de compras abandonados en la página de cuenta del cliente del panel de administración.

<u>Pasos a seguir</u>:

1. Cree una función de administrador con acceso solo a uno de los sitios web.
1. Crear un carro de compras abandonado.
1. Inicie sesión como usuario administrador con privilegios completos. Compruebe **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** y vea que se muestra el carro de compras.
1. Seleccione **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** como usuario administrador restringido.

<u>Resultados esperados</u>:

El administrador restringido puede ver los carros de compras abandonados del sitio web asociado.

<u>Resultados reales</u>:

El administrador restringido no ve carros de compras abandonados para el sitio web asociado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
