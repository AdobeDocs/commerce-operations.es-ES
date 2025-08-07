---
title: 'ACSD-66441: la navegación por capas muestra opciones de atributos incorrectas en la configuración de varias tiendas'
description: Aplique el parche ACSD-66441 para corregir el problema de Adobe Commerce en el que la navegación por capas muestra incorrectamente atributos de otras tiendas en una configuración de varias tiendas.
feature: Catalog Management, Search
role: Admin, Developer
type: Troubleshooting
source-git-commit: 5a8b30d1fac953ff5d921b7a7d3f12619b03bc81
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---


# ACSD-66441: la navegación por capas muestra opciones de atributos incorrectas en la configuración de varias tiendas

El parche de ACSD-66441 soluciona el problema de que la navegación por capas muestra incorrectamente atributos de otras tiendas en una configuración de varias tiendas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. El ID del parche es ACSD-66441. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La navegación por capas en la tienda incluye valores de atributos de otras tiendas, incluso cuando esos productos no están disponibles en la vista de tienda actual.

<u>Pasos a seguir</u>:

1. Crear un sitio web, una tienda y una vista de tienda secundarios.
1. Cree un producto configurable con un atributo personalizado (por ejemplo, tamaño).
1. Asigne el producto configurable al sitio web principal y a una categoría.
1. Reindexe todos los datos.
1. Vaya a la categoría asignada en la tienda. Todas las opciones de tamaño aparecen correctamente en Navegación por capas.
1. Cancele la asignación de dos productos simples del sitio web principal y asígnelos al sitio web secundario o elimínelos del sitio web principal.
1. Reindexe todos los datos.
1. Vuelva a visitar la página de categoría de tienda y marque la opción Navegación por capas.

<u>Resultados esperados</u>:

La navegación por capas solo muestra las opciones de atributos de los productos asignados a la tienda o sitio web actual.

<u>Resultados reales</u>:

La navegación por capas muestra las opciones de atributos (tamaños) de los productos asignados a otras tiendas o sitios web.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
