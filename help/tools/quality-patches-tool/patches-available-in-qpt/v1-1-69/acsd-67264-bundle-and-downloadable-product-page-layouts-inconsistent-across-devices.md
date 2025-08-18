---
title: 'ACSD-67264: diseños de página de producto descargables y agrupados incoherentes entre dispositivos'
description: Aplique el parche ACSD-67264 para corregir el paquete de Adobe Commerce y las páginas descargables que experimentaron problemas de diseño debido a una reorganización del bloque de medios de información del producto.
feature: Page Content, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9b6794366ba552d86cdfc6a3d6f699c307fcd8f6
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# ACSD-67264: diseños de página de producto descargables y agrupados incoherentes entre dispositivos

El parche ACSD-67264 corrige el problema de que los diseños de paquete y de página de producto descargables son incoherentes entre dispositivos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACSD-67264. Tenga en cuenta que este problema se solucionó en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las páginas de producto agrupadas y descargables experimentaron problemas de diseño debido a una reorganización del bloque de medios de información del producto.

<u>Pasos a seguir</u>:

1. Instale los datos de ejemplo.
1. Abra la página del producto del paquete y compruebe el diseño en el escritorio.
1. Añada la página del producto del paquete a la lista de deseos, vaya a la lista de deseos, haga clic en el icono de edición y compruebe el diseño.
1. Repita los pasos 2 y 3 para un producto descargable.

<u>Resultados esperados</u>:

La PDP del producto del paquete se procesa sin ningún problema.

<u>Resultados reales</u>:

La PDP del producto del paquete se procesa con espacios aleatorios.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas
