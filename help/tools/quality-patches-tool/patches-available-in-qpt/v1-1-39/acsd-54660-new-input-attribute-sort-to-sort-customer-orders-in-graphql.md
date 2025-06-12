---
title: 'ACSD-54660: nuevo orden de atributos de entrada para ordenar los pedidos de los clientes en  [!DNL GraphQL]'
description: Aplique el parche ACSD-54660 para corregir el problema de Adobe Commerce en el que se agregó un nuevo atributo de entrada sort para ordenar los pedidos de los clientes en  [!DNL GraphQL]  por sort_field y sort_direction.
feature: GraphQL, Orders
role: Admin, Developer
exl-id: 3962d4b6-634e-4164-adae-fa840ca7d869
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# ACSD-54660: nueva ordenación de atributos de entrada agregada para ordenar los pedidos de los clientes en [!DNL GraphQL]

La revisión ACSD-54660 corrige el problema en el que se agregó un nuevo atributo de entrada `sort` para ordenar los pedidos de los clientes en [!DNL GraphQL] por `sort_field` y `sort_direction`. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39. El ID del parche es ACSD-54660. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se agregó el nuevo atributo de entrada `sort` para ordenar los pedidos de los clientes en [!DNL GraphQL] por `sort_field` y `sort_direction`.

<u>Pasos a seguir</u>:

Consultar pedidos de clientes mediante [!DNL GraphQL]:

```
  {
    customerOrders {
      items {
        order_number
        id
        created_at
        grand_total
        status
      }
    }
  }
```

<u>Resultados esperados</u>:

Este parche agrega `sort` y `sort_direction` argumentos a `customer.orders`.

<u>Resultados reales</u>:

No es posible ordenar los pedidos usando [!DNL GraphQL].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
