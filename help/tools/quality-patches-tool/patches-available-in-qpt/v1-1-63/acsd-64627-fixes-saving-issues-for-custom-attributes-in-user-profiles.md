---
title: 'ACSD-64627: no se pueden guardar los atributos personalizados del cliente en [!UICONTROL Company Structure]'
description: Aplique el parche ACSD-64627 para corregir el problema de Adobe Commerce en el que los atributos personalizados del cliente no se pueden guardar al agregar o editar usuarios dentro de [!UICONTROL Company Structure].
feature: B2B
role: Admin, Developer
exl-id: 8e7dd72e-c21e-46cf-8e2b-9dccedfd8b04
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
source-wordcount: '396'
ht-degree: 0%
---
# ACSD-64627: no se pueden guardar los atributos personalizados del cliente en [!UICONTROL Company Structure]

La revisión ACSD-64627 corrige el problema en el cual los atributos personalizados del cliente no se pueden guardar al agregar o editar usuarios dentro de la página **[!UICONTROL Company Structure]**. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63. El ID del parche es ACSD-64627. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3, 2.4.7-p4, 2.4.8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p8, 2.4.7-p3, 2.4.7-p4, 2.4.8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los atributos personalizados del cliente no se guardan al agregar o editar usuarios en la página **[!UICONTROL Company Structure]**.

<u>Pasos a seguir</u>:

1. Instale una instancia de Adobe Commerce con las funciones B2B habilitadas.
1. Cree un nuevo atributo de cliente denominado *custom_upload* con **[!UICONTROL Input Type]** establecido en *[!UICONTROL File (attachment)]*.
1. Cree otro atributo de cliente denominado *image_attachment* con **[!UICONTROL Input Type]** establecido en *[!UICONTROL Image File]*.
1. Establezca **[!UICONTROL Show on Storefront]** en *Yes* para que ambos atributos estén visibles en la tienda. Seleccionar todos los formularios:
   * Registro de cliente
   * Edición de cuenta de cliente
   * Cierre de administración
1. Cree y active una nueva compañía.
1. Inicie sesión en la tienda como administrador de la empresa.
1. Vaya a **[!UICONTROL Customer Account]** > **[!UICONTROL Company Structure]** o a **[!UICONTROL Customer Account]** > **[!UICONTROL Company Users]**.
1. Haga clic en **[!UICONTROL Add New User]**.
1. Haga clic en **[!UICONTROL Upload]** para el atributo *custom_upload*.
1. Haga clic en **[!UICONTROL Select file]** para el atributo *image_attachment*.

<u>Resultados esperados</u>:

Se abrirá el explorador de archivos para ambos atributos. Al guardar, los valores se almacenan y los archivos se cargan correctamente.

<u>Resultados reales</u>:

Los botones no responden. No se abre el explorador de archivos ni se guardan datos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
