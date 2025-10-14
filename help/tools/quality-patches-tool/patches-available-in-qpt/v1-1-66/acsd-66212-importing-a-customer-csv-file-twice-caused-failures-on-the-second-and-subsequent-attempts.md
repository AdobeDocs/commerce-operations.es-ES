---
title: 'ACSD-66212: la importación del archivo CSV del cliente dos veces provocaba errores en el segundo intento y en los posteriores'
description: Aplique el parche ACSD-66212 para corregir el problema de Adobe Commerce en el que la importación de un archivo CSV del cliente dos veces provocaba errores en el segundo intento y en los posteriores.
feature: Data Import/Export, Customers
role: Admin, Developer
exl-id: ae41f341-6ca3-405e-877a-35bdc3bc5623
source-git-commit: 5a36d0f0aaa9b7cf0ed30f0da8efac241523cf6b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# ACSD-66212: la importación del archivo CSV del cliente dos veces provocaba errores en el segundo intento y en los posteriores

El parche ACSD-66212 corrige el problema en el que la importación de un archivo CSV de cliente dos veces provocaba errores en el segundo intento y en los posteriores. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. El ID del parche es ACSD-66212. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La importación de un archivo CSV de cliente dos veces provocaba errores en el segundo y siguientes intentos.

<u>Pasos a seguir</u>:

Importe un CSV que contenga datos de clientes, incluido el estado del cliente.

<u>Resultados esperados</u>:

El estado se importa y exporta correctamente.

<u>Resultados reales</u>:

Se produce un error durante la importación:

```
General system exception happened
Additional data: <div class="messages"><div class="message message-error error"><div data-ui-id="messages-message-error" >SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near " at line 1, query was: INSERT INTO company_advanced_customer_entity (customer_id*) VALUES </div></div></div>
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
