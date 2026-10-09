---
title: 'ACSD-43887: detalles incorrectos mostrados en la página de pago del cierre de compra'
description: El parche ACSD-43887 corrige el problema en el que se muestran detalles incorrectos en la página de pago de cierre de compra cuando se activan los pedidos de compra para empresas. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17. El ID del parche es ACSD-43887. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
exl-id: e150f093-9f1a-4ba5-bdcf-90e7f42a29c3
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 4560f5f5-d00c-5b5d-b61b-369d85ef7a26
    internal-label: User Account
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%
---
# ACSD-43887: detalles incorrectos mostrados en la página de pago del cierre de compra

El parche ACSD-43887 corrige el problema en el que se muestran detalles incorrectos en la página de pago de cierre de compra cuando se activan los pedidos de compra para empresas. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.17. El ID del parche es ACSD-43887. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los detalles incorrectos se muestran en la página de pago de cierre de compra cuando se habilitan los pedidos de compra para empresas.

<u>Requisitos previos</u>:

1. Los módulos B2B están instalados.
1. Habilitar compañía está establecida en _Sí_. Vaya a **Tiendas** > **Configuraciones** > **General** > **Características B2B** > **Habilitar compañía** > **Sí**.
1. Habilitar pedidos de compra está establecido en _Sí_. Vaya a **Configuración de aprobación de pedidos** > **Habilitar pedidos** > **Sí**.
1. PayPal Express está configurado como forma de pago.

<u>Pasos a seguir</u>:

1. Cree un producto virtual.
1. Registre una cuenta de empresa desde el front-end con un administrador de empresa.
1. Apruebe la cuenta de la compañía desde el backend y establezca **Habilitar pedidos de compra** como _Sí_ al aprobar la compañía.
1. Vaya al front-end e inicie sesión con la cuenta de administrador de la empresa creada en el paso dos.
1. Cree un &quot;Usuario predeterminado&quot; para la empresa. Vaya a **Usuario de la empresa** > **Agregar nuevo usuario**.
1. Cree una &quot;regla de aprobación&quot; para la empresa. Vaya a **Reglas de aprobación** > **Agregar nueva regla**.

   * Tipo de regla: Total de pedido
   * Total de pedido: es superior o igual a 1 $
   * Requiere aprobación de: Administrador de la empresa

1. Cierre la sesión e inicie sesión con la cuenta &quot;Usuario predeterminado&quot;.
1. Añada el producto virtual creado en el paso uno al carro de compras y continúe con el cierre de compra.
1. Selecciona PayPal Express como forma de pago y pulsa **Realizar pedido**.
1. Cierre la sesión e inicie sesión con la cuenta de administrador de la empresa.
1. Vaya a **Mis pedidos de compra** y desde **Pedidos de compra de la compañía**, haga clic en **Ver** para el pedido creado en el paso nueve.
1. Apruebe el pedido de compra. El estado del pedido de compra debe ser &quot;Aprobado: Pago pendiente&quot;.
1. Cierre la sesión y vuelva a iniciarla con la cuenta &quot;Usuario predeterminado&quot; de la empresa.
1. Vaya a **Mis pedidos** > **Ver** > **Realizar pedido**.
1. Compruebe **Resumen del pedido**.

<u>Resultados esperados</u>:

El resumen del pedido muestra valores correctos distintos de cero.

<u>Resultados reales</u>:

El valor total de resumen del pedido es cero.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
