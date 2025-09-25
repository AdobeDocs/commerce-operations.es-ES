---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.71'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.71.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: db405ed4cc0f600e24b22242db9e5f48f31c2756
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.71

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.71.

QPT v1.1.71 incluye los siguientes parches:


* **ACSD-60624**: **[!UICONTROL Upload Image]** no funciona para contenido vacío en las secciones [!UICONTROL Image], [!UICONTROL Banner] y [!UICONTROL Slider] de [!DNL Page Builder].
* **ACSD-67089**: problema de paginación en la API `inventory/export-stock-salable-qty`, que limita incorrectamente `total_count` al tamaño de página.
* **ACSD-67093**: La recuperación de pedidos hasta [!DNL GraphQL] mediante el filtro de intervalo de fechas devuelve resultados incorrectos.
* **ACSD-67459**: no se pueden importar productos con descripciones de más de 65.536 caracteres.
* **ACSD-67603**: generación de mapas del sitio para productos con experiencias de procesamiento prolongadas habilitadas para la inclusión de imágenes.
* **ACSD-67643**: las entradas duplicadas se crean durante las actualizaciones programadas en entornos con un número elevado de categorías anidadas.
* **ACSD-67652**: el estado del paquete de productos se devuelve como agotado en [!DNL GraphQL] llamadas, incluso con productos secundarios y principales en existencias.
* **ACSD-67904**: los pedidos no se pueden realizar si el nombre de la ciudad contiene dígitos (0-9), el signo &amp;, puntos (.) o paréntesis ().

Utilice el menú de la izquierda para navegar a una página específica del parche.
