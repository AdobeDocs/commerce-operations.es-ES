---
title: 'ACSD-62212: [!UICONTROL Forgot Password] correo electrónico no traducido al idioma de vista de tienda'
description: Aplique el parche ACSD-62212 para corregir el problema de Adobe Commerce en el que el contenido del correo electrónico *[!UICONTROL Forgot Password]* no está traducido al idioma de la vista de tienda.
feature: GraphQL
role: Admin, Developer
exl-id: 29e6f2fa-574f-4ab1-82f5-88e1eb1de83e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-62212: *[!UICONTROL Forgot Password]* correo electrónico no traducido al idioma de vista de tienda

El parche ACSD-62212 corrige el problema en el que el contenido del correo electrónico *[!UICONTROL Forgot Password]* no se traduce al idioma de vista de la tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) 1.1.57. El ID del parche es ACSD-62212. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al restablecer la contraseña mediante GraphQL en una vista de tienda distinta a la registrada, el vínculo de restablecer contraseña no coincide con la vista de tienda desde la que se inició.

<u>Pasos a seguir</u>:

1. Cree una vista de almacén secundaria en *[!UICONTROL Main Website Store]*.
1. Cambiar *[!UICONTROL Locale]* a *[!UICONTROL French (France)]* en el ámbito de vista del almacén secundario.
1. Instale el paquete en francés para las traducciones.
1. Cree una cuenta de cliente.
1. Utilice la siguiente mutación de GraphQL con el encabezado *store* con el código de vista de tienda secundario.

   ```
   mutation {
       requestPasswordResetEmail(
           email: "test@gmail.com"
       )
   }
   ```

1. Compruebe el correo electrónico.

<u>Resultados esperados</u>:

* El idioma del asunto del correo electrónico, el vínculo y su contenido son coherentes con la configuración regional de la vista de tienda.
* La solicitud de restablecimiento de contraseña se envía desde el almacén en el que la cuenta del cliente está registrada, independientemente del encabezado del almacén en la solicitud.

<u>Resultados reales</u>:

Se puede observar lo siguiente en el correo electrónico:

* El vínculo restablecer contraseña tiene el código de almacén &quot;predeterminado&quot;.
* El tema está en inglés.
* El contenido está en francés.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
