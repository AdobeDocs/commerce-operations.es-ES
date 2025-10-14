---
title: 'MDVA-38666: El usuario administrador no puede cambiar las opciones configurables del producto'
description: El parche MDVA-38666 resuelve el problema en el que el usuario administrador no puede cambiar las opciones de productos configurables en el carro de compras del cliente. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9. El ID del parche es MDVA-38666. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Admin Workspace, Configuration, Products
role: Admin
exl-id: 8e72f6a4-b36f-4fe4-bc01-2254984dd512
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-38666: El usuario administrador no puede cambiar las opciones configurables del producto

El parche MDVA-38666 resuelve el problema en el que el usuario administrador no puede cambiar las opciones de productos configurables en el carro de compras del cliente. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9. El ID del parche es MDVA-38666. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador no puede cambiar las opciones de producto configurables en el carro de compras del cliente.

<u>Pasos a seguir</u>:

1. Establezca el ámbito de la cuenta del cliente en Global.
1. Cree dos sitios web con tiendas.
1. Cree dos productos configurables y asígnelos a cada sitio web.
1. Cree una cuenta de cliente en el front-end e inicie sesión.
1. Añada un producto al carro de compras y realice un cierre de compra (esto se hace para que los identificadores de cotización sean diferentes en cada sitio web).
1. Añada un producto al carro de compras y déjelo.
1. Cambie al segundo sitio web y añada el producto al carro de compras (el mismo inicio de sesión debe funcionar, ya que el ámbito de la cuenta del cliente está establecido en Global).
1. Abra el cliente desde el administrador y vaya a la pestaña carro de compras.
1. Cambie el almacén de la lista desplegable e intente cambiar la configuración.

<u>Resultados esperados</u>:

El usuario obtiene una ventana emergente con opciones configurables.

<u>Resultados reales</u>:

No aparece ningún formulario emergente. El usuario no puede cambiar la configuración.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
