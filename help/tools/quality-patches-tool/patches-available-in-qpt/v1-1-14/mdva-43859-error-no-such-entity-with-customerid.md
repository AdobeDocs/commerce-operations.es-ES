---
title: 'MDVA-43859: Error "No existe esa entidad con customerId =" registrado cuando el cliente eliminado inicia sesión'
description: El parche MDVA-43859 corrige el problema por el que el error *No existe dicha entidad con el =* customerId cuando un cliente eliminado intenta iniciar sesión. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14. El ID del parche es MDVA-43859. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Variables
role: Admin
exl-id: b8451b08-978a-44a2-8664-4369e832423b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# MDVA-43859: Error &quot;No existe esa entidad con customerId =&quot; registrado cuando el cliente eliminado inicia sesión

El parche MDVA-43859 corrige el problema en el que el error *No existe esa entidad con customerId =* se registra cuando un cliente eliminado intenta iniciar sesión. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14. El ID del parche es MDVA-43859. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El error *No existe esa entidad con customerId =* cuando un cliente eliminado intenta iniciar sesión.

<u>Pasos a seguir</u>:

1. Cree una cuenta de cliente desde el front-end.
1. Cierre la sesión e inicie sesión en la cuenta de cliente creada en el paso uno.
1. Cargue el servidor en otro explorador y vaya a la cuadrícula del cliente.
1. Elimine el cliente creado en el paso uno.
1. Vuelva al primer explorador e intente cerrar la sesión.

<u>Resultados esperados</u>:

Se redirige al cliente a la página de inicio de sesión sin ningún error.

<u>Resultados reales</u>:

El cliente obtiene el siguiente error: *No existe esa entidad con customerId =*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
