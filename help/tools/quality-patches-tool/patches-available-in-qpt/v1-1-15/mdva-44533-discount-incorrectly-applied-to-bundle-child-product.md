---
title: 'MDVA-44533: descuento aplicado incorrectamente al producto secundario empaquetado'
description: El parche MDVA-44533 corrige el problema en el que un descuento se aplica incorrectamente a un producto secundario empaquetado. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15. El ID del parche es MDVA-44533. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Orders, Personalization, Products
role: Admin
exl-id: 150fe577-a61a-451e-838a-d60be7754bf4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-44533: descuento aplicado incorrectamente al producto secundario empaquetado

El parche MDVA-44533 corrige el problema en el que un descuento se aplica incorrectamente a un producto secundario empaquetado. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15. El ID del parche es MDVA-44533. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El descuento se aplica incorrectamente a un producto secundario empaquetado.

<u>Pasos a seguir</u>:

1. Crea un producto sencillo con un precio de 50$.
1. Cree un producto agrupado y asigne el producto simple como la única opción para el producto agrupado.
1. Crear una regla de precio de carro de compras con:

   * Condición: si la cantidad total es mayor que 130 $
   * Acción: se aplica un descuento de importe fijo de 10$

1. Vaya a la tienda y añada el producto del paquete al carro con la cantidad = 1.
1. Vaya al carro y compruebe que el coste total del producto del paquete es de 50 $ y que no se aplica el descuento.
1. Cambie la cantidad a 2 y actualice el carro de compras. El coste total del producto agrupado ahora debe ser de 100 $.

<u>Resultados esperados</u>:

El descuento no se aplica porque el subtotal es 100\$, que es inferior a 130\$ en la condición de regla.

<u>Resultados reales</u>:

Se aplica el descuento.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
