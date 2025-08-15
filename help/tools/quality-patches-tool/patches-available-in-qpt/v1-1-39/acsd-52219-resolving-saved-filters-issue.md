---
title: 'ACSD-52219: resolviendo el problema de filtro de las cuadrículas de administración en el cambio de vista de marcadores'
description: Aplique el parche ACSD-52219 para corregir el problema de Adobe Commerce en el que los filtros guardados de las cuadrículas de administración no funcionan como se espera cuando se cambia con frecuencia entre vistas de marcadores.
feature: Admin Workspace
role: Admin
exl-id: 3f1af6ba-88a0-480c-b16e-c00c655e346f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-52219: resolviendo el problema de filtro de las cuadrículas de administración en el cambio de vista de marcadores

El parche ACSD-52219 soluciona el problema de que los filtros guardados de las cuadrículas de administración no funcionan como se esperaba cuando se cambia con frecuencia entre vistas de marcadores. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39. El ID del parche es ACSD-52219. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al cambiar con frecuencia entre las vistas de marcadores, los filtros guardados en las cuadrículas de administración no funcionan según lo previsto.

<u>Pasos a seguir</u>:

1. Acceda a la cuadrícula [!DNL Sales Order] en el Administrador.
1. Cree de dos a tres filtros.
1. Compruebe la configuración del filtro cambiando de vista para asegurarse de que se guarda con precisión.
1. Vaya a Filter1 o Filter2.
1. Actualice la página para actualizar los datos mostrados.
1. Cambie a una vista diferente y observe que los filtros permanecen inalterados.
1. Observe que la vista predeterminada ahora muestra los resultados filtrados, aunque no se haya establecido ningún filtro específico para ella.

<u>Resultados esperados</u>:

Los filtros no se intercambian y conservan su estado original.

<u>Resultados reales</u>:

Al modificar una vista, los filtros se mezclan y la vista correcta no se guarda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
