---
title: 'ACSD-51899: la dirección de envío predeterminada se rellena automáticamente de forma incorrecta'
description: Aplique el parche ACSD-51899 para corregir el problema de Adobe Commerce en el que la dirección de envío predeterminada se rellena automáticamente con una dirección incorrecta.
feature: Checkout
role: Admin
exl-id: 14e48613-6af8-476c-978d-87c27a0b0d15
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-51899: la dirección de envío predeterminada se rellena automáticamente de forma incorrecta

El parche ACSD-51899 corrige el problema en el que la dirección de envío predeterminada se rellena automáticamente con una dirección incorrecta. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.35. El ID del parche es ACSD-51899. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La dirección de envío predeterminada se rellena automáticamente con una dirección incorrecta

<u>Pasos a seguir</u>:

1. Habilitar **recogida en tienda** en el método de envío.
1. Crear *stock* y *origen*.
1. Cree un producto y asígnelo al origen.
1. Añadir un producto al carro de compras.
1. Haga clic en **Continuar con el cierre de compra** del minicarrito.
1. Escriba la dirección de correo electrónico de prueba y seleccione **Elegir en tienda**.
1. Haz clic en el botón **Seleccionar tienda** y selecciona una ubicación de tienda para elegir.
1. Haz clic en el botón **siguiente**.
1. Navegue hasta la **página principal** al hacer clic en el logotipo de la tienda.
1. Abra el **minicarrito**.
1. Haga clic en el hipervínculo inferior **Ver y editar carro**.
1. Haga clic en **Continuar con la desprotección**.
1. Pulsa el botón de envío de la página de envío.

<u>Resultados esperados</u>

El campo Dirección de envío permanece vacío excepto *País, Región y Código postal*.

<u>Resultados reales</u>

La dirección de envío predeterminada se rellena automáticamente con *dirección de recogida en tienda* después de actualizar la página.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
