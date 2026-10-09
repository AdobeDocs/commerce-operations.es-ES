---
title: 'ACSD-64178: [!UICONTROL Edit Attribute Set] la página se carga lentamente con miles de atributos de producto'
description: Aplique el parche ACSD-64178 para solucionar el problema de Adobe Commerce donde la página [!UICONTROL Edit Attribute Set] se carga lentamente si hay miles de atributos de producto.
feature: Catalog Management
role: Admin, Developer
exl-id: 959d825d-1b7b-49f0-b49f-64e149106e91
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
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
source-wordcount: '318'
ht-degree: 0%
---
# ACSD-64178: [!UICONTROL Edit Attribute Set] la página se carga lentamente con miles de atributos de producto

El parche ACSD-64178 corrige el problema en el que la página **[!UICONTROL Edit Attribute Set]** se carga lentamente si hay miles de atributos de producto. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. El ID del parche es ACSD-64178. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La página **[!UICONTROL Edit Attribute Set]** se carga lentamente si hay miles de atributos de producto.

<u>Pasos a seguir</u>:

1. Cree al menos 4200 atributos sin asignar a ninguno de los conjuntos de atributos.
1. En la barra lateral de Administración, vaya a **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Attribute Set]**. Haga clic en cualquier conjunto de atributos que desee editar.

<u>Resultados esperados</u>:

La página se carga en un tiempo razonable.

<u>Resultados reales</u>:

La página tarda varios minutos en cargarse.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
