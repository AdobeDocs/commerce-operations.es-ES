---
title: 'ACSD-55305: congelación emergente durante la edición por parte del usuario de la compañía en [!UICONTROL My Account]'
description: Aplique la revisión ACSD-55305 para solucionar el problema de Adobe Commerce donde la ventana emergente [!UICONTROL Edit Company User] de la página [!UICONTROL My Account] > [!UICONTROL Company Structure] se bloquea con un cargador en la pantalla.
feature: Companies, B2B
role: Admin, Developer
exl-id: eeb2b136-022f-42d5-85e2-85537f4677d6
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
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
source-wordcount: '389'
ht-degree: 0%
---
# ACSD-55305: congelación emergente durante la edición por parte del usuario de la compañía en [!UICONTROL My Account]

La revisión ACSD-55305 corrige el problema en el que la ventana emergente [!UICONTROL Edit Company User] de la página [!UICONTROL My Account]> [!UICONTROL Company Structure] se bloquea con un cargador en la pantalla. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.43. El ID del parche es ACSD-55305. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error al intentar usar la ventana emergente *[!UICONTROL Edit Company User]* en la página *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]*, ya que se bloquea con un cargador mostrado en la pantalla.

<u>Pasos a seguir</u>:

1. Crear una compañía B2B.
1. Cree un atributo de selección múltiple para los clientes.
1. Asigne un valor al atributo recién creado para el administrador de la empresa.
1. Inicie sesión como administrador de la empresa.
1. Vaya a [!UICONTROL account dashboard] y luego a **[!UICONTROL Company Structure]**.
1. Seleccione el usuario.
1. Haga clic en **[!UICONTROL Edit Selected]**.

<u>Resultados esperados</u>:

La ventana emergente del formulario aparece con precisión y proporciona la opción de editar la información de la empresa.

<u>Resultados reales</u>:

La ventana emergente del formulario aparece sin posibilidad de edición.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
