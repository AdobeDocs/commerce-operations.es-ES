---
title: 'ACSD-63974: corrige el tiempo de carga de [!UICONTROL Requisition List] lento con la paginación'
description: Aplique el parche ACSD-63974 para solucionar el problema en el que la página [!UICONTROL Requisition List] tarda mucho tiempo en cargarse cuando hay demasiados elementos.
feature: B2B
role: Admin, Developer
exl-id: 1798baa3-da2f-44eb-8312-1f1b3f75b24d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-63974: corrige el tiempo de carga de [!UICONTROL Requisition List] lento con la paginación

La revisión ACSD-63974 corrige el problema en el cual la página **[!UICONTROL Requisition List]** tarda mucho tiempo en cargarse cuando hay demasiados elementos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. El ID del parche es ACSD-63974. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La página **[!UICONTROL Requisition List]** tarda mucho tiempo en cargarse cuando hay muchos elementos (más de 2000). Esto se debe a la ausencia de paginación, lo que provoca que todos los elementos se carguen a la vez.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > *[!UICONTROL General]* > **[!UICONTROL B2B features]**.
1. Establezca **[!UICONTROL Enable Requisition List]** en *Sí*.
1. Genere más de 2000 productos editando el nodo `simple_products` en `setup/performance-toolkit/profiles/ce/small.xml`.
1. Ejecute el comando:

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Cree un cliente e inicie sesión.
1. Agregar todos los productos a **[!UICONTROL Requisition List]**.
1. Ver **[!UICONTROL Requisition List]** en la tienda.


<u>Resultados esperados</u>:

La página debe cargarse en un tiempo razonable.


<u>Resultados reales</u>:

El tiempo de carga de la página aumenta con el número de elementos porque todos los elementos se cargan a la vez debido a la ausencia de paginación.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura en la nube: Actualizaciones y parches > Aplicar parches en la guía de Commerce en la infraestructura en la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
