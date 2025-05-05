---
title: 'ACSD-63182: Error al guardar un producto después de la duplicación de productos del paquete'
description: Aplique el parche ACSD-63182 para corregir el problema de Adobe Commerce en el que se produce un error al guardar un producto después de duplicar un producto del paquete con MSI habilitado.
feature: Inventory, Catalog Management
Role: Admin, Developer
source-git-commit: e532323a743512f0fdd12b6ba30d1c56e8e37e20
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# ACSD-63182: Error al guardar un producto después de la duplicación de productos del paquete

El parche ACSD-63182 corrige el problema en el que un producto simple utilizado como opción de paquete no se podía guardar después de la duplicación del producto del paquete. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. El ID del parche es ACSD-63182. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error al guardar un producto simple utilizado como opción de paquete después de duplicar el producto del paquete.

<u>Pasos a seguir</u>:

1. Crear un nuevo origen y stock de MSI.
1. Cree dos productos simples: **p1** y **p2**.
1. Crear un producto agrupado **b1** con **p1** y **p2** como opciones agrupadas.
1. Edite el **paquete de productos b1** y haga clic en ***[!UICONTROL Save and Duplicate]***.
1. Edite el **producto simple p1** y haga clic en **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

El producto se guarda sin errores.

<u>Resultados reales</u>:

Se muestra el siguiente error:
*Excepción: ya existe el elemento (Magento\Catalog\Model\Product\Interceptor) con el mismo identificador &#39;XXX&#39;.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
