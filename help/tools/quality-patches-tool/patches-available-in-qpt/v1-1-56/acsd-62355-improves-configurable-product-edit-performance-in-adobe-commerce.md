---
title: 'ACSD-62355: mejora el rendimiento de edición de productos configurables en Adobe Commerce'
description: Aplique el parche ACSD-62355 para corregir el problema de Adobe Commerce en el que la página de edición de productos configurables experimenta una carga lenta cuando el producto se basa en numerosos atributos con muchos valores.
feature: Admin Workspace
role: Admin, Developer
exl-id: cd934aa9-901a-4f03-ab83-716131e6bd85
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# ACSD-62355: mejora el rendimiento de edición de productos configurables en Adobe Commerce

El parche ACSD-62355 corrige el problema de los tiempos de carga lentos y el alto consumo de memoria en la página de edición de productos configurables cuando el producto tiene muchos atributos con numerosos valores. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. El ID del parche es ACSD-62355. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La página de edición del producto configurable tarda mucho tiempo en cargarse cuando el producto configurable se basa en varios atributos con muchos valores, lo que provoca retrasos y posibles problemas de tiempo de espera o límite de memoria.

<u>Pasos a seguir</u>:

1. Cree 9 nuevos atributos en el conjunto de atributos predeterminado, cada uno de los cuales es [!UICONTROL Filterable] y tiene [!UICONTROL Scope]: [!UICONTROL Global].
   * Atributo 1: 50 opciones
   * Atributo 2: 20 opciones
   * Atributo 3: 10 opciones
   * Atributo 4: 5 opciones
   * Atributo 5: 5 opciones
   * Atributo 6: 5 opciones
   * Atributo 7: 5 opciones
   * Atributo 8: 3 opciones
   * Atributo 9: 2 opciones

1. Cree 9 productos simples con combinaciones de opciones de los atributos recién creados.
   * Product 1: Primera opción de cada atributo
   * Product 2: Segunda opción de cada atributo
   * Producto 3: Tercera opción de cada atributo
   * Producto 4: Cuarta opción de cada atributo
   * Si un atributo tiene menos opciones que el número de productos, asigne los productos restantes a opciones aleatorias dentro de ese atributo.

1. Cree un producto configurable que utilice los atributos recién creados:
   * Añadir un producto secundario con la siguiente configuración:
      * Utilice la última opción del Atributo 1 y la primera opción de los Atributos 2 a 9.
      * Esto da como resultado 1 producto configurable y 1 producto secundario.
1. Vaya a la pestaña **[!UICONTROL Configurations]** del producto configurable.
1. Haga clic en **[!UICONTROL Add Products]** manualmente y empiece a agregar uno a uno los productos simples creados anteriormente.
1. Guarde los cambios después de cada adición.
1. A medida que añada productos, observe el tiempo de carga de la página de producto editable configurable.
1. Después de agregar 7 productos, debería notar un aumento significativo en el consumo de RAM y el tiempo de carga de la página

<u>Resultados esperados</u>:

El formulario de edición de productos se debe cargar de forma rápida y eficaz sin un consumo excesivo de memoria.

<u>Resultados reales</u>:

La edición del producto configurable tarda mucho tiempo en cargarse y puede alcanzar los límites de memoria o errores de tiempo de espera.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
