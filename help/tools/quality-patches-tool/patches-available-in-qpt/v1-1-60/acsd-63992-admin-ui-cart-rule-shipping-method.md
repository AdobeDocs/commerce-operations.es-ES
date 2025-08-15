---
title: 'ACSD-63992: [!UICONTROL Cart Price Rule] con error de condición de método de envío y cupón en la IU de administración'
description: Aplique el parche ACSD-63992 para solucionar el problema de Adobe Commerce donde [!UICONTROL Cart Price Rule] con un cupón y una condición basados en un método de envío no se pueden aplicar correctamente a través de la IU de administración.
feature: Price Rules, Admin Workspace
role: Admin, Developer
exl-id: 80f407c7-4552-4cfb-96ae-43773d2ec398
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-63992: [!UICONTROL Cart Price Rule] con error de condición de método de envío y cupón en la IU de administración

El parche ACSD-63992 corrige el problema en el que [!UICONTROL Cart Price Rule] con un cupón y una condición basados en un método de envío no se pueden aplicar correctamente a través de la IU de administración. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60. El ID del parche es ACSD-63992. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando una regla de carro de compras incluye una condición para el método de envío en la sección **[!UICONTROL Conditions]**, el código de cupón asociado no se aplica al crear un pedido a través del Panel de administración. En su lugar, el sistema muestra el siguiente error:

_El código de cupón &lt;> no es válido. Compruebe el código e inténtelo de nuevo._

<u>Pasos a seguir</u>:

1. Cree una regla de precios de carro de compras y describa sus condiciones:
   * En *[!UICONTROL Conditions]*: agregue una condición para incluir el método de envío (por ejemplo, *[!UICONTROL Flat Rate]*).
   * En *[!UICONTROL Rule Information]*: establezca **[!UICONTROL Coupon]** en *[!UICONTROL Specific Coupon]* y luego ingrese **[!UICONTROL Coupon Code]** como *TEST*.
1. Cree un nuevo pedido desde el Panel de administración e introduzca el código de cupón *TEST* en el campo **[!UICONTROL Apply Coupon]**.

<u>Resultados esperados</u>:

El cupón se aplica correctamente.

<u>Resultados reales</u>:

Aparece el siguiente mensaje de error:

```
"The "TEST" coupon code isn't valid. Verify the code and try again."
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
