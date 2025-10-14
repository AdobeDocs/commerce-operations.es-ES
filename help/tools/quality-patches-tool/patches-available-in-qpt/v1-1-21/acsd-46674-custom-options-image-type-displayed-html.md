---
title: 'ACSD-46674: opciones personalizadas de tipo de imagen mostradas como HTML en correos electrónicos de clientes'
description: Aplique el parche ACSD-46674 para corregir el problema de Adobe Commerce donde las opciones personalizadas de tipo de imagen se muestran como HTML en los correos electrónicos de los clientes.
feature: Communications, Personalization
role: Developer
exl-id: 123ca7b5-02da-4573-897f-ff8adb184389
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-46674: opciones personalizadas de tipo de imagen mostradas como HTML en correos electrónicos de clientes

El parche ACSD-46674 corrige el problema en el que las opciones personalizadas de un tipo de imagen se muestran como HTML en los correos electrónicos de los clientes. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21. El ID del parche es ACSD-46674. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las opciones personalizadas de un tipo de imagen se muestran como HTML en los correos electrónicos del cliente.

<u>Pasos a seguir</u>:

1. Cree un producto con una opción personalizada.
   * Tipo de opción: *Archivo*
   * Extensiones de archivo compatibles: *png, jpg, gif*
   * Requerido: *Sí*
1. Realice un pedido de este producto con una imagen cargada como opción personalizada.
1. Cree una factura para el pedido creado en el paso dos.
1. Crear un abono.
1. Compruebe todos los correos electrónicos de confirmación.

<u>Resultados esperados</u>:

Los correos electrónicos de confirmación muestran la imagen cargada.

<u>Resultados reales</u>:

Los correos electrónicos de confirmación contienen código HTML sin formato en lugar de la imagen de opción personalizada del producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tools] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información acerca de otras revisiones disponibles en [!DNL QPT], consulte [[!DNL Quality Patches Tool]: Buscar revisiones](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
