---
title: 'ACSD-61969: Necesario para escribir el código de cupón en mayúsculas o minúsculas.'
description: Aplique el parche ACSD-61969 para corregir el problema de Adobe Commerce en el que un usuario debe escribir el código de cupón exactamente como está configurado en mayúsculas o minúsculas.
feature: Price Rules
role: Admin, Developer
exl-id: 4bdf797b-2570-49f8-8e03-952b49ed1d18
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61969: Necesario para escribir el código de cupón en mayúsculas o minúsculas.

El parche ACSD-61969 corrige el problema en el que se requiere que un usuario escriba el código de cupón exactamente como está configurado en mayúsculas o minúsculas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53. El ID del parche es ACSD-61969. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Debe escribir el código de cupón exactamente como se configuró en mayúsculas o minúsculas al aplicarlo desde el backend. Distinguen entre mayúsculas y minúsculas en la creación de pedidos de administración, pero no en la tienda.

<u>Pasos a seguir</u>:

1. Cree un(a) *[!UICONTROL Cart Price Rule]* con un cupón específico *TEST*. Asegúrese de que el código del cupón esté en mayúsculas.
1. Cree un pedido en Admin.
1. Agregue *prueba* al campo *[!UICONTROL Apply Coupon Code]* y haga clic en la flecha cerca del campo para aplicar el cupón.
1. Observe el resultado.

<u>Resultados esperados</u>:

El cupón se ha aplicado correctamente. El campo de cupón no distingue entre mayúsculas y minúsculas.

<u>Resultados reales</u>:

El cupón no se aplica. Se muestra el siguiente error:

*El código de cupón de &quot;prueba&quot; no es válido. Compruebe el código e inténtelo de nuevo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

[[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
