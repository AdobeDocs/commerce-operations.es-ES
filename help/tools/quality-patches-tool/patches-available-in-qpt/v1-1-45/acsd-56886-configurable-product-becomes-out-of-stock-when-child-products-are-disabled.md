---
title: 'ACSD-56886: el producto configurable se queda sin existencias cuando los productos secundarios están desactivados'
description: Aplique el parche ACSD-56886 para corregir el problema de Adobe Commerce en el que el producto configurable se queda sin existencias secundario cuando los productos están desactivados.
feature: Products
role: Admin, Developer
exl-id: 5e9c1fd4-b56a-42c0-83e7-75e868213124
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-56886: el producto configurable se queda sin existencias cuando los productos secundarios están desactivados

El parche ACSD-56886 corrige el problema en el que el producto configurable se queda sin existencias cuando se desactivan los productos secundarios. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45. El ID del parche es ACSD-56886. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El producto configurable se queda sin existencias cuando los productos secundarios están desactivados.

<u>Pasos a seguir</u>:

1. Inicie sesión como administrador.
1. Establezca todos los indizadores en el modo **[!UICONTROL Update By Schedule]**.
1. Cree el siguiente producto configurable:

   * Nombre = *PRUEBA CONFIGURABLE 1*
   * Atributo = *color*
   * Valores = *red* y *black*
   * Precio del producto secundario **red** = *$100*;
   * Precio del producto secundario &quot;negro&quot; = *$200*.

1. Cree la siguiente actualización programada para el producto configurable:

   * Fecha de inicio = *3* minutos a partir de ahora.
   * Fecha de finalización = *5* minutos después de la fecha de inicio.
   * Nombre de producto = *PRUEBA CONFIGURABLE 1 editada*.
   * Deshabilite el producto secundario **red** en la sección **Configurable**.

1. Espere a la fecha de inicio.
1. Abra los detalles configurables del producto en la Tienda.

<u>Resultados esperados</u>:

El producto configurable se muestra como **En existencia** con la etiqueta **Tan bajo como 200**.

<u>Resultados reales</u>:

El producto configurable se muestra como **Agotado**.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
