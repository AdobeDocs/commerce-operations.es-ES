---
title: 'MDVA-42410: Los informes de cupones solo muestran la moneda base predeterminada'
description: El parche MDVA-42410 corrige el problema en el que los informes de cupones solo muestran la moneda base. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-42410. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Orders
role: Admin
exl-id: 97b4d9cf-12fd-4659-ad71-914c8422da37
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-42410: Los informes de cupones solo muestran la moneda base predeterminada

El parche MDVA-42410 corrige el problema en el que los informes de cupones solo muestran la moneda base. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-42410. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los informes de cupones solo muestran la moneda base predeterminada.

<u>Pasos a seguir</u>:

1. Crear un sitio web, una tienda y una vista de tienda adicionales.
1. Establece una moneda diferente para este nuevo sitio web. Por ejemplo, Euro.
1. Vaya a **Tiendas** > **Tasas de cambio** y configure las tasas de cambio a **Euro**.
1. Cree una **Regla de precio del carro de compras** con un cupón específico: **Prueba**.
1. Vaya al front-end y haga un pedido con el cupón **Test** en el nuevo sitio web.
1. Vaya a **Informes** > **Ventas** > **Cupones**.
1. Seleccione el nuevo sitio web en la lista desplegable Ámbito.
1. Actualizar estadísticas y ejecutar informes.

<u>Resultados esperados</u>:

Los informes de cupones muestran la moneda del nuevo sitio web como Euro.

<u>Resultados reales</u>:

La moneda base predeterminada (USD en este caso) se utiliza en los informes de cupones del nuevo sitio web.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
