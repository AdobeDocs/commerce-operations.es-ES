---
title: 'ACSD-63325: Error de sintaxis: &lt;EOF&gt; inesperado al enviar  [!DNL GraphQL] solicitud vacía'
description: Aplique el parche ACSD-63325 para corregir el problema de Adobe Commerce donde se produce un error de sintaxis al enviar una solicitud  [!DNL GraphQL] vacía.
feature: GraphQL
Role: Admin, Developer
exl-id: a83a8c5f-a43a-4733-a601-7b92656e5325
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# ACSD-63325: &quot;Error de sintaxis: &lt; EOF > inesperado&quot; al enviar una solicitud [!DNL GraphQL] vacía

El parche ACSD-63325 corrige el problema donde se devolvía un error &quot;Sintaxis: Inesperada &lt; EOF >&quot; y un código de respuesta distinto de 200 al enviar una solicitud [!DNL GraphQL] vacía. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. El ID del parche es ACSD-63325. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al enviar una solicitud [!DNL GraphQL] vacía, se produce un error de servidor interno HTTP en lugar de un código de respuesta 200.

<u>Pasos a seguir</u>:

1. Enviar una solicitud de GraphQL vacía

   ```graphql
   curl -i -X OPTIONS http://commerce.local/graphql
   ```

<u>Resultados esperados</u>:

El código de respuesta es 200 para la solicitud.

```
curl -i -X OPTIONS http://commerce.local/graphql
```

<u>Resultados reales</u>:

Se produce un error de servidor interno 500 como se muestra:

```
HTTP/1.1 500 Internal Server Error
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en infraestructura de nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) en la guía Commerce en infraestructura de nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
