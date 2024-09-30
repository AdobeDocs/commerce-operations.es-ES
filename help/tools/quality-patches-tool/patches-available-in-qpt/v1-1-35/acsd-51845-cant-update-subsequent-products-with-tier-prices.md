---
title: "ACSD-51845: No se pueden actualizar productos subsiguientes con precios de nivel y diferentes conjuntos de atributos a través de lotes asíncronos [!DNL API]"
description: Aplique el parche ACSD-51845 para corregir el problema de Adobe Commerce en el que no puede actualizar productos subsiguientes con precios de nivel y diferentes conjuntos de atributos a través de lotes asincrónicos  [!DNL REST API].
feature: REST, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-51845: No se pueden actualizar productos subsiguientes con precios de nivel y diferentes conjuntos de atributos a través de lotes asíncronos [!DNL API]

El parche ACSD-51845 corrige el problema que impide actualizar productos subsiguientes con precios de nivel y diferentes conjuntos de atributos a través de lotes asincrónicos [!DNL REST API]. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.35. El ID del parche es ACSD-51845. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La actualización falla para los productos subsiguientes con precios de nivel y diferentes conjuntos de atributos a través de lotes asíncronos [!DNL REST API].

<u>Pasos a seguir</u>:

1. Configurar [!DNL RabbitMQ].
1. Cree dos conjuntos de atributos.
1. Cree dos **productos simples** y asigne cada producto a un conjunto de atributos diferente.
1. Agregue un **Precio de grupo de clientes** para cada producto.
1. Actualizar ambos productos en la misma actualización masiva de [!DNL API].
1. Asegúrese de que el comando `bin/magento queue:consumers:start async.operations.all` se esté ejecutando.
1. Comprobar el estado de [!DNL API] masivo.

<u>Resultados esperados</u>:

La ejecución del servicio se realizó correctamente.

<u>Resultados reales</u>:

El sistema devuelve el mensaje de error: *No se pudo guardar el producto. Inténtelo de nuevo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
