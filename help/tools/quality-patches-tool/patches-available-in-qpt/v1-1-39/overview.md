---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.39'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.39.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6116f566-2ff8-4148-ab60-cec65f9b7a6f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.39

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.39.

QPT v1.1.39 incluye los siguientes parches:

1. **ACSD-53704**: corrige el problema por el que el historial de saldo de puntos de recompensa se calcula incorrectamente después de la caducidad de los puntos de recompensa.
1. **ACSD-53583**: mejora el rendimiento de reindexación parcial para los indexadores *Category Products* y *Product Categories*.
1. **ACSD-54026**: corrige un mensaje de error incorrecto para una solicitud de GraphQL de `updateCompanyRole` para un usuario no autorizado.
1. **ACSD-54106**: corrige el problema en el que la ordenación de productos de categoría por nombre para caracteres acentuados turcos es incorrecta.
1. **ACSD-52219**: corrige el problema en el cual los filtros guardados de las cuadrículas de administración no funcionan como se esperaba cuando se cambia con frecuencia entre vistas de marcadores.
1. **ACSD-54342**: corrige un mensaje de error incorrecto *Error en la estructura de datos: los valores se mezclan* al importar un archivo CSV sin datos válidos.
1. **ACSD-54660**: se ha agregado un nuevo atributo de entrada *sort* para ordenar los pedidos de los clientes en GraphQL por `sort_field` y `sort_direction`.
1. **ACSD-54776**: corrige el problema en el cual los valores de *[!UICONTROL Use Default Value]* sin marcar y los valores de campo de producto no predeterminados no se guardan para el segundo sitio web, tienda y vista de tienda.
1. **ACSD-53998**: corrige el problema en el cual un(a) **[!UICONTROL Dynamic Block]** basado en un(a) **[!UICONTROL Customer Segment]** no funciona correctamente después de cerrar sesión desde una cuenta de cliente.
1. **ACSD-53204**: correcciones *El producto no se puede guardar.Error* al realizar solicitudes simultáneas para agregar imágenes a la galería de productos mediante el extremo `rest/V1/products/<sku>/media`.
1. **ACSD-47657**: se agregó un mecanismo de almacenamiento en caché para las credenciales de AWS. Un proveedor de credenciales ahora utiliza la caché de Magento para almacenar en caché las credenciales recuperadas de AWS para la configuración EC2.

Utilice el menú de la izquierda para navegar a una página específica del parche.
