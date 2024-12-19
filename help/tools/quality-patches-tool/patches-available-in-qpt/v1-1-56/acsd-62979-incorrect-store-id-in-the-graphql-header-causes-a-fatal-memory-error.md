---
title: 'ACSD-62979: un ID de tienda incorrecto en el encabezado de GraphQL provoca un error grave de memoria'
description: Aplique el parche ACSD-62979 para corregir el problema de Adobe Commerce en el que el uso del ID de almacenamiento incorrecto en el encabezado de GraphQL provoca un error grave de memoria
feature: GraphQL
role: Admin, Developer
source-git-commit: 16875f95ab23559d4e1081b8cfe0374e1394d87d
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# ACSD-62979: un ID de tienda incorrecto en el encabezado de GraphQL provoca un error grave de memoria

El parche ACSD-62979 corrige el problema en el que el uso del ID de almacén incorrecto en el encabezado de GraphQL provoca un error de memoria fatal. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. El ID del parche es ACSD-62979. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p7, 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Corrige el problema en el cual el uso del ID de almacén incorrecto en el encabezado de GraphQL provoca un error de memoria fatal.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]**). Habilitar **[!UICONTROL Add Store Code to Urls]**.
1. Ejecute debajo de la consulta de GraphQL con el valor incorrecto para el encabezado de la tienda.

```graphql
{
  categoryList(filters: { ids: { eq: "2" } }) {
    uid
    level
    name
    url_path
    image
    children {
      uid
      level
      name
      url_path
      image
      children {
        uid
        level
        name
        url_path
        image
        children {
          uid
          level
          name
          url_path
          image
        }
      }
    }
  }
}
```

<u>Resultados esperados</u>:

Mensaje de error: &quot;No se encontró el almacén solicitado. Compruebe la tienda e inténtelo de nuevo&quot;

<u>Resultados reales</u>:

Error grave como:

```Allowed memory size of 792723456 bytes exhausted```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.

