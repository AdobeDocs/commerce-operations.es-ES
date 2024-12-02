---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.31'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.31.
feature: Tools and External Services
role: Admin
exl-id: d37c7f05-1bf5-495b-9b9e-ac9dd117a3ab
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.31

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.31.

QPT v1.1.31 incluye los siguientes parches:

1. **ACSD-50817**: optimiza el trabajo cron `sales_clean_quotes` para que se ejecute más rápido al agregar un índice compuesto en las columnas `store_id` y `updated_at` de la tabla de comillas.
1. **ACSD-50345**: corrige el problema donde: [!DNL Google reCAPTCHA v2] no se vuelve a cargar después de enviar un pago erróneo, [!DNL Google reCAPTCHA v3 Invisible] no funciona en el cierre de compra y no se puede realizar el pedido, y no se activó el evento [!UICONTROL PlaceOrder].
1. **ACSD-49392**: corrige el problema en el que el estado del pedido cambia a cerrado después de un reembolso parcial de un producto agrupado.
1. **ACSD-51036**: corrige el problema en el que las condiciones de carrera durante las llamadas simultáneas a la API REST resultan en una sobrescritura de la información de estado de envío en la tabla [!UICONTROL Items Ordered].
1. **ACSD-50858**: corrige el problema por el cual un cupón se marca incorrectamente como usado después de un pago con tarjeta erróneo.

Utilice el menú de la izquierda para navegar a una página específica del parche.
