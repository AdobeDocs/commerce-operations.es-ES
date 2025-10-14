---
title: 'MDVA-41229: las imágenes disponibles en el back-end no se muestran en el front-end después de importar productos configurables'
description: El parche MDVA-41229 resuelve el problema de que las imágenes disponibles en el back-end no se muestran en el front-end después de importar productos configurables. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-41229. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Data Import/Export, Configuration, Products
role: Admin
exl-id: 894fdc5b-545c-4ed8-ae1b-573d1d8d3cd6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 2%

---

# MDVA-41229: las imágenes disponibles en el back-end no se muestran en el front-end después de importar productos configurables

El parche MDVA-41229 resuelve el problema de que las imágenes disponibles en el back-end no se muestran en el front-end después de importar productos configurables. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-41229. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.2-p2 y 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las imágenes disponibles en el servidor no se muestran en el front-end después de importar los productos configurables.

<u>Pasos a seguir</u>:

1. Instale un Adobe Commerce limpio.
1. Para agregar un atributo personalizado, ve a **Tiendas** > **Atributos** > **Producto** > **Agregar nuevo atributo** con la siguiente configuración:

   * Propiedades:
      * Propiedades de atributo:

         * Etiqueta predeterminada: Establecer tamaño
         * Tipo de entrada de catálogo para el propietario de la tienda: muestra de texto
         * Valores necesarios: no
         * Actualizar imagen de vista previa del producto: sí

      * Administrar muestra (valores de su atributo):

        | Es predeterminado | Muestra de administrador | Descripción del administrador | Muestra de vista de tienda predeterminada | Descripción de vista de tienda predeterminada |
        |---|---|---|---|---|
        | no | 4 | 4 | 4 | 4 |
        | no | 24 | 24 | 24 | 24 |
        | no | 30 | 30 | 30 | 30 |
        | no | 60 | 60 | 60 | 60 |
        | no | 68 | 68 | 68 | 68 |

      * Propiedades de atributo avanzadas:

         * Código de atributo: set_size
         * Ámbito: Global
         * Valor único: No
         * Validación de entrada para el propietario de la tienda: Ninguno
         * Agregar a opciones de columna: No
         * Uso en las opciones de filtro: no

   * Administrar etiquetas:

      * Administrar títulos (tamaño, color, etc.)

         * Vista de tienda predeterminada: Establecer tamaño

   * Propiedades de tienda:

      * Usar en la búsqueda: sí
      * Peso de búsqueda: 1
      * Visible en la búsqueda avanzada: no
      * Comparable en tienda: Sí
      * Uso en la navegación por capas: filtrable (con resultados)
      * Utilizar en la navegación por capas de los resultados de búsqueda: Sí
      * Uso de las condiciones de regla de promoción: no
      * Visible en las páginas del catálogo en la tienda: Sí
      * Se utiliza en la lista de productos: Sí
      * Se utiliza para ordenar en la lista de productos: No

1. Agregue este atributo al conjunto de atributos predeterminado dentro del grupo Detalles del producto (**Almacenes** > **Atributos** > **Conjunto de atributos**).
1. Descargue las imágenes configuradas en la carpeta var dentro del directorio raíz de Adobe Commerce.
1. Vaya a **Sistema** > **Transferencia de datos** > e importe el archivo con las siguientes opciones:

   * Configuración de importación:

      * Tipo de entidad: productos

   * Comportamiento de importación:

      * Comportamiento de importación: añadir/actualizar
      * Estrategia de validación: Detener si hay error
      * Recuento de errores permitidos: 1
      * Separador de campos: `;`
      * Separador de varios valores: `,`
      * Constante de valor de atributo: EMPTYVALUE
      * Recinto de campos: sin marcar

   * Archivo para importar:

      * Seleccionar archivo para importar
      * Directorio de archivos de imágenes: déjelo vacío

1. Vaya a la tienda en `/product-set.html` página y cambie entre diferentes tamaños de conjunto. Para Set Size 24, no habrá galería.

<u>Resultados esperados</u>:

La galería para todos los productos simples dentro de un producto configurable es visible con todas las imágenes relacionadas.

<u>Resultados reales</u>:

No hay ninguna galería para los productos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
