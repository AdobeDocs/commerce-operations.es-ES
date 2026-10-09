---
title: 'ACSD-64592: los vínculos de solicitud de tarjeta de regalo de tienda no predeterminados se redirigen al sitio web predeterminado'
description: Aplique el parche ACSD-64592 para solucionar el problema en el que, en una configuración de varios sitios web, cuando se compra una tarjeta de regalo virtual desde el sitio web secundario (no predeterminado), el vínculo Código de tarjeta de regalo del correo electrónico tiene la dirección URL predeterminada del sitio web.
feature: Gift, Products
role: Admin, Developer
exl-id: 1cc026c0-7487-48e8-a092-3e72085ca38a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
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
source-wordcount: '437'
ht-degree: 0%
---
# ACSD-64592: los vínculos de solicitud de tarjeta de regalo de tienda no predeterminados se redirigen al sitio web predeterminado

El parche ACSD-64592 corrige un problema en el que, en un entorno de varios sitios, si se compra una tarjeta de regalo virtual desde un sitio web secundario (no principal), el correo electrónico que contiene el vínculo Código de tarjeta de regalo dirige a los usuarios a la dirección URL del sitio web predeterminado. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

En una configuración de varios sitios web, cuando se compra una tarjeta de regalo virtual desde un sitio secundario (no predeterminado), el correo electrónico que contiene el vínculo Código de tarjeta de regalo dirige a los usuarios a la dirección URL del sitio web predeterminado.

<u>Pasos a seguir</u>:

1. Crear un sitio web, una tienda y una vista de tienda secundarios.
1. Configure distintas direcciones URL base para el sitio web base y el sitio web secundario.
1. Cree una tarjeta de regalo virtual con algunas opciones de cantidad.
1. Generar un nuevo grupo de código en **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Gift Card Accounts]**.
1. Realice un pedido con el producto Tarjeta de regalo en el sitio web secundario.
1. Facture el pedido en el administrador de Commerce.
1. Compruebe la URL en el vínculo Código de la tarjeta regalo de *Se le ha enviado un regalo del correo electrónico de Two*.

<u>Resultados esperados</u>:

El vínculo Código de tarjeta de regalo debe tener el vínculo al segundo sitio web.

<u>Resultados reales</u>:

El vínculo Código de tarjeta regalo tiene la dirección URL predeterminada del sitio web, aunque el pedido se realice en el segundo sitio web.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:
* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
