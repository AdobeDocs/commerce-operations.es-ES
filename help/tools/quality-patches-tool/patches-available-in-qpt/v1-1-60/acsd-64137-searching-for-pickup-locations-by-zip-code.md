---
title: 'ACSD-64137: La búsqueda de ubicaciones de recogida por código postal no funciona correctamente para la localización en neerlandés'
description: Aplique el parche ACSD-64137 para solucionar el problema en el que la búsqueda de ubicaciones de recogida por código postal no funciona correctamente para la localización en neerlandés.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 86c28b6d-6584-4caf-bd35-13e0c1bdcf1d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-64137: La búsqueda de ubicaciones de recogida por código postal no funciona correctamente para la localización en neerlandés

El parche ACSD-64137 soluciona el problema de que la búsqueda de ubicaciones de recogida por código postal no funciona correctamente en la localización en neerlandés. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60. El ID del parche es ACSD-64137. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La búsqueda con código postal de Países Bajos no muestra resultados en la página de cierre de compra de front-end. Sin embargo, funciona por ciudad y muestra la dirección correspondiente sin búsqueda.

<u>Pasos a seguir</u>:

1. Instale una instancia limpia con módulos de inventario.
1. Cree un inventario personalizado.
1. Cree dos fuentes con las direcciones de los Países Bajos y asígnelas a la población (códigos postales 7311ER y 7311AE).
1. Cree un producto sencillo y añada un inventario.
1. Para habilitar **[!UICONTROL In-Store Delivery]**, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]**.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Distance Provider for Distance Based SSA]**. **[!UICONTROL Provider]** se estableció en *cálculo sin conexión*.
1. Ejecute el siguiente comando para importar los nombres geográficos de NL country.

   ```bash
   bin/magento inventory-geonames:import NL
   ```

1. Añada el producto al carro de compras y vaya a la etapa de envío.
1. Seleccione **[!UICONTROL Pick In Store]**. A continuación, haga clic en **[!UICONTROL Select Other]** para seleccionar otras tiendas.
1. Escriba *7311* o *7311AE* en el formulario de búsqueda **[!UICONTROL Select Store]**.


**Resultados esperados**:

* Las tiendas coincidentes deben rellenarse.

**Resultados reales**:

* No se han encontrado resultados.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
