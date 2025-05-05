---
title: 'ACSD-55339: solución del problema de recorte de SKU en presupuestos negociables para Adobe Commerce'
description: Aplique el parche ACSD-55339 para corregir el problema de Adobe Commerce en el que se recortan los SKU de productos con ceros a la izquierda, lo que provoca errores de negociación.
feature: B2B, Quotes
role: Admin, Developer
source-git-commit: 5153eadfe0d90c256bf6d294fcebb1dd8c0a7093
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-55339: solución del problema de recorte de SKU en presupuestos negociables para Adobe Commerce

El parche ACSD-55339 corrige el problema por el que se recortan los SKU de productos con ceros a la izquierda, lo que da como resultado errores durante el proceso de negociación. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.56. El ID del parche es ACSD-55339. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce B2B 1.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los SKU numéricos de producto con ceros a la izquierda se recortan cuando se utilizan en cotizaciones negociables, lo que da como resultado errores que impiden actualizar cantidades o establecer precios.

<u>Pasos a seguir</u>:

1. Vaya a la sección Creación de productos en el panel de administración.
1. Establezca [!UICONTROL SKU] para el producto como 01910.
1. Inicie sesión en la tienda y realice las siguientes operaciones:
   1. Añadir producto al carro de compras.
   1. Ver y editar el carro de compras.
   1. Solicite un presupuesto.
1. Vaya a [!UICONTROL admin] > [!UICONTROL Quote] > [!UICONTROL View] y [!UICONTROL Add Products by SKU] - 01910.

**Nota:** El SKU se muestra como *1910* en lugar de *01910*. Esta discrepancia impide al usuario actualizar la cantidad o establecer los precios, ya que no existe ningún producto con el SKU 1910 en el catálogo.

<u>Resultados esperados</u>:

La oferta negociable debe actualizarse correctamente sin errores.

<u>Resultados reales</u>:

Se muestra un mensaje de advertencia que indica que el producto no existe.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
