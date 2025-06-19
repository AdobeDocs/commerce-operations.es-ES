---
title: 'ACSD-63090: al eliminar un producto del administrador, se vacía el carro de compras'
description: Aplique el parche ACSD-63090 para corregir el problema de Adobe Commerce en el que los elementos del carro de compras de un cliente desaparecieron como resultado de la eliminación de un producto después de agregarlo al carro de compras.
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: c07778cb-390f-4202-9539-7bb159e4b714
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63090: al eliminar un producto del administrador, se vacía el carro de compras

El parche ACSD-63090 resuelve el problema en el que los elementos del carro de compras de un cliente desaparecieron como resultado de la eliminación de un producto del administrador, después de agregarlo al carro de compras. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. El ID del parche es ACSD-63090. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los elementos del carro de compras desaparecen cuando se elimina un producto después de agregarlo al carro de compras.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con dos productos secundarios.
1. Inicie sesión como cliente registrado.
1. Agregue ambos productos secundarios al carro de compras.
1. Cierre la sesión de la cuenta.
1. Elimine uno de los productos secundarios del catálogo.
1. Actualice el precio del otro producto secundario mediante la API.

<u>Resultados esperados</u>:

El producto restante se muestra en el carro de compras y la oferta existente se actualiza en la tabla de base de datos `quote`.

<u>Resultados reales</u>:

* El carrito está vacío.
* Se genera un nuevo registro de comillas en la tabla de base de datos `quote`.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
