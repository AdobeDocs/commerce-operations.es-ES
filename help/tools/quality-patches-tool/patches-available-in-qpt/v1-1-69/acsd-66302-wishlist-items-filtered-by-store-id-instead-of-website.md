---
title: 'ACSD-66302: elementos de lista de deseos filtrados por ID de tienda en lugar de sitio web'
description: Aplique el parche ACSD-66302 para corregir el problema de Adobe Commerce en el que los elementos de la lista de deseos se filtran por ID de tienda en lugar de por sitio web en  [!DNL GraphQL] solicitudes.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7f9a13a9a8cc666c8aa9d964da8aaff01913d35f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---


# ACSD-66302: elementos de lista de deseos filtrados por ID de tienda en lugar de sitio web

El parche ACSD-66302 corrige el problema en el que los elementos de la lista de deseos que se filtran por ID de tienda en lugar del sitio web en [!DNL GraphQL] solicitudes. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACSD-66302. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los elementos de la lista de deseos se filtran incorrectamente por ID de tienda en lugar de por sitio web.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Cree una vista de tienda adicional.
1. En Administración, vaya a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Wish List]** > **[!UICONTROL General Options]** y establezca **[!UICONTROL Enable Multiple Wish Lists]** en `Yes`.
1. Vaya a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]** y establezca **[!UICONTROL Add Store Code to Urls]** en `Yes`.
1. Cree una cuenta de cliente.
1. Usar una solicitud [!DNL GraphQL] para recuperar el token de autenticación de cliente.
1. Inicie sesión como cliente.
1. Seleccione **[!UICONTROL Default Store View]** y agregue el producto a la lista de deseos.
1. Cambiar vista de tienda a *test*.
1. Confirme que el producto sigue apareciendo en la lista de deseos (comportamiento correcto).
1. Ejecute la siguiente consulta [!DNL GraphQL]:

```
{
  customer {
    wishlists {
      id
      name
      items_count
      items_v2 {
        items {
          id
          product {
            uid
            name
            sku
          }
        }
      }
    }
  }
}
```

1. Realice la consulta en la tienda predeterminada: el producto aparece según lo esperado.
1. Realice la misma consulta en el almacén de prueba: el producto no aparece.

<u>Resultados esperados</u>:

El producto debe ser visible en todas las vistas de tienda dentro del mismo sitio web a través de [!DNL GraphQL] consultas.

<u>Resultados reales</u>:

El producto desaparece de la lista de deseos al cambiar de vista de tienda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
