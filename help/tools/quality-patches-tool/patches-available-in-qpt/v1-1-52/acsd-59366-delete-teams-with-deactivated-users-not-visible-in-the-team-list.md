---
title: 'ACSD-59366: elimina los equipos con usuarios desactivados que no estén visibles en la lista de equipos'
description: Aplique el parche ACSD-59366 para corregir el problema de Adobe Commerce en el que se produce un error al intentar eliminar un equipo que contiene usuarios desactivados que no están visibles en la lista de equipos.
feature: GraphQL, Companies
role: Admin, Developer
exl-id: 406d2242-38f9-4852-b311-0ee57c4a7c26
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-59366: elimina los equipos con usuarios desactivados que no estén visibles en la lista de equipos

El parche ACSD-59366 corrige el problema en el que se produce un error al intentar eliminar un equipo que contiene usuarios desactivados que no están visibles en la lista de equipos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52. El ID del parche es ACSD-59366. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error cuando se elimina un equipo que contiene usuarios desactivados que no están visibles en la lista de equipos.

<u>Requisitos previos</u>:

Los módulos B2B de Adobe Commerce están instalados y las empresas habilitadas.

<u>Pasos a seguir</u>:

1. Cree e inicie sesión con un usuario de la empresa.
1. En Estructura de la empresa, cree un nuevo equipo.
1. En el nuevo equipo, cree un nuevo usuario.
1. Edite el nuevo usuario y desactive.
1. Seleccione el equipo y elimine.

<u>Resultados esperados</u>:

El equipo tiene uno o más usuarios inactivos. Si se elimina el equipo, se anulará la asignación de estos usuarios. Puede encontrar usuarios inactivos en la sección [!UICONTROL Company Users].

<u>Resultados reales</u>:

Se produce un error cuando intenta eliminar un equipo con un usuario desactivado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
