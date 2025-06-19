---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.62'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.62.
feature: Tools and External Services
role: Admin, Developer
exl-id: be8ffedc-b589-4a30-ba9a-eed705696825
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.62

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.62.

QPT v1.1.62 incluye los siguientes parches:

1. **ACSD-63406**: corrige el problema en el cual las comillas persistentes caducadas no son borradas por ningún trabajo cron cuando se ejecuta el trabajo cron `persistent_clear_expired`.
1. **ACSD-63520**: corrige el problema en el cual las imágenes agregadas a través de **[!UICONTROL Configurations]** en el panel de administración no respetan el límite de tamaño máximo de carga.
1. **ACSD-64523**: corrige el problema en el cual se podían crear nuevos productos sin nombre a través del proceso de importación (a través de la administración o la API), lo que provocaba que la interfaz de administración se dañara y produjera productos no válidos.
1. **ACSD-64532**: corrige el problema en el que una variable ENV establecida en *false* se trata como una cadena *false* en lugar de como un valor booleano false.
1. **ACSD-64592**: corrige el problema por el que el vínculo de notificación del correo electrónico para una tarjeta regalo en tiendas no predeterminadas siempre redirigía la notificación de tarjeta regalo al sitio web predeterminado.
1. **ACSD-65164**: corrige el problema donde el mensaje de error *Algunas de las opciones del elemento seleccionado no están disponibles actualmente* se produce al reordenar un producto configurable con una única opción personalizada de casilla de verificación seleccionada.
1. **ACSD-64732**: corrige el problema en el cual los controladores de terceros no se almacenaban correctamente en la caché con segmentos de clientes.

Utilice el menú de la izquierda para navegar a una página específica del parche.
