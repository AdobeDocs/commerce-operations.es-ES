---
title: 'ACSD-52133: la cuenta de cliente no se puede guardar después de una actualización'
description: Aplique el parche ACSD-52133 para corregir el problema de Adobe Commerce en el que una cuenta de cliente no se puede guardar después de una actualización.
feature: Customers, Upgrade
role: Admin
exl-id: 4a0e6ed8-3e35-40ce-bb49-8ccfcde437a0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-52133: la cuenta de cliente no se puede guardar después de una actualización

>[!NOTE]
>
>Este parche ha quedado obsoleto debido a un conflicto con el parche de seguridad [APSB25-08](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08).

El parche ACSD-52133 corrige el problema en el que una cuenta de cliente no se puede guardar después de una actualización. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.35. El ID del parche es ACSD-52133. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cuenta del cliente no se puede guardar después de una actualización.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce versión 2.4.4.
1. Crear un cliente.
1. Actualice Adobe Commerce a 2.4.6 desde la versión anterior de 2.4.4, en la que ya se creó un cliente.
1. Establezca la clave de cifrado como se muestra a continuación en `env.php`:

   `d337b914e91ff703b1e94ba4156aadf0`

1. Establezca los valores siguientes en la base de datos para cualquier cliente de la tabla `customer_entity`:

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Edite el cliente para el que se actualizaron los valores anteriores.
1. Haga clic en **[!UICONTROL Save Customer]** o **[!UICONTROL Save and Continue Edit]**

<u>Resultados esperados</u>:

El cliente se guarda correctamente sin errores.

<u>Resultados reales</u>:

* El registro de cliente no se ha guardado.
* El administrador ve el siguiente mensaje de error: *Se produjo un error al guardar el cliente.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool]
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
