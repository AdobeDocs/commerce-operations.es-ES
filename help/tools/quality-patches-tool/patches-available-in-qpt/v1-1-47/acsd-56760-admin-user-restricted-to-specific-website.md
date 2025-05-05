---
title: 'ACSD-56760: el usuario administrador está restringido a un sitio web específico y no puede ordenar ni agregar nuevos productos'
description: Aplique el parche ACSD-56760 para solucionar el problema de Adobe Commerce en el que el usuario administrador, que está restringido a un sitio web específico y no puede ordenar o agregar nuevos productos dentro de una categoría en caso de que la tienda web tenga su propia categoría raíz.
role: Admin
exl-id: 2d75164e-c463-4e1a-aa6f-f420dbe0aaeb
source-git-commit: 881d33089b15b78583e09b79e93a3f78f38bc2ca
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-56760: el usuario administrador está restringido a un sitio web específico y no puede ordenar ni agregar nuevos productos

El parche ACSD-56760 corrige el problema en el que el usuario administrador, que está restringido a un sitio web específico y no puede ordenar o agregar nuevos productos dentro de una categoría en caso de que la tienda web tenga su propia categoría raíz. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.47. El ID del parche es ACSD-56760. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8-beta1.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador que está restringido a un sitio web específico y no puede ordenar o agregar nuevos productos dentro de una categoría en caso de que la tienda web tenga su propia categoría raíz.

<u>Pasos a seguir</u>:

1. Crear *2* sitios web.
1. Crear un(a) **[!UICONTROL restricted admin user]** con acceso solamente al sitio web *1*.
1. Inicie sesión como **[!UICONTROL restricted admin user]** e intente cambiar las posiciones de los productos en una categoría.

*Caso 1*:

* *2* tiendas.
* *2* categorías raíz, cada sitio web asignó su propia raíz de categoría.

*Caso 2*:

* *2* tiendas.
* Solo se ha asignado la categoría raíz *1* a ambos sitios web.

<u>Resultados esperados</u>:

* *Caso 1*: el administrador restringido debe poder ordenar los productos dentro de la categoría disponible.
* *Caso 2*: el administrador restringido no puede ordenar productos dentro de la categoría disponible, porque esto también afectará al almacén restringido.

<u>Resultados reales</u>:

* *Caso 1*: el administrador restringido no puede ordenar productos dentro de la categoría disponible.
* *Caso 2*: el administrador restringido puede ordenar productos dentro de la categoría disponible, lo que afecta a las tiendas restringidas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
