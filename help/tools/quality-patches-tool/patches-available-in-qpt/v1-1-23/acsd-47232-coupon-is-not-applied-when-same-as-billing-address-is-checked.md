---
title: 'ACSD-47232: el cupón no se aplica cuando se comprueba [!UICONTROL Same as Billing Address]'
description: Aplique el parche ACSD-47232 para corregir el problema de Adobe Commerce en el que el cupón no se aplica cuando se marca [!UICONTROL Same as Billing Address].
feature: Orders, Shipping/Delivery
role: Admin
exl-id: d8050f6e-00a9-4aa3-bb8b-1631e0e7a714
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-47232: el cupón no se aplica cuando se comprueba [!UICONTROL Same as Billing Address]

El parche ACSD-47232 corrige el problema en el que el cupón no se aplica cuando se comprueba **[!UICONTROL Same as Billing Address]**. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23. El ID del parche es ACSD-47232. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El cupón no se aplica cuando se marca **[!UICONTROL Same as Billing Address]**.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce.
1. Crear un producto simple con peso = *8*.
1. Crear un cliente nuevo con la dirección de facturación y envío predeterminada.
1. Cree una regla de precio de carro de compras con un cupón.
   * En **[!UICONTROL Conditions]** secciones, agregue *Peso total igual o mayor que 5*
1. Intente crear un nuevo orden en el administrador de [!UICONTROL Commerce].
   * Utilice el cliente creado justo ahora
   * Agregar un producto
   * Intente aplicar el cupón

<u>Resultados esperados</u>:

Se aplica el cupón.

<u>Resultados reales</u>:

Recibe un error similar al siguiente: *El código de cupón 123 no es válido. Compruebe el código e inténtelo de nuevo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
