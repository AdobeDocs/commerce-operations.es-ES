---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.71'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.71.
feature: Tools and External Services
role: Admin, Developer
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
source-wordcount: '185'
ht-degree: 0%
---
# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.71

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.71.

QPT v1.1.71 incluye los siguientes parches:


* **ACSD-60624**: Error al cargar imagen por contenido vacío en las secciones Imagen, Titular y Regulador en [!DNL Page Builder]
* **ACSD-67089**: problema de paginación en la API `inventory/export-stock-salable-qty`, que limita incorrectamente `total_count` al tamaño de página.
* **ACSD-67093**: La recuperación de pedidos hasta [!DNL GraphQL] mediante el filtro de intervalo de fechas devuelve resultados incorrectos.
* **ACSD-67459**: no se pueden importar productos con descripciones de más de 65.536 caracteres.
* **ACSD-67603**: Tiempos de procesamiento largos de generación de mapas del sitio para productos con la inclusión de imágenes habilitada
* **ACSD-67643**: las entradas duplicadas se crean durante las actualizaciones programadas en entornos con un número elevado de categorías anidadas.
* **ACSD-67652**: el estado del paquete de productos se devuelve como agotado en [!DNL GraphQL] llamadas, incluso con productos secundarios y principales en existencias.
* **ACSD-67904**: los pedidos no se pueden realizar si el nombre de la ciudad contiene dígitos (0-9), el signo &amp;, puntos (.) o paréntesis ().

Utilice el menú de la izquierda para navegar a una página específica del parche.
