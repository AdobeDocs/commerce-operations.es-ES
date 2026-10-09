---
title: 'ACP2E-3753: Correos electrónicos de alerta de stock que no utilizan plantillas de temas específicas de la tienda en la configuración de varias tiendas'
description: Aplique el parche ACP2E-3753 para solucionar el problema de Adobe Commerce, donde los correos electrónicos de alerta de productos en una configuración de varias tiendas siempre se envían con la temática predeterminada, independientemente de la configuración de la tienda o el tema.
feature: Themes, Personalization
role: Admin, Developer
exl-id: ad44ffdd-f122-4119-83e3-1816951b662c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8b440f30-6794-5ed6-981f-391de4e9b0cc
    internal-label: Themes
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
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
source-wordcount: '406'
ht-degree: 0%
---
# ACP2E-3753: Correos electrónicos de alerta de stock que no utilizan plantillas de temas específicas de la tienda en la configuración de varias tiendas

El parche ACP2E-3753 corrige el problema en el que los correos electrónicos de alerta de producto en una configuración de varias tiendas siempre se enviaban utilizando el tema predeterminado, independientemente de la configuración de la tienda o el tema. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. El ID del parche es ACP2E-3753. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p11

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los correos electrónicos de alerta de producto en una configuración de varias tiendas siempre se envían con la temática predeterminada, independientemente de la configuración de la tienda o la temática.

<u>Pasos a seguir</u>:

1. Cree dos sitios web, tiendas y vistas de tiendas.
1. Cree dos temáticas independientes y asígnelas a diferentes tiendas.
1. La configuración de alertas de producto es el ámbito predeterminado que se ejecuta cada minuto.
1. Anular o agregar contenido al archivo `stock.phtml` para ambas temáticas. Ejemplo de la ubicación del archivo:

   ```text
   app\design\frontend\Adobe\Taiwan\Magento_ProductAlert\templates\email\stock.phtml
   app\design\frontend\Adobe\Japan\Magento_ProductAlert\templates\email\stock.phtml
   ```

1. Cree un usuario para cada tienda y suscríbase a la alerta de stock de productos.
1. Almacene en déclencheur la alerta de stock de productos para enviar los correos electrónicos.

<u>Resultados esperados</u>:

El correo electrónico debe incluir los cambios en el nivel de tema.

<u>Resultados reales</u>:

Los correos electrónicos no incluyen las plantillas configuradas en el sitio web o tienda correspondiente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
