---
title: 'ACSD-46869: los productos configurables no se actualizan mediante la API de REST al cerrar la compra'
description: El parche ACSD-46869 corrige el problema en el que los productos configurables no se actualizan mediante la API de REST en el cierre de compra. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20. El ID del parche es ACSD-46869. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
exl-id: f03d4b24-ac95-406e-8e9d-908149b9207c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-46869: los productos configurables no se actualizan mediante la API de REST al cerrar la compra

El parche ACSD-46869 corrige el problema en el que los productos configurables no se actualizan mediante la API de REST al cerrar la compra. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20. El ID del parche es ACSD-46869. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la [[!DNL QPT] página de aterrizaje](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos configurables no se actualizan mediante la API de REST durante el cierre de compra.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con atributos de color y tamaño.
1. Seleccione **[!UICONTROL Options]** y agregue el producto al carro de compras.
1. Vaya a **[!UICONTROL Checkout]**, actualice el tamaño varias veces excepto para la cantidad y compruebe la solicitud y la respuesta.
1. Recibirá la siguiente respuesta cuando actualice el tamaño.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Resultados esperados</u>:

El valor se actualiza según los cambios.

<u>Resultados reales</u>:

`option_value` no se ha actualizado, por lo que cuando se realiza el pedido, tiene el valor de tamaño anterior.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tools] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía de la herramienta Parches de calidad.
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
