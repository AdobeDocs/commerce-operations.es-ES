---
title: 'ACSD-47004: IVA no aplicado a la dirección de facturación sin ID de IVA'
description: Aplique el parche ACSD-47004 para solucionar el problema de Adobe Commerce en el que el IVA no se aplica a una dirección de facturación sin ID de IVA.
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
exl-id: 72a64937-1c04-4fc2-bc61-fd2056e24419
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%
---
# ACSD-47004: IVA no aplicado a la dirección de facturación sin ID de IVA

El parche ACSD-47004 soluciona el problema de que el IVA no se aplica a una dirección de facturación sin un ID de IVA. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24. El ID del parche es ACSD-47004. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El IVA no se aplica a una dirección de facturación sin un ID de IVA.

<u>Pasos a seguir</u>:

1. Abra [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]** y establezca **[!UICONTROL Enable Automatic Assignment to Customer Group]** en *[!UICONTROL Yes]*.
1. Defina grupos diferentes para las validaciones de ID de IVA. Por ejemplo:

   ![Interfaz de configuración de validación de ID de IVA que muestra las opciones de configuración para la validación de impuestos](/help/assets/tools/vat-id-validations.png)

1. Registre un cliente nuevo.
1. Añadir una nueva dirección predeterminada sin IVA. Por ejemplo:

   ```text
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. Compruebe que el grupo del cliente permanece [!UICONTROL General].
1. Edita esta dirección y añade un número de IVA válido:

   ```text
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. Asegúrese de que el grupo del cliente ha cambiado a [!UICONTROL Retailer].
1. Edita la dirección y elimina el número de IVA:

   ```text
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u>Resultados esperados</u>:

El grupo de clientes se cambia automáticamente al grupo predeterminado [!UICONTROL General].

<u>Resultados reales</u>:

El grupo de clientes no se cambia automáticamente al grupo predeterminado [!UICONTROL General].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
