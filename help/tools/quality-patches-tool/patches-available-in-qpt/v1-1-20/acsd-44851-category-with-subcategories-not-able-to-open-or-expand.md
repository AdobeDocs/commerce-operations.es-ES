---
title: 'ACSD-44851: categoría con subcategorías que no se pueden abrir o expandir'
description: Este artículo proporciona una solución al problema en el que el usuario no puede abrir o expandir una categoría con subcategorías.
feature: Categories
role: Admin
exl-id: c1ad13d8-94e1-47cf-ad65-9bc5ce1c26ad
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-44851: categoría con subcategorías que no se pueden abrir o expandir

El parche ACSD-44851 resuelve el problema en el que el usuario no puede abrir o expandir una categoría con subcategorías. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20. El ID del parche es ACSD-44851. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario no puede abrir ni expandir una categoría con subcategorías.

<u>Pasos a seguir</u>:

1. En el Administrador de Adobe Commerce, cree un árbol de categorías con dos categorías raíz y algunas subcategorías para cada una de ellas.
1. Abra la vista o el emulador móvil o reduzca el ancho de la ventana hasta que el diseño se vuelva móvil.
1. Abra el menú principal del catálogo.
1. Intente expandir las categorías raíz.
1. Intente abrir la categoría.

<u>Resultados esperados</u>:

Se puede acceder al menú.

<u>Resultados reales</u>:

El segundo nivel del menú móvil no se abre.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Herramientas de parches de calidad > Uso](/help/tools/quality-patches-tool/usage.md) en la guía de la herramienta de parches de calidad.

* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
