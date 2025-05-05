---
title: 'ACSD-64209: el programador Cron recupera las ofertas negociables sin excluir las [!UICONTROL Ordered]'
description: Aplique el parche ACSD-64209 para corregir el problema de Adobe Commerce en el que el programador cron recupera todas las ofertas negociables sin excluir las que tienen el estado [!UICONTROL Ordered], lo que provoca que se active un correo electrónico o correos electrónicos.
feature:  B2B, Communications
role: Admin, Developer
source-git-commit: 6fbe987dca81065071b611bfe0bfd0cb7baf1938
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-64209: el programador Cron recupera las ofertas negociables sin excluir las [!UICONTROL Ordered]

El parche ACSD-64209 corrige el problema en el que el programador cron recupera todas las ofertas negociables sin excluir las que tienen el estado **[!UICONTROL Ordered]**, lo que provoca que se active un correo electrónico o correos electrónicos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. El ID del parche es ACSD-64209. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El programador cron recupera todas las ofertas negociables sin excluir las que tienen el estado **[!UICONTROL Ordered]**, lo que provoca que se active un correo electrónico o correos electrónicos.

<u>Pasos a seguir</u>:


1. En la barra lateral *Admin*, vaya a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** y habilite la oferta de la compañía y B2B.
1. Establezca **[!UICONTROL Default Expiration Period]** en *1* en *Administración* > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]**.
1. Cree una empresa, actívela e inicie sesión como administrador de la empresa.
1. Añadir un producto al carro de compras.
1. Solicite un presupuesto.
1. En la barra lateral *Admin*, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Seleccione la oferta creada y haga clic en **[!UICONTROL Send]** para devolver la oferta al comprador.
1. Inicie sesión como administrador de la empresa en la tienda.
1. Seleccione la oferta y haga clic en **[!UICONTROL Proceed to checkout]** para completar la compra.
1. Compruebe que el estado de la oferta sea **[!UICONTROL Ordered]** y que no haya más acciones posibles en la tienda.
1. Déclencheur el trabajo cron de `negotiable_quote_send_emails`.


<u>Resultados esperados</u>:

Dado que la cotización se ha pedido y no se pueden realizar más acciones, no se debe enviar ningún correo electrónico sobre la caducidad de la cotización.

<u>Resultados reales</u>:

Se envía un correo electrónico *La cotización caduca pronto*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
