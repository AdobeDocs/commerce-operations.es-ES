---
title: 'ACSD-63454: El valor predeterminado para los atributos Desplegable y Selección múltiple no se guarda correctamente en la base de datos'
description: Aplique el parche ACSD-63454 para solucionar el problema de Adobe Commerce en el que el valor predeterminado de los atributos Desplegable y Selección múltiple no se guarda correctamente en la base de datos.
feature: Attributes, Products
role: Admin, Developer
exl-id: fa79a3bb-e615-44cb-8d84-da892f924fd0
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 2%
---
# ACSD-63454: el valor predeterminado de los atributos [!UICONTROL Dropdown] y [!UICONTROL Multiple Select] no se ha guardado correctamente en la base de datos

La revisión ACSD-63454 corrige el problema en el que el valor predeterminado de los atributos [!UICONTROL Dropdown] y [!UICONTROL Multiple Select] no se guarda correctamente en la base de datos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. El ID del parche es ACSD-63454. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El valor predeterminado de los atributos [!UICONTROL Dropdown] y [!UICONTROL Multiple Select] no se guarda correctamente en la base de datos; en lugar de actualizar el valor predeterminado, el nuevo valor se anexa al anterior, separado por una coma.

<u>Pasos a seguir</u>:

1. Inicie sesión en el servidor, vaya a **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Product]**.
1. Haga clic en **[!UICONTROL Add New Attribute]**.
1. En la ficha **[!UICONTROL Properties]**, establezca lo siguiente:
   * **[!UICONTROL Default Label]**: *prueba*
   * **[!UICONTROL Catalog Input Type for Store Owner]**: *[!UICONTROL Multiple Select]*
   * **[!UICONTROL Manage Options]**: agregar dos opciones sin seleccionar **[!UICONTROL Is Default]**.
1. Haga clic en **[!UICONTROL Save Attribute]**.
1. Compruebe en la base de datos que la columna `default_value` está vacía.

   `select attribute_code, default_value from eav_attribute where attribute_code = 'test';`

1. Vuelva atrás y establezca una de las dos opciones como **[!UICONTROL Is Default]**.
1. Vuelva a comprobar la base de datos para asegurarse de que `default_value` contiene ahora el identificador de opción seleccionado.
1. Vuelva y seleccione la otra opción para cambiar la opción predeterminada.

<u>Resultados esperados</u>:

El nuevo valor predeterminado debe reemplazar el valor antiguo de la base de datos.

<u>Resultados reales</u>:

En lugar de reemplazar el valor predeterminado por el nuevo, anexa el nuevo valor al antiguo, separado por una coma.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
