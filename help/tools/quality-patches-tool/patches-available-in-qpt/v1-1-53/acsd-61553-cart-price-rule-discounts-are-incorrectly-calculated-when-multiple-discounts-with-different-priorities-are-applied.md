---
title: 'ACSD-61553: [!UICONTROL Cart Price Rule] se calcula incorrectamente cuando se aplican varios descuentos con diferentes prioridades'
description: Aplique el parche ACSD-61553 para resolver el problema de Adobe Commerce donde el [!UICONTROL Cart Price Rule] se calcula incorrectamente cuando se aplican varios descuentos con diferentes prioridades.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 0fb7a988-d391-49e5-a59d-62315a16132c
source-git-commit: b182fc0cd2f00f36138675277ac1de8a7179135a
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-61553: [!UICONTROL Cart Price Rule] se calcula incorrectamente cuando se aplican varios descuentos con diferentes prioridades

El parche ACSD-61553 corrige el problema en el que [!UICONTROL Cart Price Rule] se calcula incorrectamente cuando se aplican varios descuentos con diferentes prioridades. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.53. El ID del parche es ACSD-61553. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.5-p8

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!UICONTROL Cart Price Rule] se calcula incorrectamente cuando se aplican varios descuentos con diferentes prioridades.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo con un precio de 9.000 $.
1. Crear un [!UICONTROL Cart Price Rule]: regla A con un descuento fijo de 700 $ sin condiciones y sin descartar las reglas posteriores.
1. Crear otro [!UICONTROL Cart Price Rule]: regla B con un descuento fijo de 1000 $ sin condiciones y sin descartar las reglas posteriores.
1. Añada el producto con la cantidad 13 al carro de compras.
1. Actualice las reglas con cualquiera de las siguientes situaciones:

   Escenario 01

       Regla A
       Prioridad: 1
       Se ha aplicado un descuento por cantidad máxima a: 1
       
       Regla B
       Prioridad: 0
       Se ha aplicado el descuento máximo en cantidad a: 0
   
   Escenario 02

       Regla A
       Prioridad: 0
       Se ha aplicado un descuento por cantidad máxima a: 0
       
       Regla B
       Prioridad: 1
       Se ha aplicado el descuento máximo en cantidad a: 1
   
   Escenario 03

       Regla A
       Prioridad: 0
       Se ha aplicado un descuento por cantidad máxima a: 0
       
       Regla B
       Prioridad: 0
       Se ha aplicado el descuento máximo en cantidad a: 1
   
1. Haga clic en el botón **[!UICONTROL Update Shopping Cart]** para volver a calcular los descuentos.

<u>Resultados esperados</u>:

Verá el siguiente descuento total para diferentes situaciones:

    Escenario 01: 13.700 $
    Escenario 02: 10.100 $
    Escenario 03: 10.100 $

<u>Resultados reales</u>:

En los tres casos, el descuento total es de 9.000 dólares.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
