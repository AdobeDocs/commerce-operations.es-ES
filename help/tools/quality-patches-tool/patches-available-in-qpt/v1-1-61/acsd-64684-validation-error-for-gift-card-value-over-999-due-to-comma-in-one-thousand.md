---
title: 'ACSD-64684: Error de validación al guardar una tarjeta regalo con un valor superior a 999 debido a la coma en mil (1000)'
description: Aplique el parche ACSD-64684 para corregir el problema de Adobe Commerce en el que se produce un error de validación al guardar una tarjeta regalo con un valor superior a 999 debido a la coma de "mil" (1000).
feature: Catalog Management
role: Admin, Developer
exl-id: 327c5d28-b52c-4da9-a905-8a3deb755241
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64684: Error de validación al guardar una tarjeta regalo con un valor superior a 999 debido a la coma en mil (1000)

El parche ACSD-64684 corrige el problema en el que se produce un error de validación al guardar una tarjeta regalo con un valor superior a 999 debido a la coma de &quot;mil&quot; (1000). Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. El ID del parche es ACSD-64684. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error de validación al editar y guardar una tarjeta regalo con un valor mayor que 999 debido a la coma (separador de miles) en el número, como &quot;mil&quot; (1000).

<u>Pasos a seguir</u>:

1. Cree un producto de tarjeta de regalo.
   1. Escriba 1.000 como [!UICONTROL Amount].
   1. Haga clic en **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

* Se ahorra la nueva tarjeta regalo con un importe de 1.000.

<u>Resultados reales</u>:

* Se produce un error de validación cuando la cantidad de la tarjeta regalo es mayor que 999.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
