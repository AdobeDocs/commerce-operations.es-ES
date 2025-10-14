---
title: 'ACSD-48448: Problema de condición de carrera durante las cancelaciones de pedidos que causan entradas duplicadas en la tabla inventory_reservation'
description: Aplique el parche ACSD-48448 para corregir el problema de rendimiento de Adobe Commerce en el que el problema Race condition se produce durante las cancelaciones de pedidos, lo que provoca entradas duplicadas en la tabla inventory_reservation.
feature: Orders, Checkout
role: Admin
exl-id: c1905b60-4607-454c-975b-77b0056661ad
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-48448: *[!UICONTROL Race]* problema de condición durante las cancelaciones de pedidos que causan la entrada duplicada en la tabla `inventory_reservation`

La revisión ACSD-48448 corrige el problema en el que la condición *[!UICONTROL Race]* se produce durante las cancelaciones de pedidos, lo que provoca entradas duplicadas en la tabla `inventory_reservation`. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.34. El ID del parche es ACSD-48448. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2 y 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

*[!UICONTROL Race]* problema de condición está ocurriendo durante las cancelaciones de pedidos, lo que provoca entradas duplicadas en la tabla `inventory_reservation`.

<u>Pasos a seguir</u>:

1. Haga un pedido.
1. Compruebe la tabla `inventory_reservation` para asegurarse de que haya un registro para el evento `order_placed`.
1. Ejecute la secuencia de comandos adjunta para cancelar la solicitud en paralelo (recuerde cambiar la URL y el ID de pedido).

`bash cancel_order.sh`

```
#!/bin/bash
baseUrl=" "
orderId=3
token=$(curl --location --request POST "${baseUrl}rest/V1/integration/admin/token" \
 -H 'Content-Type: application/json' \
 -d '{
  "username": "admin",
  "password": "password"
}')
echo ${token//\"/}
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
 &
sleep 0.1;
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
wait
```

<u>Resultados esperados</u>:

Los registros no están duplicados.

<u>Resultados reales</u>:

Se crean registros duplicados en la tabla `inventory_reservation` para `order_canceled`.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool]
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
