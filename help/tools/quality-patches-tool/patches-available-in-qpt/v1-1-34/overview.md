---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.34'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.34.
feature: Tools and External Services
role: Admin
exl-id: d6cc3161-802c-4a1a-95b1-1eb85715643b
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.34

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.34.

QPT v1.1.34 incluye los siguientes parches:

1. **ACSD-52277**: corrige el problema en el cual un usuario administrador no es redirigido correctamente después de seleccionar la vista de tienda al crear un nuevo pedido en el administrador.
1. **ACSD-50813**: corrige el problema en el cual un administrador no puede agregar productos agrupados que contengan una barra en el SKU con la funcionalidad [!UICONTROL Add Products by SKU] al pedido del administrador.
1. **ACSD-51630**: corrige un problema en el que una gran cantidad de mensajes del sistema ralentiza la descarga de páginas de administración.
1. **ACSD-51853**: corrige el problema en el cual los estilos de texto copiados no se aplican al usar [!DNL Page Builder].
1. **ACSD-52160**: corrige el problema en el que un resultado de validación de producto contra la regla de precio del carro de compras no se evaluó correctamente, según la condición de regla *Si se ENCUENTRA/NO SE ENCUENTRA un artículo en el carro de compras con todas/cualquiera de estas condiciones como true*.
1. **ACSD-51636**: corrige un problema en el cual un administrador no puede agregar nuevos usuarios desde la sección de cuenta de cliente a pesar de tener todos los roles y permisos necesarios.
1. **ACSD-51739**: corrige el problema en el que se devuelve un error cuando se solicita `structure_id` en una solicitud de GraphQL `CompanyTeam`.
1. **ACSD-51857**: corrige el problema en el que el rendimiento lento de `aggregate_sales_report_bestsellers_data` informe cron afecta a tablas de base de datos `sales_order` y `sales_order_item` grandes.
1. **ACSD-48448**: corrige el problema en el que hay un problema de condición de carrera que se produce durante las cancelaciones de pedidos, lo que provoca entradas duplicadas en la tabla *inventory_reservation*.
1. **ACSD-52689**: corrige el problema por el que las imágenes no se pueden cargar en el almacenamiento de [!DNL Amazon S3] mediante la API de REST.

Utilice el menú de la izquierda para navegar a una página específica del parche.
