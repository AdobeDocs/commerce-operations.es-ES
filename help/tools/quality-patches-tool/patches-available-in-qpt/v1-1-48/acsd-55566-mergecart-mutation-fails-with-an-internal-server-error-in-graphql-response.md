---
title: 'ACSD-55566: la mutación [!UICONTROL mergeCart] falla con un error interno del servidor en  [!DNL GraphQL] respuesta'
description: Aplique el parche ACSD-55566 para solucionar el problema de Adobe Commerce donde la mutación mergeCart falla con un error interno del servidor en la respuesta  [!DNL GraphQL]  al combinar los carros de compras de origen y destino que tienen los mismos elementos de paquete.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84c6fbb9-73b3-4197-aff3-49743f0ebb2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-55566: la mutación `mergeCart` falla con un error interno del servidor en la respuesta [!DNL GraphQL]

La revisión ACSD-55566 corrige el problema en el que la mutación `mergeCart` falla con un error interno del servidor en la respuesta [!DNL GraphQL]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48. El ID del parche es ACSD-55566. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La mutación `mergeCart` falla con un error interno del servidor en la respuesta [!DNL GraphQL] al combinar los carros de compras de origen y destino que tienen los mismos elementos de paquete.

<u>Pasos a seguir</u>:

1. Crear una fuente personalizada y un inventario personalizado.
1. Asigne las existencias creadas al sitio web principal.
1. Cree un producto simple y asígnele el origen creado (cantidad=2).
1. Cree un producto agrupado con una opción y un producto secundario (producto creado en el paso 3).
1. Crear un carro de invitados mediante [!DNL GraphQL].
1. Agregar un paquete de productos con ambas opciones seleccionadas.
1. Guardar *cartID*.
1. Cree un cliente y genere un token de cliente.
1. Crear un carro de compras de clientes.
1. Añada el mismo producto del paquete con la misma configuración al carro de compras.
1. Intente combinar el carro de invitados con el carro de cliente.

<u>Resultados esperados</u>:

El carro del cliente contiene productos de ambos carros.

<u>Resultados reales</u>:

Se obtiene un error interno.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
