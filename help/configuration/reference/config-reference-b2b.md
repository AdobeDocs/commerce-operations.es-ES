---
title: Referencia de rutas de configuración de la extensión B2B
description: Obtenga información acerca de las rutas y los valores de configuración de la extensión B2B para Adobe Commerce. Descubra las opciones de configuración específicas de empresa, pago, presupuesto y B2B.
feature: Configuration, B2B, Companies, Payments, Quotes
exl-id: 3414dea1-17c9-4462-8b8a-51a6045b0bc9
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 0%

---

# Referencia de rutas de configuración de la extensión B2B

_Esto está disponible para instancias con B2B para Adobe Commerce instalado._

En este tema se enumeran las rutas de configuración para la extensión B2B de Commerce Enterprise. El comando [`magento app:config:dump` &#x200B;](../cli/export-configuration.md) escribe estos valores en el archivo de configuración compartida, `app/etc/config.php`, que debe estar en el control de código fuente.

>[!INFO]
>
>Esta referencia enumera _solamente_ rutas de configuración únicas de B2B para Adobe Commerce. Esta extensión incluye todas las rutas de configuración para Adobe Commerce.

Para ver esas rutas de configuración, consulte:

- [Rutas de configuración de pago](config-reference-payment.md)
- [Referencia de rutas de configuración confidenciales y específicas del sistema](config-reference-sens.md)

Para anular opcionalmente las opciones de configuración o establecer opciones confidenciales, vea [Usar variables de entorno para anular las opciones de configuración](override-config-settings.md#environment-variables).

## Categoría general

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **[!UICONTROL Stores]** > Configuración > **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### Rutas de funciones B2B

Estos valores de configuración están disponibles en el Administrador en **[!UICONTROL Stores]** > Configuración > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| Nombre | Ruta de configuración | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Habilitar compañía | `btob/website_configuration/company_active` | | | |
| Habilitar catálogo compartido | `btob/website_configuration/sharedcatalog_active` | | | |
| Activar oferta B2B | `btob/website_configuration/negotiablequote_active` | | | |
| Activar orden rápido | `btob/website_configuration/quickorder_active` | | | |
| Activar lista de solicitudes | `btob/website_configuration/requisition_list_active` | | | |
| Métodos de pago aplicables | `btob/default_b2b_payment_methods/applicable_payment_methods` | | | |
| Métodos de pago | `btob/default_b2b_payment_methods/available_payment_methods` | | | |

{style="table-layout:auto"}

## Categoría de clientes

En esta sección se enumeran los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **[!UICONTROL Stores]** > Configuración > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### Rutas de configuración de empresa

Estos valores de configuración están disponibles en el Administrador en **[!UICONTROL Stores]** > Configuración > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| Nombre | Ruta de configuración | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|
| Permitir el registro de empresa desde la tienda | `company/general/allow_company_registration` | | | |
| Destinatario de correo electrónico de registro de empresa | `company/email/company_registration` | | | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico de registro de empresa a | `company/email/company_registration_copy` | | | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Método Enviar copia de correo electrónico | `company/email/company_copy_method` | | | |
| Correo electrónico predeterminado de registro de empresa | `company/email/company_notify_admin_template` | | | |
| Correos electrónicos relacionados con el cliente | `company/email/heading_customer` | | | |
| Correo electrónico asignado del representante de ventas predeterminado | `company/email/customer_sales_representative_template` | | | |
| Asignar compañía predeterminada al correo electrónico del cliente | `company/email/customer_company_customer_assign_template` | | | |
| Correo electrónico de administrador de empresa asignado predeterminado | `company/email/customer_assign_super_user_template` | | | |
| Correo electrónico inactivo de administrador de empresa predeterminado | `company/email/customer_inactivate_super_user_template` | | | |
| Se Ha Cambiado El Administrador Predeterminado De La Empresa Al Correo Electrónico Del Miembro | `company/email/customer_remove_super_user_template` | | | |
| Correo electrónico activo de estado de cliente predeterminado | `company/email/customer_account_activated_template` | | | |
| Correo electrónico inactivo de estado de cliente predeterminado | `company/email/customer_account_locked_template` | | | |
| Cambio de estado de compañía | `company/email/heading_company_status` | | | |
| Estado de la compañía Cambiar destinatario de correo electrónico | `company/email/company_status_change` | | | |
| Enviar copia de cambio de estado de compañía a | `company/email/company_status_change_copy` | | | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Método Enviar copia de correo electrónico | `company/email/company_status_copy_method` | | | |
| Se Cambió El Estado Predeterminado De La Empresa A Activo 1 Correo Electrónico | `company/email/company_status_pending_approval_to_active_template` | | | |
| Se Cambió El Estado Predeterminado De La Empresa A Correo Electrónico Activo 2 | `company/email/company_status_rejected_blocked_to_active_template` | | | |
| Cambio De Estado Predeterminado De La Empresa A Correo Electrónico Rechazado | `company/email/company_status_rejected_template` | | | |
| Cambio De Estado Predeterminado De La Empresa A Correo Electrónico Bloqueado | `company/email/company_status_blocked_template` | | | |
| Se Cambió El Estado Predeterminado De La Compañía A Correo Electrónico De Aprobación Pendiente | `company/email/company_status_pending_approval_template` | | | |
| Crédito de empresa | `company/email/heading_company_credit` | | | |
| Remitente de correo electrónico de cambio de crédito de compañía | `company/email/company_credit_change` |  | | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar correo electrónico de cambio de crédito de empresa a | `company/email/company_credit_change_copy` | | | |
| Método Enviar copia de correo electrónico | `company/email/company_credit_copy_method` | | | |
| Plantilla de correo electrónico asignada | `company/email/credit_allocated_email_template` | | | |
| Plantilla de correo electrónico actualizada | `company/email/credit_updated_email_template` | | | |
| Plantilla de correo electrónico reembolsado | `company/email/credit_reimbursed_email_template` | | | |
| Plantilla de correo electrónico de reembolso | `company/email/credit_refunded_email_template` | | | |
| Plantilla de correo electrónico revertida | `company/email/credit_reverted_email_template` | | | |

{style="table-layout:auto"}

### Rutas de listas de solicitudes

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Clientes** > **Listas de solicitudes**.

| Nombre | Ruta de configuración | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Número de listas de solicitudes | `requisitionlist/general/number_requisition_lists` | | | |

{style="table-layout:auto"}

## Categoría de ventas

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones del Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas**.

### Rutas de correos electrónicos de ventas

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Correos electrónicos de ventas**.

| Nombre | Ruta de configuración | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Habilitado | `sales_email/quote/enabled` | | | |
| Plantilla de oferta actualizada (para el comprador) | `sales_email/quote/updated_buyer_template` | | | |
| Plantilla de oferta rechazada (para el comprador) | `sales_email/quote/declined_buyer_template` | | | |
| Plantilla de nuevo presupuesto (para vendedor) | `sales_email/quote/new_seller_template` | | | |
| Plantilla de presupuesto actualizada (para vendedor) | `sales_email/quote/updated_seller_template` | | | |
| Caducidad del presupuesto (en 48 horas) | `sales_email/quote/expire_two_days_template` | | | |
| Caducidad del presupuesto (en 24 horas) | `sales_email/quote/expire_one_day_template` | | | |
| Restablecimiento de fecha de vencimiento | `sales_email/quote/expire_reset_template` | | | |
| Enviar copia de presupuesto por correo electrónico a | `sales_email/quote/copy_to` | | | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Método Enviar copia de correo electrónico de presupuesto | `sales_email/quote/copy_method` | | | |

{style="table-layout:auto"}

### Rutas de comillas

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Ofertas**.

| Nombre | Ruta de configuración | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Cantidad mínima | `quote/general/minimum_amount` | | | |
| Mensaje de cantidad mínima | `quote/general/minimum_amount_message` | | | |
| Período de caducidad predeterminado | `quote/general/default_expiration_period` | | | |
| Formatos de archivo para carga | `quote/attached_files/file_formats` | | | |
| Tamaño máximo de archivo | `quote/attached_files/maximum_file_size` | | | |
| Cantidad mínima | `quote/general/minimum_amount` | | | |
| Mensaje de cantidad mínima | `quote/general/minimum_amount_message` | | | |
| Período de caducidad predeterminado | `quote/general/default_expiration_period` | | | |
| Formatos de archivo para carga | `quote/attached_files/file_formats` | | | |
| Tamaño máximo de archivo | `quote/attached_files/maximum_file_size` | | | |

{style="table-layout:auto"}

## Rutas de métodos de pago

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Métodos de pago**.

>[!INFO]
>
>Las rutas disponibles están determinadas por su elección de país comerciante.

| Nombre | Ruta de configuración | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Habilitado | `payment/au/companycredit/active` | | | |
| Título | `payment/au/companycredit/title` | | | |
| Estado de nuevo pedido | `payment/au/companycredit/order_status` | | | |
| Pago de países aplicables | `payment/au/companycredit/allowspecific` | | | |
| Pago desde países específicos | `payment/au/companycredit/specificcountry` | | | |
| Total de pedido mínimo | `payment/au/companycredit/min_order_total` | | | |
| Total de pedido máximo | `payment/au/companycredit/max_order_total` | | | |
| Orden de clasificación | `payment/au/companycredit/sort_order` | | | |
| Habilitado | `payment/es/companycredit/active` | | | |
| Título | `payment/es/companycredit/title` | | | |
| Estado de nuevo pedido | `payment/es/companycredit/order_status` | | | |
| Pago de países aplicables | `payment/es/companycredit/allowspecific` | | | |
| Pago desde países específicos | `payment/es/companycredit/specificcountry` | | | |
| Total de pedido mínimo | `payment/es/companycredit/min_order_total` | | | |
| Total de pedido máximo | `payment/es/companycredit/max_order_total` | | | |
| Orden de clasificación | `payment/es/companycredit/sort_order` | | | |
| Habilitado | `payment/companycredit/active` | | | |
| Título | `payment/companycredit/title` | | | |
| Estado de nuevo pedido | `payment/companycredit/order_status` | | | |
| Pago de países aplicables | `payment/companycredit/allowspecific` | | | |
| Pago desde países específicos | `payment/companycredit/specificcountry` | | | |
| Total de pedido mínimo | `payment/companycredit/min_order_total` | | | |
| Total de pedido máximo | `payment/companycredit/max_order_total` | | | |
| Orden de clasificación | `payment/companycredit/sort_order` | | | |
| Habilitado | `payment/nz/companycredit/active` | | | |
| Título | `payment/nz/companycredit/title` | | | |
| Estado de nuevo pedido | `payment/nz/companycredit/order_status` | | | |
| Pago de países aplicables | `payment/nz/companycredit/allowspecific` | | | |
| Pago desde países específicos | `payment/nz/companycredit/specificcountry` | | | |
| Total de pedido mínimo | `payment/nz/companycredit/min_order_total` | | | |
| Total de pedido máximo | `payment/nz/companycredit/max_order_total` | | | |
| Orden de clasificación | `payment/nz/companycredit/sort_order` | | | |
| Habilitado | `payment/us/companycredit/active` | | | |
| Título | `payment/us/companycredit/title` | | | |
| Estado de nuevo pedido | `payment/us/companycredit/order_status` | | | |
| Pago de países aplicables | `payment/us/companycredit/allowspecific` | | | |
| Pago desde países específicos | `payment/us/companycredit/specificcountry` | | | |
| Total de pedido mínimo | `payment/us/companycredit/min_order_total` | | | |
| Total de pedido máximo | `payment/us/companycredit/max_order_total` | | | |
| Orden de clasificación | `payment/us/companycredit/sort_order` | | | |
| Habilitado | `payment/gb/companycredit/active` | | | |
| Título | `payment/gb/companycredit/title` | | | |
| Estado de nuevo pedido | `payment/gb/companycredit/order_status` | | | |
| Pago de países aplicables | `payment/gb/companycredit/allowspecific` | | | |
| Pago desde países específicos | `payment/gb/companycredit/specificcountry` | | | |
| Total de pedido mínimo | `payment/gb/companycredit/min_order_total` | | | |
| Total de pedido máximo | `payment/gb/companycredit/max_order_total` | | | |
| Orden de clasificación | `payment/gb/companycredit/sort_order` | | | |
| Habilitado | `payment/de/companycredit/active` | | | |
| Título | `payment/de/companycredit/title` | | | |
| Estado de nuevo pedido | `payment/de/companycredit/order_status` | | | |
| Pago de países aplicables | `payment/de/companycredit/allowspecific` | | | |
| Pago desde países específicos | `payment/de/companycredit/specificcountry` | | | |
| Total de pedido mínimo | `payment/de/companycredit/min_order_total` | | | |
| Total de pedido máximo | `payment/de/companycredit/max_order_total` | | | |
| Orden de clasificación | `payment/de/companycredit/sort_order` | | | |
| Habilitado | `payment/other/companycredit/active` | | | |
| Título | `payment/other/companycredit/title` | | | |
| Estado de nuevo pedido | `payment/other/companycredit/order_status` | | | |
| Pago de países aplicables | `payment/other/companycredit/allowspecific` | | | |
| Pago desde países específicos | `payment/other/companycredit/specificcountry` | | | |
| Total de pedido mínimo | `payment/other/companycredit/min_order_total` | | | |
| Total de pedido máximo | `payment/other/companycredit/max_order_total` | | | |
| Orden de clasificación | `payment/other/companycredit/sort_order` | | | |
| Habilitado | `payment/ca/companycredit/active` | | | |
| Título | `payment/ca/companycredit/title` | | | |
| Estado de nuevo pedido | `payment/ca/companycredit/order_status` | | | |
| Pago de países aplicables | `payment/ca/companycredit/allowspecific` | | | |
| Pago desde países específicos | `payment/ca/companycredit/specificcountry` | | | |
| Total de pedido mínimo | `payment/ca/companycredit/min_order_total` | | | |
| Total de pedido máximo | `payment/ca/companycredit/max_order_total` | | | |
| Orden de clasificación | `payment/ca/companycredit/sort_order` | | | |
| Habilitado | `payment/hk/companycredit/active` | | | |
| Título | `payment/hk/companycredit/title` | | | |
| Estado de nuevo pedido | `payment/hk/companycredit/order_status` | | | |
| Pago de países aplicables | `payment/hk/companycredit/allowspecific` | | | |
| Pago desde países específicos | `payment/hk/companycredit/specificcountry` | | | |
| Total de pedido mínimo | `payment/hk/companycredit/min_order_total` | | | |
| Total de pedido máximo | `payment/hk/companycredit/max_order_total` | | | |
| Orden de clasificación | `payment/hk/companycredit/sort_order` | | | |
| Habilitado | `payment/jp/companycredit/active` | | | |
| Título | `payment/jp/companycredit/title` | | | |
| Estado de nuevo pedido | `payment/jp/companycredit/order_status` | | | |
| Pago de países aplicables | `payment/jp/companycredit/allowspecific` | | | |
| Pago desde países específicos | `payment/jp/companycredit/specificcountry` | | | |
| Total de pedido mínimo | `payment/jp/companycredit/min_order_total` | | | |
| Total de pedido máximo | `payment/jp/companycredit/max_order_total` | | | |
| Orden de clasificación | `payment/jp/companycredit/sort_order` | | | |
| Habilitado | `payment/fr/companycredit/active` | | | |
| Título | `payment/fr/companycredit/title` | | | |
| Estado de nuevo pedido | `payment/fr/companycredit/order_status` | | | |
| Pago de países aplicables | `payment/fr/companycredit/allowspecific` | | | |
| Pago desde países específicos | `payment/fr/companycredit/specificcountry` | | | |
| Total de pedido mínimo | `payment/fr/companycredit/min_order_total` | | | |
| Total de pedido máximo | `payment/fr/companycredit/max_order_total` | | | |
| Orden de clasificación | `payment/fr/companycredit/sort_order` | | | |
| Habilitado | `payment/it/companycredit/active` | | | |
| Título | `payment/it/companycredit/title` | | | |
| Estado de nuevo pedido | `payment/it/companycredit/order_status` | | | |
| Pago de países aplicables | `payment/it/companycredit/allowspecific` | | | |
| Pago desde países específicos | `payment/it/companycredit/specificcountry` | | | |
| Total de pedido mínimo | `payment/it/companycredit/min_order_total` | | | |
| Total de pedido máximo | `payment/it/companycredit/max_order_total` | | | |
| Orden de clasificación | `payment/it/companycredit/sort_order` | | | |

{style="table-layout:auto"}
