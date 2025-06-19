---
title: 'ACSD-56635: los clientes importados se duplican cuando el uso compartido de cuentas se establece en  [!DNL Global]'
description: Aplique el parche ACSD-56635 para corregir el problema de Adobe Commerce en el que el cliente importado se duplica con la misma dirección de correo electrónico cuando la importación se utiliza con el uso compartido de cuentas establecido en  [!DNL Global].
feature: Customers, Attributes
role: Admin, Developer
exl-id: 73abec4a-03b0-45d4-bfc6-f3c6862e733c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-56635: los clientes importados se duplican con la misma dirección de correo electrónico cuando el uso compartido de cuentas se establece en [!DNL Global]

La revisión ACSD-56635 corrige el problema en el que el cliente importado se duplica con la misma dirección de correo electrónico cuando la importación se utiliza con el uso compartido de cuentas establecido en [!DNL Global]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48. El ID del parche es ACSD-56635. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los clientes importados se duplican con la misma dirección de correo electrónico cuando el uso compartido de la cuenta se establece en [!DNL Global].

<u>Pasos a seguir</u>:

1. En Adobe Commerce (2.4-development b2b) **[!UICONTROL Admin]**, acceda a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**.
1. Establezca la configuración de *[!UICONTROL Share Customer Accounts]* en *[!DNL Global]*.
1. Crear varios sitios web y tiendas:

   * ws1 > s11, s12 > sw111, sw122
   * ws2 > s21, s22 > sw211, sw212

1. Cree un nuevo cliente bajo el *sitio web principal* del administrador con la dirección de correo electrónico utilizada como <adb@yormail.com>.
1. En **[!UICONTROL Admin]**, vaya a **[!UICONTROL System]** > **[!UICONTROL Import]**.
1. Seleccione **[!UICONTROL Customer Entity Type]** como *[!UICONTROL Customers Main File]*.
1. Utilice la misma dirección de correo electrónico que <adb@yormail.com> en un sitio web diferente, por ejemplo, ws1. Consulte el archivo CSV de ejemplo customer.csv, que aparece a continuación.
1. Complete la importación para ver el nuevo usuario creado en el sitio web *ws1* con la misma dirección de correo electrónico.

contenido de customer.csv:

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>Resultados esperados</u>:

Se actualiza el cliente importado con la misma dirección de correo electrónico en lugar de duplicarlo.

<u>Resultados reales</u>:

Los clientes duplicados se crean con la misma dirección de correo electrónico al utilizar la importación de clientes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
