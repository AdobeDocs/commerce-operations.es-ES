---
title: 'ACSD-62635: productos relacionados con varias tiendas mostrados incorrectamente en [!DNL GraphQL]'
description: Aplique el parche ACSD-62635 para corregir el problema de Adobe Commerce en el que los productos relacionados con varias tiendas no se muestran correctamente en la consulta de producto [!DNL GraphQL].
feature: B2B
role: Admin, Developer
exl-id: 540cd37b-4dc5-42d1-a968-2989262effdd
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '417'
ht-degree: 0%
---
# ACSD-62635: productos relacionados con varias tiendas mostrados incorrectamente en [!DNL GraphQL]

La revisión ACSD-62635 corrige el problema en el que los productos relacionados con varias tiendas no se muestran correctamente en la consulta de producto [!DNL GraphQL]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57. El ID del parche es ACSD-62635. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando B2B está habilitado, la solicitud [!DNL GraphQL] devuelve todos los productos relacionados de todos los sitios web, incluso si se utiliza un ámbito de vista de tienda en la solicitud.

<u>Pasos a seguir</u>:

1. Cree dos sitios web, tiendas y vistas de tiendas.
1. Cree los siguientes productos simples:
   * Un elemento principal con el SKU *product1* asignado a todos los sitios web
   * Uno asignado solamente al *Sitio web 1*
   * Uno asignado solamente al *Sitio web 2*
   * Uno asignado al *Sitio web 1* y al *Sitio web 2*
1. Agregue todos los productos según se relacionan con *product1*.
1. Habilitar [!UICONTROL B2B] y [!UICONTROL Shared Catalog].
1. Añadir todos los productos al catálogo compartido predeterminado.
1. Envíe la solicitud [!DNL GraphQL] para recuperar *product1* y sus productos relacionados con el código de almacén de *Sitio web 1* en el encabezado.

<u>Resultados esperados</u>:

La respuesta solo contiene productos relacionados de los sitios web que corresponden al código de tienda enviado en el encabezado de la solicitud.

<u>Resultados reales</u>:

La respuesta contiene todos los productos relacionados de todos los sitios web, independientemente del código de tienda especificado en la solicitud.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
