---
title: 'ACSD-63974: Corrige el tiempo de carga lento [!UICONTROL Requisition List] con paginación'
description: Aplique el parche ACSD-63974 para solucionar el problema en el que la página [!UICONTROL Requisition List] tarda mucho tiempo en cargarse cuando hay demasiados elementos.
feature: B2B
role: Admin, Developer
source-git-commit: e5f8112b870e3550b4f3a9113be48428a54d454a
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# ACSD-63974: corrige el tiempo de carga de [!UICONTROL Requisition List] lento con la paginación

La revisión ACSD-63974 corrige el problema en el cual la página **[!UICONTROL Requisition List]** tarda mucho tiempo en cargarse cuando hay demasiados elementos. Este parche está disponible cuando está instalado 1.1.61 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) . El ID parche es ACSD-63974. Tenga en cuenta que el problema está programado para solucionarse en Adobe Systems Commerce 2.4.8.

## Productos y versiones afectados

**El parche se crea para Adobe Systems versión de Commerce:**

* Adobe Systems Commerce (todos los métodos implementación) 2.4.7-p4

**Compatible con las versiones de Adobe Systems Commerce:**

* Adobe Systems Commerce (todos los métodos implementación) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con nuevas [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La página **[!UICONTROL Requisition List]** tarda mucho tiempo en cargarse cuando hay muchos elementos (más de 2000). Esto se debe a la ausencia de paginación, lo que provoca que todos los elementos se carguen a la vez.

<u>Procedimiento</u>:

1. Vaya a la **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > *[!UICONTROL General]* > **[!UICONTROL B2B features]**.
1. Configúrelo **[!UICONTROL Enable Requisition List]** en *Sí*.
1. Genera 2000+ productos editando `simple_products` nodo en `setup/performance-toolkit/profiles/ce/small.xml`.
1. Ejecute el comando:

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Crear cliente e inicie sesión.
1. añadir todos los productos al **[!UICONTROL Requisition List]** archivo .
1. Ver **[!UICONTROL Requisition List]** en la tienda.


<u>Resultados esperados</u>:

La página debe cargarse en un tiempo razonable.


<u>Resultados reales</u>:

El tiempo de carga del Página aumenta con el número de elementos porque todos los elementos se cargan a la vez debido a la ausencia de paginación.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función de su método implementación:

* Adobe Systems de comercio o Magento Open Source local: [[!DNL Quality Patches Tool] uso >](/help/tools/quality-patches-tool/usage.md) en el [!DNL Quality Patches Tool] guía.
* Adobe Systems Commerce on infraestructura en la nube: Upgrades and Patches > Aplicar Patches in the Commerce on Cloud Infrastructure guía.

## Lecturas relacionadas

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
