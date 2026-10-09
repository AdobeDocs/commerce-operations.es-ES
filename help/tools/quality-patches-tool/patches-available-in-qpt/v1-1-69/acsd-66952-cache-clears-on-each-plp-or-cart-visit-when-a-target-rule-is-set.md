---
title: 'ACSD-66952: la caché se borra en cada visita al PLP o al carro de compras cuando se establece una regla de destino'
description: Aplique el parche ACSD-66952 para corregir el problema de Adobe Commerce en el que la caché se borraba en cada PLP o visita al carro de compras, lo que provocaba una sobrecarga de rendimiento innecesaria, cuando se establecía una regla de destino.
feature: Shopping Cart, Cache, Price Rules
role: Admin, Developer
type: Troubleshooting
exl-id: abff5761-bcf1-4cfc-b5d9-6a7e1ca907e7
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '387'
ht-degree: 0%
---
# ACSD-66952: la caché se borra en cada visita al PLP o al carro de compras cuando se establece una regla de destino

El parche ACSD-66952 corrige el problema de borrado de la caché en cada PLP o visita al carro de compras, lo que provoca una sobrecarga de rendimiento cuando se establece una regla de destino. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACSD-66952. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Problema en el que se borra la caché en cada visita al PLP o al carro de compras, lo que provoca una sobrecarga de rendimiento cuando se establece una regla de destino.

<u>Pasos a seguir</u>:

1. Genere un pequeño conjunto de datos de ejemplo.
1. Cree valores de reglas de segmentación como se indica a continuación:
   1. **[!UICONTROL Rule information]**
      * **[!UICONTROL Rule Name]** = *Productos relacionados*
      * **[!UICONTROL Status]** = *Activo*
      * **[!UICONTROL Apply to]** = *Productos relacionados*
   1. **[!UICONTROL Products to Match]**
      * Dejar en su valor predeterminado.
   1. **[!UICONTROL Products to Display]**
      * Si **ALL** de estas condiciones son *true*, establecer **[!UICONTROL Product Category]** = *Valor constante 111111*
1. Inicie la monitorización de los registros para las solicitudes de invalidación de caché.
1. Visite la página de producto de.
1. Añadir un producto al carro de compras y navegar a su página.

<u>Resultados esperados</u>:

La aplicación no debe invalidar la caché al navegar por el sitio.

<u>Resultados reales</u>:

Las etiquetas de caché se invalidan.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas
