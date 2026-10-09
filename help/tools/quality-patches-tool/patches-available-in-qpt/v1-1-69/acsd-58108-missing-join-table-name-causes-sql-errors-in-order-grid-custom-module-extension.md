---
title: 'ACSD-58108: Se producen errores de SQL en la extensión del módulo personalizado de cuadrícula de orden debido a la falta del nombre de la tabla de unión'
description: Aplique el parche ACSD-58108 para corregir el problema de Adobe Commerce en el que la falta de un nombre de tabla de unión en la extensión de módulo personalizado de cuadrícula de pedidos provoca errores de SQL al filtrar determinadas columnas.
feature: Orders, System
role: Admin, Developer
type: Troubleshooting
exl-id: 1195e1c3-575c-48d6-8a10-c300f9bbb84a
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
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
source-wordcount: '388'
ht-degree: 0%
---
# ACSD-58108: Se producen errores de SQL en la extensión del módulo personalizado de cuadrícula de orden debido a la falta del nombre de la tabla de unión

El parche ACSD-58108 corrige el problema en el que la falta de un nombre de tabla de unión en la extensión de módulo personalizado de cuadrícula de pedidos provoca errores de SQL al filtrar determinadas columnas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACSD-58108. Este problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.7-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El nombre de tabla de unión que falta en la tabla de recuperación original provoca errores de SQL en la cuadrícula de pedidos al utilizar una extensión de módulo personalizada. Este problema se debe a que la función `addFilterToMap` no funciona para ciertas columnas después de unirse a la tabla **[!UICONTROL sales_order_item]**, lo que provoca errores al filtrar.

<u>Pasos a seguir</u>:

&#x200B;01. Instale una instancia de desarrollo de 2.4.
&#x200B;02. Cree un nuevo pedido.
&#x200B;03. Instale un módulo personalizado con una extensión SQL.
&#x200B;04. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
&#x200B;05. Aplique el filtro **[!UICONTROL Purchase Date]** y espere al resultado.
&#x200B;06. Aplicar el filtro **[!UICONTROL Product SKU]**.

<u>Resultados esperados</u>:

El filtrado de pedidos en la cuadrícula de pedidos funciona sin errores.

<u>Resultados reales</u>:

Se produce un error al aplicar filtros en la cuadrícula de orden.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
