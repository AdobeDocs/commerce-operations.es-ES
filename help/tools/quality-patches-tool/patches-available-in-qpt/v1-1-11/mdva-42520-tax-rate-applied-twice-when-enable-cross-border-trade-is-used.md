---
title: 'MDVA-42520: tipo impositivo aplicado dos veces cuando se utiliza "Habilitar comercio transfronterizo"'
description: El parche de MDVA-42520 corrige el problema en el que la tasa impositiva se aplica dos veces cuando se utiliza el **Enable Cross Border Trade**. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11. El ID del parche es MDVA-42520. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Catalog Management, Orders, Taxes
role: Admin
exl-id: 34c101fd-3a47-4877-8a41-ccaeaa010969
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# MDVA-42520: tipo impositivo aplicado dos veces cuando se utiliza &quot;Habilitar comercio transfronterizo&quot;

El parche MDVA-42520 corrige el problema en el que la tasa impositiva se aplica dos veces cuando se utiliza **Habilitar comercio internacional**. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11. El ID del parche es MDVA-42520. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La tasa de impuestos se aplica dos veces cuando se usa **Habilitar comercio transfronterizo**.

<u>Pasos a seguir</u>:

1. Habilitar **Compañía**, **Catálogo compartido** y **Presupuesto**
1. Configure los impuestos según la captura de pantalla. Asegúrese de habilitar **comercio transfronterizo**.

   ![configuración de impuestos](/help/assets/tools/tax_settings_1.png){width="700"}

1. Cree un tipo impositivo para Alemania (10 %).
1. Cree una regla fiscal para aplicar el tipo impositivo.
1. Cree una empresa y un catálogo compartido personalizado.
1. Cree un producto con un precio de 100 e inclúyalo en el catálogo compartido personalizado con un descuento del 20 % en el precio.
1. Cree un cliente con una dirección en alemán y asígnelo a la compañía
1. Agregue 10 productos a la tarjeta como cliente.
1. Vaya al carro de compras y solicite un presupuesto.
1. Abra este presupuesto en el backend de e intente añadir un descuento adicional del 10%.

<u>Resultados esperados</u>:

Subtotal de Oferta (Impuestos Incluidos) y Total General de Oferta (Impuestos Incluidos) = 720 $

<u>Resultados reales</u>:

Subtotal de la oferta (impuestos incluidos) y Total general de la oferta (impuestos incluidos) = 649,50 $.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
