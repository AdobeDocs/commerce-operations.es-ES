---
title: 'ACSD-49480: descartar las reglas posteriores que no funcionen'
description: Aplique el parche ACSD-49480 para corregir el problema de Adobe Commerce en el que [!UICONTROL Cart Price Rule - Discard Subsequent Rules] no funciona como estaba previsto.
feature: Price Rules
role: Admin
exl-id: 1919043b-99a8-46a2-94df-9285c05bec7b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules] no funciona como estaba previsto

El parche ACSD-49480 corrige el problema en el que [!UICONTROL Cart Price Rule - Discard Subsequent Rules] no funciona como estaba previsto. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.32. El ID del parche es ACSD-49480. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] no funciona como estaba previsto.

<u>Pasos a seguir</u>:

1. Cree un **[!UICONTROL Cart Price Rule]** con un código de cupón (asígnele el nombre *TEST*) que dé un descuento de 10 $ al *Id. de producto 1* en la ficha **[!UICONTROL Actions]** con [!UICONTROL Discard Subsequent Rules] establecido en *[!UICONTROL Yes]* y [!UICONTROL Priority] establecido en *1*.
1. Cree otro(a) **[!UICONTROL Cart Price Rule]** sin un código de cupón que le dé un descuento de $5 a *Id. de producto 2* en la ficha **[!UICONTROL Actions]** con [!UICONTROL Priority] establecido en *2*. Aquí, suponemos que se trata de una venta global para el *Id. del producto 2*.
1. Vaya al sitio de front-end y agregue *ID de producto 1* e *ID de producto 2* al carro de compras.
1. Aplicar el código de cupón *TEST*.

<u>Resultados esperados</u>

* *El descuento 1* se ha aplicado a *Id. de producto 1*.
* *El descuento 2* se ha aplicado a *Id. de producto 2*.

<u>Resultados reales</u>

* Solo se aplica el *descuento 1* a *Id. de producto 1*.
* *El descuento 2* no se ha aplicado a *Id. de producto 2*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
