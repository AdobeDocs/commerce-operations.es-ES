---
title: "Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.24"
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.24.
feature: Tools and External Services
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Información general de [!DNL Quality Patches Tool] (QPT) v1.1.24

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.24.

QPT v1.1.24 incluye los siguientes parches:

1. **ACSD-45168**: corrige el problema en el cual las direcciones URL compatibles con SEO no se generan para los productos que tienen los atributos *url_key* anulados en el nivel de vista de tienda.
1. **ACSD-46617**: corrige el problema en el que el botón **[!UICONTROL Continue to Checkout]** aparece atenuado incluso si el subtotal es mayor que el *Importe mínimo de pedido* configurado.
1. **ACSD-46770**: corrige el problema por el que se envían correos electrónicos de pedidos de administrador incluso cuando la *confirmación de pedidos por correo electrónico* está desmarcada.
1. **ACSD-46865**: corrige el problema en el que la cuadrícula [!UICONTROL Shipment and Credit Memo] no se rellena cuando la indización asincrónica está habilitada.
1. **ACSD-47004**: corrige el problema en el que el IVA no se aplica a una dirección de facturación sin un identificador de IVA.
1. **ACSD-47079**: corrige el problema en el que el estado de las existencias de los productos compuestos (paquete, agrupados y configurables) no se actualiza cuando el estado de las existencias de subproductos cambia a través del POST de API de REST /rest/V1/inventory/source-items.
1. **ACSD-47137**: mejora la velocidad de carga de la galería de imágenes cuando la carpeta de medios/pub es muy grande.
1. **ACSD-47336**: Correcciones *Se produjo un error.Error* al descartar las notificaciones en el administrador de Commerce.
1. **ACSD-47559**: corrige el problema en el cual el área Vista previa de plantilla de correo electrónico no es totalmente visible.
1. **ACSD-47803**: corrige el problema por el que las muestras de productos configurables sin existencias se muestran como disponibles.
1. **ACSD-47920**: corrige el problema en el cual los pedidos se pueden realizar a través de la API de REST como usuario invitado incluso cuando la opción *Permitir desprotección de invitados* está desactivada.
1. **ACSD-47955**: corrige el problema en el cual GraphQL no muestra correctamente el descuento del carro de compras.

Utilice el menú de la izquierda para navegar a una página específica del parche.
