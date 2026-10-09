---
title: 'ACSD-46865: [!UICONTROL shipment] y [!UICONTROL credit memo] no se rellenaron cuando [!UICONTROL asynchronous indexing] está habilitado'
description: Aplique el parche ACSD-46865 para solucionar el problema de Adobe Commerce en el que las cuadrículas [!UICONTROL shipment] y [!UICONTROL credit memo] no se rellenan cuando [!UICONTROL asynchronous indexing] está habilitado.
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 6f84f5b6-6c34-476c-aae5-9a8ba306f8e4
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%
---
# ACSD-46865: [!UICONTROL shipment] y [!UICONTROL credit memo] no se rellenaron cuando [!UICONTROL asynchronous indexing] está habilitado

La revisión ACSD-46865 corrige el problema en el que las cuadrículas [!UICONTROL shipment] y [!UICONTROL credit memo] no se rellenan cuando [!UICONTROL asynchronous indexing] está habilitado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24. El ID del parche es ACSD-46865. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las cuadrículas [!UICONTROL Shipment] y [!UICONTROL credit memo] no se rellenan cuando [!UICONTROL asynchronous indexing] está habilitado.

<u>Pasos a seguir</u>:

1. En el administrador de [!DNL Commerce], vaya a **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *SÍ*.
2. De nuevo, vaya a **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Limpie la caché de configuración.
4. Realice un nuevo pedido de invitado para un producto simple.
5. Corre cron.
6. Abra el pedido en el administrador de [!UICONTROL Commerce] yendo a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** y genere una factura y un abono.
7. Mover la orden a [!UICONTROL Archive].
8. Cree otro pedido para un producto simple.
9. Corre cron.
10. Vaya al nuevo pedido y genere un nuevo envío, una factura y una nota de abono.
11. Corre cron.
12. Compruebe las cuadrículas [!UICONTROL shipments], [!UICONTROL invoices] y [!UICONTROL credit memo] en el administrador.

<u>Resultados esperados</u>:

Se muestran los nuevos [!UICONTROL shipment], [!UICONTROL invoice] y [!UICONTROL credit memo].

<u>Resultados reales</u>:

No se muestran los nuevos [!UICONTROL shipment], [!UICONTROL invoice] y [!UICONTROL credit memo].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
