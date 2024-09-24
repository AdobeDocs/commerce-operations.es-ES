---
title: "Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.12"
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.12.
feature: Tools and External Services
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Información general de [!DNL Quality Patches Tool] (QPT) v1.1.12

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.12.

QPT v1.1.12 incluye los siguientes parches:

1. **MDVA-39546**: corrige el problema por el cual la fecha de inicio de la actualización de ensayo se podía establecer en una fecha anterior a la fecha actual durante la edición.
1. **MDVA-39713**: corrige el problema en el cual el usuario puede editar la hora de inicio de una actualización programada activa.
1. **MDVA-39993**: corrige el problema en el cual los cambios de inventario realizados a través de la API no se reflejan en la página del producto en el front-end.
1. **MDVA-41136**: corrige el problema en el que la fecha de caducidad de `mage-cache-sessid` no se amplía, lo que da como resultado la limpieza de datos del cliente.
1. **MDVA-41229**: corrige el problema en el cual las imágenes disponibles en el backend no se muestran en el front-end después de importar productos configurables.
1. **MDVA-41628**: corrige el problema en el cual los usuarios administradores restringidos existentes obtienen acceso a los nuevos recursos cuando se agregan nuevos módulos.
1. **MDVA-42410**: corrige el problema en el cual los informes de cupones solo muestran la moneda base predeterminada.
1. **MDVA-42645**: corrige el problema en el cual el administrador no puede reembolsar puntos de recompensa si la funcionalidad de crédito de tienda está deshabilitada.
1. **MDVA-42689**: corrige el problema por el que Adobe Commerce genera un error de *infracción de restricción de integridad* al actualizar las categorías de productos durante la importación.
1. **MDVA-42855**: corrige el problema que impide que se guarde una nueva dirección de cliente en la libreta de direcciones durante el cierre de compra.
1. **MDVA-42950**: corrige el problema por el que los vídeos no se reproducen en la página de producto.
1. **MDVA-43232**: corrige el problema en el cual ordenar productos en [!DNL Visual Merchandiser] por precio especial de abajo/arriba causa un error al guardar la categoría.
1. **MDVA-43348**: corrige el problema en el cual la solicitud GraphQL de tarjeta regalo muestra un error si `gift_card_options` contiene *uid*.
1. **MDVA-43414**: Corrige el error irrecuperable de PHP que ocurre al ejecutar el consumidor de cola `inventory.reservations.updateSalabilityStatus` en SKU numéricas.
1. **MDVA-43726**: corrige el problema en el que la regla de precios de catálogo basada en la coincidencia de atributos de nivel de tienda no se aplica después de un reíndice parcial.
1. **MDVA-43731**: corrige el problema en el que *Buscar sinónimos* ya no funciona cuando se agrega un valor en *Términos mínimos que deben coincidir*.

Utilice el menú de la izquierda para navegar a una página específica del parche.
