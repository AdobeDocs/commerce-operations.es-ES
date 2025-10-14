---
title: 'ACSD-51102: La regla de catálogo aplicada a un gran número de productos no está indexada correctamente'
description: Aplique el parche ACSD-51102 para corregir el problema de Adobe Commerce en el que una regla de catálogo aplicada a un gran número de productos no se indexa correctamente cuando una actualización programada habilita la regla.
feature: Catalog Management, Products
role: Admin
exl-id: 35a8078d-667b-4101-8562-ece052b44c9c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# ACSD-51102: La regla de catálogo aplicada a un gran número de productos no está indexada correctamente

El parche ACSD-51102 corrige el problema de que una regla de catálogo aplicada a un gran número de productos no se indexa correctamente cuando la regla está habilitada por una actualización programada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33. El ID del parche es ACSD-51102. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Una regla de catálogo aplicada a un gran número de productos no se indexa correctamente cuando una actualización programada activa la regla.

Requisitos previos:

* El trabajo de cron se configura y se ejecuta cada minuto.

<u>Pasos a seguir</u>:

1. Cree un catálogo grande con miles de productos para conseguir el tiempo de ejecución de los indexadores de *regla de catálogo* de más de 120 segundos cuando se habiliten las reglas de catálogo.
2. Cree dos reglas de catálogo con el estado *Activo* establecido en *No*.  Por ejemplo, *Prueba 1* y *Prueba 2*. Cada regla debe afectar a todos los productos del catálogo y hacer que el indexador se ejecute durante más de 120 segundos.
3. Asegúrese de que el estado del indizador sea *Listo*.
4. Cree actualizaciones programadas para habilitar estas dos reglas. La programación de la *Prueba 2* debería comenzar poco después de la *Prueba 1*. Por ejemplo, con una diferencia de 1 minuto.
5. Consulta los precios de los productos en la Tienda.

<u>Resultados esperados</u>

Se aplican descuentos de ambas reglas.

<u>Resultados reales</u>

Solo se aplica el primer descuento de regla.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es>) en la guía [!DNL Quality Patches Tool].
