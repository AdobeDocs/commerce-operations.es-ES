---
title: 'MDVA-42046: Valor incorrecto asignado para el atributo del producto'
description: El parche MDVA-42046 corrige el problema en el que se asigna un valor incorrecto para el atributo del producto al actualizar un producto que tiene un campo de entrada de fecha. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. El ID del parche es MDVA-42046. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Attributes, Products
role: Admin
exl-id: ff5903ff-70b3-4274-a8a1-450c2fde9750
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-42046: Valor incorrecto asignado para el atributo del producto

El parche MDVA-42046 corrige el problema en el que se asigna un valor incorrecto para el atributo del producto al actualizar un producto que tiene un campo de entrada de fecha. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. El ID del parche es MDVA-42046. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4 - 2.3.5-p2 y 2.4.0 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Después de guardar un producto con `news_from_date` y/o `news_to_date` campos, los valores de esos campos se restablecen a los valores predeterminados.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Exporte el producto creado en el paso uno.
1. En el archivo CSV exportado, coloque algunos valores en los campos `news_from_date` y `news_to_date`. Por ejemplo, 15 de mayo de 2021 y 18 de junio de 2021.
1. Importe el producto utilizando el archivo CSV modificado.
1. Añada a la cuadrícula de productos las columnas adicionales &quot;Definir producto como nuevo desde la fecha&quot; y &quot;Definir producto como nuevo desde la fecha&quot;.
1. Abra la página de edición del producto y, sin realizar ningún cambio, haga clic en **Guardar**.
1. Vuelva a la cuadrícula del producto y compruebe los datos del producto.

<u>Resultados esperados</u>:

Tanto &quot;Establecer producto como nuevo desde la fecha&quot; como &quot;Establecer producto como nuevo hasta la fecha&quot; son los mismos que antes de guardar.

<u>Resultados reales</u>:

* Los valores de las columnas &quot;Establecer producto como nuevo desde la fecha&quot; y &quot;Establecer producto como nuevo hasta la fecha&quot; cambian.

* La columna &quot;Establecer producto como nuevo desde la fecha&quot; muestra la fecha actual y la columna &quot;Establecer producto como nuevo desde la fecha&quot; está vacía.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
