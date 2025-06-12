---
title: 'ACSD-51240: falta el archivo cargado al registrarse a través del formulario de registro de la empresa'
description: Aplique el parche ACSD-51240 para solucionar el problema de Adobe Commerce en el que falta el archivo cargado al registrarse mediante el formulario de registro de la empresa.
exl-id: 78e339d6-435e-4856-9f57-98bb955d093c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51240: falta el archivo cargado al registrarse a través del formulario de registro de la empresa

>[!NOTE]
>
>Este parche se reemplazó por [ACSD-55628](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md).

El parche ACSD-51240 corrige el problema en el que el archivo cargado no se encuentra al registrarse a través del formulario de registro de la empresa. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33. El ID del parche es ACSD-51240. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es>). Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Problema

Falta el archivo cargado al registrarse mediante el formulario de registro de empresa.

<u>Pasos a seguir</u>:

1. Establecer **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *Sí*.
1. Cree un nuevo atributo de cliente de tipo **[!UICONTROL File]**, establezca **[!UICONTROL Show in StoreFront]** = *Sí* y seleccione **[!UICONTROL all forms]**.
1. Cree una nueva compañía en la Tienda y cargue una imagen para el nuevo atributo.
Abra la compañía y el usuario administrador en la Tienda.

<u>Resultados esperados</u>:

Se muestra el archivo cargado.

<u>Resultados reales</u>:

El archivo cargado no se muestra en la página de la compañía ni en la página del cliente administrador de [!UICONTROL Commerce Admin].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
