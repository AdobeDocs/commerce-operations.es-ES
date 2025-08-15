---
title: 'MDVA-42509: No se ha podido cargar el CSV para un pedido rápido, lo que provoca el error "No se puede enviar la cookie"'
description: El parche MDVA-42509 soluciona el problema de que no se podía cargar un CSV para un pedido rápido, lo que da como resultado el error "No se puede enviar la cookie". Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16. El ID del parche es MDVA-42509. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: B2B, Orders
role: Admin
exl-id: 6319931b-9cf1-4004-b302-737863c53ff8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-42509: No se ha podido cargar el CSV para un pedido rápido, lo que provoca el error &quot;No se puede enviar la cookie&quot;

El parche MDVA-42509 soluciona el problema que impedía cargar un CSV para un pedido rápido, lo que daba como resultado *Error al enviar la cookie*. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16. El ID del parche es MDVA-42509. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.3 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al crear un pedido rápido con un gran número de productos mediante un CSV, se muestra un error de cookie: *No se puede enviar la cookie*

<u>Pasos a seguir</u>:

1. Habilite el orden rápido navegando a **Tiendas** > **Configuración** > **Configuraciones** > **General** > **Características B2B**.
1. Cree una cuenta de cliente y vaya a **Pedido rápido** en el vínculo superior.
1. Intente crear un pedido rápido con un CSV que tenga más de 100 SKU.

<u>Resultados esperados</u>:

Puede crear un pedido rápido con un gran número de SKU.

<u>Resultados reales</u>:

Aparece un mensaje de error relacionado con el tamaño de la cookie.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
