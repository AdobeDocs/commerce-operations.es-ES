---
title: 'MDVA-37592: Ordenar por precio no funciona para productos con precio cero'
description: El parche de MDVA-37592 Adobe Commerce soluciona el problema de que la clasificación por precio no funciona correctamente para los productos con precio cero asignados a un catálogo compartido. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0. El ID del parche es MDVA-37592. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
exl-id: 4d4a158c-2020-42a4-9b8b-14c9b48b4107
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-37592: Ordenar por precio no funciona para productos con precio cero

El parche de MDVA-37592 Adobe Commerce soluciona el problema de que la clasificación por precio no funciona correctamente para los productos con precio cero asignados a un catálogo compartido. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0. El ID del parche es MDVA-37592. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce en nuestra arquitectura de nube 2.4.0-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los tipos de implementación) 2.3.6-2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La ordenación por precio no funciona correctamente para los productos con el precio cero asignado a un catálogo compartido.

<u>Requisitos previos</u>:

B2B está instalado.

<u>Pasos a seguir</u>:

1. Habilitar catálogo compartido.
1. Cree cuatro productos con los siguientes precios y asígnelos a una categoría: 50, 60, 70 y 80 dólares.
1. Cree un catálogo compartido con los productos anteriores.
1. Establezca el precio personalizado en cero para el producto con un precio de 70 $.
1. Ahora cree un usuario de empresa y asígnelo al catálogo compartido que acaba de crear.
1. Inicie sesión con la cuenta de empresa de y vaya a la categoría donde se asignan los productos de.
1. Intente ordenar por precio.

<u>Resultados esperados</u>:

El producto con precio cero está ordenado correctamente.

<u>Resultados reales</u>:

El producto con precio cero NO está ordenado correctamente. En su lugar, se ordena según el precio original.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
