---
title: 'ACSD-65195: La mutación "createCompany" de GraphQL devuelve un error para un país sin una región requerida'
description: Aplique el parche ACSD-65195 para solucionar el problema de Adobe Commerce en el que la mutación createCompany de GraphQL genera un error en los países que no requieren una región.
feature: B2B, Companies, GraphQL
role: Admin, Developer
exl-id: b9eed00c-26f2-47fe-b1a0-6b020527f0c1
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
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
source-wordcount: '346'
ht-degree: 0%
---
# ACSD-65195: La mutación de GraphQL `createCompany` devuelve un error para un país sin una región requerida

El parche ACSD-65195 corrige el problema en el que la mutación [!UICONTROL GraphQL] `createCompany` genera un error en los países que no requieren una región. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63. El ID del parche es ACSD-65195. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La mutación [!UICONTROL GraphQL] `createCompany` devuelve un error cuando se especifica una región para un país que no la requiere.

<u>Pasos a seguir</u>:

1. Habilitar **[!UICONTROL B2B Companies]**.
1. Envíe la mutación `createCompany` [!UICONTROL GraphQL] con un campo de región especificado para un país que no lo requiera. Por ejemplo: [!UICONTROL country_id]: *AE* y [!UICONTROL region]: *Dubai*.
1. Compruebe la respuesta de GraphQL.

<u>Resultados esperados</u>:

La empresa debe crearse correctamente sin devolver un error cuando se especifica una región para un país que no la requiere.

<u>Resultados reales</u>:

La empresa no se crea y se devuelve el siguiente error:
`Error: Invalid value of "Dubai" provided for the region field.`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura en la nube: Actualizaciones y parches > Aplicar parches en la guía de Commerce en la infraestructura en la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
