---
title: 'ACSD-60267: el FTP se aplica incorrectamente cuando los productos se añaden mediante opciones de producto configurables'
description: Aplique el parche ACSD-60267 para corregir el problema de Adobe Commerce donde el impuesto de producto fijo (FPT) se aplica correctamente al añadir productos simples directamente al carro de compras, pero falla al seleccionar los mismos productos a través de opciones de producto configurables.
feature: Taxes
role: Admin, Developer
source-git-commit: c18ff9dd75ec6002c6461fcd3abd98ac8b97a9f7
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-60267: el FTP se aplica incorrectamente cuando los productos se añaden mediante opciones de producto configurables

El parche ACSD-60267 corrige el problema en el que el impuesto de producto fijo (FPT) se aplica correctamente al añadir productos simples directamente al carro de compras, pero falla al seleccionar los mismos productos a través de opciones de producto configurables. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.54. El ID del parche es ACSD-60267. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El impuesto sobre el producto fijo (FPT) funciona correctamente cuando se agregan productos simples con FPT al carro de compras, pero FPT no se agrega cuando se agregan productos mediante la selección de productos configurables.

<u>Pasos a seguir</u>:

1. Establezca *[!UICONTROL Enable FPT]* en *Sí* navegando a *Administración* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > **[!UICONTROL Fixed Product Taxes]**.
1. Crear un atributo FTP y asignarlo a un *[!UICONTROL Attribute Set]*.
1. Abra **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Para *[!UICONTROL Default Label]*, escriba una etiqueta que identifique el atributo.
1. Establezca *[!UICONTROL Catalog Input for Store Owner]* en *[!UICONTROL Fixed Product Tax]*.
1. Cree un nuevo impuesto y zona y asígnelos a un nuevo *[!UICONTROL Tax Rule]*.
1. Cree un producto configurable con dos productos simples.
1. Ahora asigne dos valores de FTP diferentes a esos productos simples.
1. Reindexe y compruebe los precios en la tienda.
1. Agregue los productos al carro de compras y compruebe los subtotales.

<u>Resultados esperados</u>:

* La página *[!UICONTROL Catalog]* muestra los precios, incluido el FTP.
* Los subtotales del carrito incluyen FTP.

<u>Resultados reales</u>:

* La página *[!UICONTROL Catalog]* no muestra los precios, incluido el valor FTP.
* Los subtotales y el resumen no son válidos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.

