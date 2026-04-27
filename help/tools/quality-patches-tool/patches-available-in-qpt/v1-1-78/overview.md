---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.78'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.78.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: cc3bd15a0c11762812e4e51e4c01bfa64756421a
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.78

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.78.

QPT v1.1.78 incluye los siguientes parches:
1. **ACP2E-4416**: corrige el problema en el cual los puntos de recompensa del cliente no se inicializan cuando se crean en el administrador.
1. **[ACP2E-4419](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4419.md)**: corrige el problema por el cual las tarjetas de regalo no se aplican correctamente en el cierre de compra después de una validación exitosa de reCAPTCHA v2 (&#39;No soy un robot&#39;) en la tienda.
1. **ACP2E-4431**: corrige el problema en el que los productos relacionados que coinciden con las reglas de destino se eliminan durante el proceso de reindexación.
1. **ACP2E-4448**: corrige el problema en el que los cambios de configuración realizados durante las interrupciones de Redis no se reflejan después de que Redis se recupere, lo que provoca que los valores antiguos persistan.
1. **ACP2E-4452**: corrige el problema por el que los precios de los productos en la página Pedido rápido incluyen impuestos independientemente de la configuración de presentación de impuestos.
1. **ACP2E-4456**: corrige un problema en el cual cancelar un pedido usando una mutación de GraphQL no pasa un pedido pagado completamente con tarjetas de regalo al estado Cerrado.
1. **ACP2E-4507**: corrige el problema en el que la configuración de Opciones de contraseña no se aplica a las solicitudes de restablecimiento de contraseña de cliente realizadas a través de mutaciones de GraphQL.
1. **ACP2E-4513**: corrige el problema en el cual las imágenes CAPTCHA caducadas no se eliminan del sistema.
1. **[ACP2E-4522](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4522.md)**: corrige el problema en el que se produce un error intermitente de clave duplicada en la tabla quote_coupons cuando se ejecutan varias solicitudes de guardado de combinación de carro de compras o presupuesto al mismo tiempo.
1. **ACP2E-4528**: corrige el problema de validación de ciudad en las direcciones de los clientes, que ahora permite el carácter de barra diagonal (/) y rechaza los caracteres no válidos como !, &quot;, # y ?.
1. **ACP2E-4535**: corrige un problema por el que al enviar el formulario de contraseña olvidada se destruye o regenera la sesión (cambios PHPSESSID) y se borra el carro de invitados.
1. **ACP2E-4540**: corrige el problema en el que la biblioteca Fotorama no se cargaba correctamente, lo que provocaba que solo fuera visible la primera imagen adjunta.
1. **ACP2E-4555**: soluciona el problema en el que los números de teléfono modernos contienen &quot;.&quot; o &quot;/&quot; no se han validado correctamente.
1. **ACP2E-4565**: corrige el problema en el que la consulta Company GraphQL devuelve &quot;El cliente actual no está autorizado&quot; cuando se utiliza el encabezado X-Adobe-Company.
1. **ACP2E-4591**: corrige el problema en el que los segmentos de clientes basados en el recuento de pedidos, como &quot;Compradores nuevos&quot;, no se actualizaban cuando los pedidos se realizaban mediante la API de REST.
1. **ACP2E-4609**: corrige el problema por el que la página Mis comillas no muestra comillas cuando algunas comillas contienen productos eliminados.
1. **ACP2E-4613**: corrige el problema en el que las estructuras de directorios de medios grandes causaban respuestas gettree lentas, lo que provocaba tiempos de carga de árboles de directorios de Media Gallery extendidos.
1. **ACP2E-4628**: corrige el problema en el que la importación de clientes con direcciones de correo electrónico en mayúsculas da como resultado un error de clave de matriz no definida, cuando el uso compartido de cuentas está establecido en Global.
1. **ACP2E-4665**: corrige el problema en el que los productos secundarios de productos configurables que contienen vídeos en las galerías de productos no aparecen en la lista cuando se solicitan mediante la API de REST.
1. **ACP2E-4732**: corrige un problema en el cual se detuvo la indexación parcial para clientes con un gran número de actualizaciones cuando la columna version_id en la tabla changelog alcanzó su valor máximo.
1. **ACP2E-4763**: Corrige el problema por el que la consulta GraphQL customerOrders devuelve valores inflados original_price_included_tax y original_row_total_include_tax cuando los precios de catálogo se establecen en Incluyendo impuesto, debido a que el impuesto se aplica dos veces.
1. **ACSD-60989**: corrige el problema en el que la modificación de una columna con una clave externa a través de un esquema declarativo provoca errores en MariaDB.

Utilice el menú de la izquierda para navegar a una página específica del parche.
