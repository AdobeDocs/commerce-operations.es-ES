---
title: 'ACSD-57570: corrección para el acceso restringido de usuarios administradores a catálogos compartidos'
description: Aplique el parche ACSD-57570 para corregir el problema de Adobe Commerce en el que un usuario administrador restringido con acceso a un almacén determinado no puede ver de forma coherente todos los catálogos compartidos asignados a productos o guardar información del cliente, lo que provoca incoherencias en el sistema.
feature: B2B, Companies, Roles/Permissions
role: Admin, Developer
source-git-commit: 6147a028e2ce783809b5c2c32c65784611d03f0e
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# ACSD-57570: corrección para el acceso restringido de usuarios administradores a catálogos compartidos

El parche ACSD-57570 soluciona el problema de que un usuario administrador restringido con acceso a un almacén concreto no puede ver de forma coherente todos los catálogos compartidos asignados a productos ni guardar información del cliente, lo que provoca incoherencias en el sistema. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. El ID del parche es ACSD-57570. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4-p9

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un usuario administrador restringido con acceso a un almacén determinado no siempre puede ver todos los catálogos compartidos ni guardar clientes, lo que provoca incoherencias. Con varias tiendas, el administrador restringido no puede ver nuevas empresas ni catálogos compartidos personalizados.

<u>Pasos a seguir</u>:

1. Configure las tiendas en el siguiente orden:
   * Cree un nuevo sitio web denominado W2.
   * Cree una nueva vista de tienda para el sitio web predeterminado.
   * Cree una nueva tienda denominada W2S2 para el sitio web W2.
   * Cree una nueva vista de tienda denominada W2S2SV1 para la tienda W2S2.
   * Cree otra nueva vista de tienda llamada W2S2SV2 para la tienda W2S2.
   * Crear una compañía para W2.
1. Asignar productos:
   * Asigne algunos productos únicamente a W1.
   * Asigne algunos productos únicamente a W2.
   * Asigne algunos productos a W1 y W2.
1. Cree un catálogo compartido personalizado y asígnele todos los productos.
1. Cree un rol de administrador personalizado con acceso solo a **W2S2**, no a **W2**.
1. Asigne el usuario administrador restringido al nuevo rol de administrador personalizado.
1. Inicie sesión como usuario administrador restringido.
1. Verificar acceso:
   * Compruebe qué compañías puede ver.
   * Compruebe qué catálogos compartidos puede ver.
   * Abra la lista de productos y compruebe si puede ver todos los catálogos compartidos a los que están asignados los productos.

<u>Resultados esperados</u>:

El comportamiento debe ser coherente.

<u>Resultados reales</u>:

Si crea únicamente un sitio web, una tienda y una vista de tienda adicionales, el usuario administrador restringido podrá ver la empresa, el catálogo compartido y ambos catálogos compartidos en la lista de productos. Con la configuración anterior, el administrador restringido no puede ver la nueva empresa ni el catálogo compartido personalizado y solo se muestra el catálogo compartido predeterminado en la lista de productos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
