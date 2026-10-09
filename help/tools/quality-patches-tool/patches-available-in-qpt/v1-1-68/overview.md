---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.68'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.68.
feature: Tools and External Services
role: Admin, Developer
exl-id: 74094036-cb1b-419f-b287-ca24d351a448
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%
---
# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.68

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.68.

QPT v1.1.68 incluye los siguientes parches:

1. **ACSD-58131** La galería de medios antigua no puede cargar imágenes debido a un archivo de imagen de 0 bytes.
1. **ACSD-62146**: la dirección de facturación seleccionada desaparece en la página de pago de cierre de compra cuando la búsqueda de direcciones está habilitada y &quot;Límite de número de direcciones de clientes&quot; está establecido en 1.
1. **ACSD-62415**: el servidor de Adobe Commerce carga las categorías muy lentamente.
1. **ACSD-65938**: se enviaron correos electrónicos con tarjeta regalo aunque se produjo un error en la creación de la factura.
1. **ACSD-66072**: los productos relacionados no se devuelven a través de GraphQL en la página de detalles del producto debido a un error interno del servidor al configurar [!UICONTROL Related Products Rule].
1. **ACSD-66082**: no se puede actualizar la imagen de muestra de un producto mediante la importación de productos.
1. **ACSD-66179**: si cancela una factura con el tipo de pago &quot;No capturar&quot;, aparecerá una página de error 404.
1. **ACSD-66233**: los usuarios administradores no pudieron agregar productos a las categorías debido a que la ventana emergente [!UICONTROL Add Product] no se cargaba.
1. **ACSD-66506**: el error del servidor se produce después de eliminar y reasignar productos del catálogo compartido.
1. **ACSD-66865**: al guardar **[!UICONTROL Catalog Price Rule]**, se invalidan los indizadores y se proporciona una alternativa para reindexar únicamente los productos afectados.
1. **ACSD-66889**: Error durante el reíndice de inventario en CLI.
1. **ACSD-66963**: La mutación de `estimateTotals` devuelve *null* para obtener descuentos cuando se aplica un código de descuento a un carro de compras con productos virtuales.
1. **ACSD-66965**: La opción de impresión de la página Lista de solicitudes produce un error.
1. **ACSD-66965**: La opción **[!UICONTROL Print]** de la página **[!UICONTROL Requisition List]** provoca un error.
1. **ACSD-67039**: los registros del cliente no se guardaron debido a la validación del atributo del sistema `rp_token`.

Utilice el menú de la izquierda para navegar a una página específica del parche.
