---
title: 'ACSD-61528: La recuperación de funciones mediante GraphQL no devuelve resultados'
description: Aplique el parche ACSD-61528 para resolver el problema de Adobe Commerce donde la recuperación de funciones del administrador de la empresa mediante GraphQL siempre devuelve un resultado nulo.
feature: GraphQL, B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 81d78746-e723-4b18-860c-d973158b469c
source-git-commit: e6ba48b10918437df8846992d435d65db0669eda
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61528: La recuperación de funciones mediante GraphQL no devuelve resultados

El parche ACSD-61258 corrige el problema en el que la recuperación de funciones del administrador de la empresa mediante GraphQL siempre devuelve un resultado nulo. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53. El ID del parche es ACSD-61528. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6-p5

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al recuperar funciones del administrador de la empresa mediante GraphQL, el resultado de la función siempre era nulo.

<u>Requisitos previos:</u>:

Instale y habilite los módulos B2B de Adobe Commerce.

<u>Pasos a seguir</u>:

1. Cree una empresa.
1. Inicie sesión como administrador de la empresa en GraphQL con la siguiente mutación:

   ```GraphQL
      mutation {
          generateCustomerToken(email: "company@admin.com", password: "PASSWORD") {
      token
      }
   }
   ```

1. Agregue el token resultante a los encabezados de solicitud **Authorization** como token `Bearer` y ejecute bajo GraphQL query:

   ```GraphQL
      {
      customer {
      email
      role{
       name
       id
      }
    }
   }
   ```

<u>Resultados esperados</u>:

La consulta GraphQL devuelve el rol.

<u>Resultados reales</u>:

La función para la empresa es nula.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
