---
title: 'ACSD-67039: No se guardaron los registros del cliente debido a la validación de atributos del sistema rp_token'
description: Aplique el parche ACSD-67039 para corregir el problema de Adobe Commerce en el que los diacríticos de codificación provocan saltos de validación en rp_token.
feature: Customers, Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: e5995e28-b6b5-4955-a52a-895842c6b6e8
source-git-commit: 17c35f6da57440c2704879309a58c46b2c4eea25
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-67039: no se guardaron los registros del cliente debido a la validación de atributos del sistema `rp_token`

El parche ACSD-67039 corrige el problema en el que los registros del cliente no se guardaban debido a la validación del atributo del sistema `rp_token` y la validación de diacríticos solo se aplicaba al correo electrónico del cliente resultante. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. El ID del parche es ACSD-67039. Tenga en cuenta que este problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p9

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p9 - 2.4.6-p11

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los diacríticos de codificación producen errores de validación en `rp_token`, que se excluye de la validación. Los diacríticos solo se permiten para direcciones de correo electrónico, según lo previsto.

<u>Pasos a seguir</u>:

1. Instale la versión 2.4.4 de Adobe Commerce.
1. Crear un cliente.
1. Actualice Adobe Commerce a la versión 2.4.6 desde la versión 2.4.4 anterior, en la que ya se creó el cliente.
1. Establecer la clave de cifrado en `env.php` =
   *d337b914e91ff703b1e94ba4156aadf0*
1. Establezca los siguientes valores en la base de datos para cualquier cliente bajo la tabla `customer_entity`:
*`rp_token` = *incr4869*
*`rp_token_created_at` = *2021-04-29 20:06:14*
1. En el panel de administración, vaya a **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Edite el cliente para el que acaba de actualizar los valores anteriores.
1. Haga clic en **[!UICONTROL Save Customer]** o **[!UICONTROL Save and Continue Edit]**.

<u>Resultados esperados</u>:

Los valores de cliente se han guardado correctamente.

<u>Resultados reales</u>:

El registro de cliente no se ha guardado y el usuario administrador ve el mensaje de error *Se produjo un error al guardar el cliente.*
`system.log` contiene el siguiente error:

```
report.CRITICAL: Exception message: Notice: iconv(): Detected an incomplete multibyte character in input string in /vendor/magento/module-eav/Model/Attribute/Data/Text.php on line 190
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas
