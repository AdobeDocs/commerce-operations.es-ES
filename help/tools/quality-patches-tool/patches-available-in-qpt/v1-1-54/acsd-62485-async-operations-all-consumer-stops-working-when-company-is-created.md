---
title: 'ACSD-62485: "async.operations.all": el consumidor deja de funcionar cuando se crea la compañía'
description: Aplique el parche ACSD-62485 para corregir el problema de Adobe Commerce en el que el consumidor async.operations.all deja de funcionar cuando se crea una compañía B2B.
feature: B2B, Companies
role: Admin, Developer
exl-id: 99d20555-fe55-4a04-a067-5a2b104811f5
source-git-commit: 9d0925ae06c3ccf9ed6b2d89cec07f8f5fe2f94f
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# ACSD-62485: el consumidor `async.operations.all` deja de funcionar cuando se crea la compañía

El parche ACSD-62485 corrige el problema en el que el consumidor `async.operations.all` deja de funcionar cuando se crea una compañía B2B. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. El ID del parche es ACSD-62485. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p7

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p7, 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El consumidor `async.operations.all` deja de procesar mensajes si se crea una empresa B2B de forma asincrónica mientras el consumidor sigue ejecutándose.

<u>Requisitos previos</u>:

Los módulos B2B están instalados y habilitados.

<u>Pasos a seguir</u>:

1. Cree dos clientes.
1. Envíe una solicitud masiva de REST para crear dos empresas, asignando los clientes creados como administradores de la empresa.
1. Inicie el consumidor con el siguiente comando:

   ``` bin/magento queue:consumer:start async.operations.all --max-messages=20000 ```

<u>Resultados esperados</u>:

El consumidor procesa 20 000 mensajes y finaliza correctamente.

<u>Resultados reales</u>:

El consumidor deja de trabajar inmediatamente tras la ejecución.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
