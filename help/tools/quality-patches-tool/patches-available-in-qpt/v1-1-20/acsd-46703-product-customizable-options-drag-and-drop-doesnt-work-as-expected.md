---
title: 'ACSD-46703: La función de arrastrar y soltar para personalizar el producto no funciona'
description: Este artículo proporciona una solución al problema en el que las opciones personalizables de producto de arrastrar y soltar no funcionan según lo esperado.
feature: Products
role: Developer
exl-id: 38b9490a-c9d4-4f8e-b90f-69bf50a6b571
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-46703: La función de arrastrar y soltar para personalizar el producto no funciona

El parche ACSD-46703 corrige el problema en el que las opciones personalizables del producto (arrastrar y soltar) no funcionan según lo esperado. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20. El ID del parche es ACSD-46703. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [Herramienta de parches de calidad]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios no pueden arrastrar y soltar las opciones personalizables de una página a otra.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Añada opciones personalizables al producto simple y asegúrese de añadir más de 20 opciones que resulten en paginación.
1. Intente mover una opción personalizable (arrastrar y soltar) dentro de la misma página.
1. Ahora intente mover una opción personalizable de la página dos a la página uno.

<u>Resultados esperados</u>:

* Puede arrastrar y soltar las opciones personalizables de una página a otra.
* Puede ordenar los valores mediante la funcionalidad de arrastrar y soltar, incluso para varias páginas.

<u>Resultados reales</u>:

No puede mover ningún valor a otra página mediante la funcionalidad de arrastrar y soltar.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Herramientas de parches de calidad > Uso](/help/tools/quality-patches-tool/usage.md) en la guía de la herramienta de parches de calidad.
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
