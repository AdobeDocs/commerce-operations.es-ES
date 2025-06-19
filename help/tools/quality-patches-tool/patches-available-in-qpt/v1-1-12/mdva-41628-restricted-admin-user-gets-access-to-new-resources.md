---
title: 'MDVA-41628: Los usuarios administradores restringidos obtienen acceso a nuevos recursos'
description: El parche MDVA-41628 corrige el problema en el que los usuarios administradores restringidos pueden acceder a los nuevos recursos cuando se añaden nuevos módulos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-41628. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Admin Workspace
role: Admin
exl-id: 774a4329-fa1f-4cca-aa97-1b8ef03c11d1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# MDVA-41628: Los usuarios administradores restringidos obtienen acceso a nuevos recursos

El parche MDVA-41628 corrige el problema en el que los usuarios administradores restringidos pueden acceder a los nuevos recursos cuando se añaden nuevos módulos. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-41628. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios administradores restringidos pueden obtener acceso a los nuevos recursos cuando se añaden nuevos módulos.

<u>Pasos a seguir</u>:

1. Cree una nueva función de usuario administrador con recursos restringidos.
1. Cree un nuevo usuario administrador con la función creada en el paso uno.
1. Instale y habilite el módulo personalizado que crea un nuevo conjunto de elementos de menú junto con recursos ACL.
1. Inicie sesión con el usuario administrador recién creado.

<u>Resultados esperados</u>:

El usuario administrador con acceso restringido no puede acceder a los elementos de menú recién creados.

<u>Resultados reales</u>:

El usuario administrador restringido puede acceder a los nuevos elementos de menú, aunque los nuevos recursos no estén asignados a la función de usuario.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
