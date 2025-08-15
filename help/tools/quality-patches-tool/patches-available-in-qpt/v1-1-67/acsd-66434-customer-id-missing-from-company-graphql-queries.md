---
title: 'ACSD-66434: [!UICONTROL Customer ID] faltan en las consultas de la compañía  [!DNL GraphQL] B'
description: Aplique el parche ACSD-66434 para solucionar el problema de Adobe Commerce en el que [!UICONTROL Customer ID] no aparece en las consultas de la empresa  [!DNL GraphQL] s.
feature: B2B, GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: cd83c868-29d8-4d7c-9067-af7597056d35
source-git-commit: e60194341bf79ca3ecdc505cf30f226b8f1b6c7f
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# ACSD-66434: faltan [!UICONTROL Customer ID] en las consultas de la empresa [!DNL GraphQL]

La revisión ACSD-66434 corrige el problema en el que **[!UICONTROL Customer ID]** no aparece en las consultas de la empresa [!DNL GraphQL]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. El ID del parche es ACSD-66434. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p10 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La consulta de la compañía [!DNL GraphQL] devuelve `null` para **[!UICONTROL Customer ID]** en la estructura de la compañía.

<u>Pasos a seguir</u>:

1. Instale el desarrollo de Adobe Commerce 2.4 con los módulos B2B e Inventario.
1. Desde el administrador de Commerce, habilite las funciones B2B y cree una empresa de prueba.
1. Genere un token de portador para el administrador de la compañía usando la siguiente mutación [!DNL GraphQL]:

```
mutation {
  generateCustomerToken(email: "admin_email@example.com", password: "admin_password") {
    token
  }
}
```

1. Utilice el token generado para recuperar la estructura de compañía del cliente con la siguiente consulta [!DNL GraphQL]:

```
query {
  company {
    id
    name
    legal_name
    structure {
      items {
        entity {
          __typename
          ... on Customer {
            firstname
            lastname
            email
            job_title
            id
          }
        }
      }
    }
  }
}
```

<u>Resultados esperados</u>:

**[!UICONTROL Customer ID]** debe devolverse en la consulta de la empresa [!DNL GraphQL].

<u>Resultados reales</u>:

**[!UICONTROL Customer ID]** devuelve como `null` en la consulta de la empresa [!DNL GraphQL].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
