---
title: 'ACSD-47004: IVA no aplicado a la dirección de facturación sin ID de IVA'
description: Aplique el parche ACSD-47004 para solucionar el problema de Adobe Commerce en el que el IVA no se aplica a una dirección de facturación sin ID de IVA.
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
exl-id: 72a64937-1c04-4fc2-bc61-fd2056e24419
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 1%

---

# ACSD-47004: IVA no aplicado a la dirección de facturación sin ID de IVA

El parche ACSD-47004 soluciona el problema de que el IVA no se aplica a una dirección de facturación sin un ID de IVA. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24. El ID del parche es ACSD-47004. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El IVA no se aplica a una dirección de facturación sin un ID de IVA.

<u>Pasos a seguir</u>:

1. Abra [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]** y establezca **[!UICONTROL Enable Automatic Assignment to Customer Group]** en *[!UICONTROL Yes]*.
1. Defina grupos diferentes para las validaciones de ID de IVA. Por ejemplo:

   ![Validaciones de ID de IVA](/help/assets/tools/vat-id-validations.png)

1. Registre un cliente nuevo.
1. Añadir una nueva dirección predeterminada sin IVA. Por ejemplo:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. Compruebe que el grupo del cliente permanece [!UICONTROL General].
1. Edita esta dirección y añade un número de IVA válido:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. Asegúrese de que el grupo del cliente ha cambiado a [!UICONTROL Retailer].
1. Edita la dirección y elimina el número de IVA:

   ```
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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
