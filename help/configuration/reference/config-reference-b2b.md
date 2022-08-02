---
title: Referencia de rutas de configuración de la extensión B2B
description: Consulte una lista de valores de configuración relacionados con B2B.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---


# Referencia de rutas de configuración de la extensión B2B

_Esto está disponible para instancias con B2B para Adobe Commerce instalado._

Este tema enumera las rutas de configuración para la extensión B2B de Commerce Enterprise. La variable [`magento app:config:dump` command](../cli/export-configuration.md) escribe estos valores en el archivo de configuración compartido, `app/etc/config.php`, que debería estar en el control de código fuente.

>[!INFO]
>
>Esta lista de referencia _only_ rutas de configuración exclusivas de B2B para Adobe Commerce. Esta extensión incluye todas las rutas de configuración para Adobe Commerce.

Para esas rutas de configuración, consulte:

- [Rutas de configuración de pago](config-reference-payment.md)
- [Referencia de rutas de configuración confidenciales y específicas del sistema](config-reference-sens.md)

Para anular, opcionalmente, cualquier configuración o definir ajustes confidenciales, consulte [Usar variables de entorno para anular los ajustes de configuración](override-config-settings.md#environment-variables).

## Categoría general

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **[!UICONTROL Stores]** > Configuración > **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### Rutas de características B2B

Estos valores de configuración están disponibles en Administración en **[!UICONTROL Stores]** > Configuración > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| Nombre | Ruta de configuración | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Habilitar empresa | `btob/website_configuration/company_active` |  |  |  |
| Habilitar catálogo compartido | `btob/website_configuration/sharedcatalog_active` |  |  |  |
| Habilitar cotización B2B | `btob/website_configuration/negotiablequote_active` |  |  |  |
| Habilitar orden rápido | `btob/website_configuration/quickorder_active` |  |  |  |
| Habilitar lista de solicitudes | `btob/website_configuration/requisition_list_active` |  |  |  |
| Métodos de pago aplicables | `btob/default_b2b_payment_methods/applicable_payment_methods` |  |  |  |
| Métodos de pago | `btob/default_b2b_payment_methods/available_payment_methods` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## Categoría de clientes

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **[!UICONTROL Stores]** > Configuración > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### Rutas de configuración de la empresa

Estos valores de configuración están disponibles en Administración en **[!UICONTROL Stores]** > Configuración > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| Nombre | Ruta de configuración | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|
| Permitir registro de empresa desde la tienda | `company/general/allow_company_registration` |  |  |  |
| Destinatario de correo electrónico de registro de la empresa | `company/email/company_registration` |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico de registro de empresa a | `company/email/company_registration_copy` |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar método de copia de correo electrónico | `company/email/company_copy_method` |  |  |  |
| Correo electrónico de registro de empresa predeterminado | `company/email/company_notify_admin_template` |  |  |  |
| Correos electrónicos relacionados con el cliente | `company/email/heading_customer` |  |  |  |
| Correo electrónico asignado de representante de ventas predeterminado | `company/email/customer_sales_representative_template` |  |  |  |
| Asignación predeterminada de la empresa al correo electrónico del cliente | `company/email/customer_company_customer_assign_template` |  |  |  |
| Asignación predeterminada de correo electrónico de administrador de la empresa | `company/email/customer_assign_super_user_template` |  |  |  |
| Correo electrónico inactivo del administrador de la empresa predeterminado | `company/email/customer_inactivate_super_user_template` |  |  |  |
| El Administrador Predeterminado De La Empresa Cambió A Correo Electrónico De Miembro | `company/email/customer_remove_super_user_template` |  |  |  |
| Correo electrónico activo del estado del cliente predeterminado | `company/email/customer_account_activated_template` |  |  |  |
| Correo electrónico inactivo del estado de cliente predeterminado | `company/email/customer_account_locked_template` |  |  |  |
| Cambio de estado de la empresa | `company/email/heading_company_status` |  |  |  |
| Estado de la empresa Cambiar destinatario de correo electrónico | `company/email/company_status_change` |  |  |  |
| Enviar el estado de la empresa a Cambiar copia de correo electrónico a | `company/email/company_status_change_copy` |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar método de copia de correo electrónico | `company/email/company_status_copy_method` |  |  |  |
| Cambio De Estado De Empresa Predeterminado A Correo Electrónico Activo 1 | `company/email/company_status_pending_approval_to_active_template` |  |  |  |
| Cambio De Estado De La Empresa Predeterminado A Correo Electrónico Activo 2 | `company/email/company_status_rejected_blocked_to_active_template` |  |  |  |
| Cambio De Estado De La Empresa Predeterminado En Correo Electrónico Rechazado | `company/email/company_status_rejected_template` |  |  |  |
| Cambio De Estado De Empresa Predeterminado En Correo Electrónico Bloqueado | `company/email/company_status_blocked_template` |  |  |  |
| Cambio de estado de compañía predeterminado a correo electrónico de aprobación pendiente | `company/email/company_status_pending_approval_template` |  |  |  |
| Crédito de la empresa | `company/email/heading_company_credit` |  |  |  |
| Remitente de correo electrónico de cambio de crédito de la empresa | `company/email/company_credit_change` |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico de cambio de crédito de la empresa a | `company/email/company_credit_change_copy` |  |  |  |
| Enviar método de copia de correo electrónico | `company/email/company_credit_copy_method` |  |  |  |
| Plantilla de correo electrónico asignada | `company/email/credit_allocated_email_template` |  |  |  |
| Plantilla de correo electrónico actualizada | `company/email/credit_updated_email_template` |  |  |  |
| Plantilla de correo electrónico reembolsada | `company/email/credit_reimbursed_email_template` |  |  |  |
| Plantilla de correo electrónico reembolsada | `company/email/credit_refunded_email_template` |  |  |  |
| Plantilla de correo electrónico revertida | `company/email/credit_reverted_email_template` |  |  |  |

{style=&quot;table-layout:auto&quot;}

### Rutas de listas de solicitudes

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Clientes** > **Listas de solicitudes**.

| Nombre | Ruta de configuración | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Número de listas de solicitudes | `requisitionlist/general/number_requisition_lists` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## Categoría de ventas

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **Almacenes** > Configuración > **Configuración** > **Ventas**.

### Rutas de correo electrónico de ventas

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Correos electrónicos de ventas**.

| Nombre | Ruta de configuración | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Habilitado | `sales_email/quote/enabled` |  |  |  |
| Plantilla de cotización actualizada (al comprador) | `sales_email/quote/updated_buyer_template` |  |  |  |
| Plantilla de cotización rechazada (al comprador) | `sales_email/quote/declined_buyer_template` |  |  |  |
| Nueva plantilla de cotización (al vendedor) | `sales_email/quote/new_seller_template` |  |  |  |
| Plantilla de cotización actualizada (al vendedor) | `sales_email/quote/updated_seller_template` |  |  |  |
| Caducidad de cotización (en 48 horas) | `sales_email/quote/expire_two_days_template` |  |  |  |
| Caducidad de cotización (en 24 horas) | `sales_email/quote/expire_one_day_template` |  |  |  |
| Restablecimiento de fecha de caducidad | `sales_email/quote/expire_reset_template` |  |  |  |
| Enviar copia de correo electrónico de cotización a | `sales_email/quote/copy_to` |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar método de copia de correo electrónico de cotización | `sales_email/quote/copy_method` |  |  |  |

{style=&quot;table-layout:auto&quot;}

### Rutas de cotización

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Comillas**.

| Nombre | Ruta de configuración | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Importe mínimo | `quote/general/minimum_amount` |  |  |  |
| Mensaje de importe mínimo | `quote/general/minimum_amount_message` |  |  |  |
| Período de caducidad predeterminado | `quote/general/default_expiration_period` |  |  |  |
| Formatos de archivo para la carga | `quote/attached_files/file_formats` |  |  |  |
| Tamaño máximo del archivo | `quote/attached_files/maximum_file_size` |  |  |  |
| Importe mínimo | `quote/general/minimum_amount` |  |  |  |
| Mensaje de importe mínimo | `quote/general/minimum_amount_message` |  |  |  |
| Período de caducidad predeterminado | `quote/general/default_expiration_period` |  |  |  |
| Formatos de archivo para la carga | `quote/attached_files/file_formats` |  |  |  |
| Tamaño máximo del archivo | `quote/attached_files/maximum_file_size` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## Rutas de método de pago

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Métodos de pago**.

>[!INFO]
>
>Las rutas disponibles están determinadas por su elección de país Mercante.

| Nombre | Ruta de configuración | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Habilitado | `payment/au/companycredit/active` |  |  |  |
| Título | `payment/au/companycredit/title` |  |  |  |
| Nuevo estado de pedido | `payment/au/companycredit/order_status` |  |  |  |
| Pago de los países aplicables | `payment/au/companycredit/allowspecific` |  |  |  |
| Pago de países específicos | `payment/au/companycredit/specificcountry` |  |  |  |
| Total de pedido mínimo | `payment/au/companycredit/min_order_total` |  |  |  |
| Total de pedido máximo | `payment/au/companycredit/max_order_total` |  |  |  |
| Orden | `payment/au/companycredit/sort_order` |  |  |  |
| Habilitado | `payment/es/companycredit/active` |  |  |  |
| Título | `payment/es/companycredit/title` |  |  |  |
| Nuevo estado de pedido | `payment/es/companycredit/order_status` |  |  |  |
| Pago de los países aplicables | `payment/es/companycredit/allowspecific` |  |  |  |
| Pago de países específicos | `payment/es/companycredit/specificcountry` |  |  |  |
| Total de pedido mínimo | `payment/es/companycredit/min_order_total` |  |  |  |
| Total de pedido máximo | `payment/es/companycredit/max_order_total` |  |  |  |
| Orden | `payment/es/companycredit/sort_order` |  |  |  |
| Habilitado | `payment/companycredit/active` |  |  |  |
| Título | `payment/companycredit/title` |  |  |  |
| Nuevo estado de pedido | `payment/companycredit/order_status` |  |  |  |
| Pago de los países aplicables | `payment/companycredit/allowspecific` |  |  |  |
| Pago de países específicos | `payment/companycredit/specificcountry` |  |  |  |
| Total de pedido mínimo | `payment/companycredit/min_order_total` |  |  |  |
| Total de pedido máximo | `payment/companycredit/max_order_total` |  |  |  |
| Orden | `payment/companycredit/sort_order` |  |  |  |
| Habilitado | `payment/nz/companycredit/active` |  |  |  |
| Título | `payment/nz/companycredit/title` |  |  |  |
| Nuevo estado de pedido | `payment/nz/companycredit/order_status` |  |  |  |
| Pago de los países aplicables | `payment/nz/companycredit/allowspecific` |  |  |  |
| Pago de países específicos | `payment/nz/companycredit/specificcountry` |  |  |  |
| Total de pedido mínimo | `payment/nz/companycredit/min_order_total` |  |  |  |
| Total de pedido máximo | `payment/nz/companycredit/max_order_total` |  |  |  |
| Orden | `payment/nz/companycredit/sort_order` |  |  |  |
| Habilitado | `payment/us/companycredit/active` |  |  |  |
| Título | `payment/us/companycredit/title` |  |  |  |
| Nuevo estado de pedido | `payment/us/companycredit/order_status` |  |  |  |
| Pago de los países aplicables | `payment/us/companycredit/allowspecific` |  |  |  |
| Pago de países específicos | `payment/us/companycredit/specificcountry` |  |  |  |
| Total de pedido mínimo | `payment/us/companycredit/min_order_total` |  |  |  |
| Total de pedido máximo | `payment/us/companycredit/max_order_total` |  |  |  |
| Orden | `payment/us/companycredit/sort_order` |  |  |  |
| Habilitado | `payment/gb/companycredit/active` |  |  |  |
| Título | `payment/gb/companycredit/title` |  |  |  |
| Nuevo estado de pedido | `payment/gb/companycredit/order_status` |  |  |  |
| Pago de los países aplicables | `payment/gb/companycredit/allowspecific` |  |  |  |
| Pago de países específicos | `payment/gb/companycredit/specificcountry` |  |  |  |
| Total de pedido mínimo | `payment/gb/companycredit/min_order_total` |  |  |  |
| Total de pedido máximo | `payment/gb/companycredit/max_order_total` |  |  |  |
| Orden | `payment/gb/companycredit/sort_order` |  |  |  |
| Habilitado | `payment/de/companycredit/active` |  |  |  |
| Título | `payment/de/companycredit/title` |  |  |  |
| Nuevo estado de pedido | `payment/de/companycredit/order_status` |  |  |  |
| Pago de los países aplicables | `payment/de/companycredit/allowspecific` |  |  |  |
| Pago de países específicos | `payment/de/companycredit/specificcountry` |  |  |  |
| Total de pedido mínimo | `payment/de/companycredit/min_order_total` |  |  |  |
| Total de pedido máximo | `payment/de/companycredit/max_order_total` |  |  |  |
| Orden | `payment/de/companycredit/sort_order` |  |  |  |
| Habilitado | `payment/other/companycredit/active` |  |  |  |
| Título | `payment/other/companycredit/title` |  |  |  |
| Nuevo estado de pedido | `payment/other/companycredit/order_status` |  |  |  |
| Pago de los países aplicables | `payment/other/companycredit/allowspecific` |  |  |  |
| Pago de países específicos | `payment/other/companycredit/specificcountry` |  |  |  |
| Total de pedido mínimo | `payment/other/companycredit/min_order_total` |  |  |  |
| Total de pedido máximo | `payment/other/companycredit/max_order_total` |  |  |  |
| Orden | `payment/other/companycredit/sort_order` |  |  |  |
| Habilitado | `payment/ca/companycredit/active` |  |  |  |
| Título | `payment/ca/companycredit/title` |  |  |  |
| Nuevo estado de pedido | `payment/ca/companycredit/order_status` |  |  |  |
| Pago de los países aplicables | `payment/ca/companycredit/allowspecific` |  |  |  |
| Pago de países específicos | `payment/ca/companycredit/specificcountry` |  |  |  |
| Total de pedido mínimo | `payment/ca/companycredit/min_order_total` |  |  |  |
| Total de pedido máximo | `payment/ca/companycredit/max_order_total` |  |  |  |
| Orden | `payment/ca/companycredit/sort_order` |  |  |  |
| Habilitado | `payment/hk/companycredit/active` |  |  |  |
| Título | `payment/hk/companycredit/title` |  |  |  |
| Nuevo estado de pedido | `payment/hk/companycredit/order_status` |  |  |  |
| Pago de los países aplicables | `payment/hk/companycredit/allowspecific` |  |  |  |
| Pago de países específicos | `payment/hk/companycredit/specificcountry` |  |  |  |
| Total de pedido mínimo | `payment/hk/companycredit/min_order_total` |  |  |  |
| Total de pedido máximo | `payment/hk/companycredit/max_order_total` |  |  |  |
| Orden | `payment/hk/companycredit/sort_order` |  |  |  |
| Habilitado | `payment/jp/companycredit/active` |  |  |  |
| Título | `payment/jp/companycredit/title` |  |  |  |
| Nuevo estado de pedido | `payment/jp/companycredit/order_status` |  |  |  |
| Pago de los países aplicables | `payment/jp/companycredit/allowspecific` |  |  |  |
| Pago de países específicos | `payment/jp/companycredit/specificcountry` |  |  |  |
| Total de pedido mínimo | `payment/jp/companycredit/min_order_total` |  |  |  |
| Total de pedido máximo | `payment/jp/companycredit/max_order_total` |  |  |  |
| Orden | `payment/jp/companycredit/sort_order` |  |  |  |
| Habilitado | `payment/fr/companycredit/active` |  |  |  |
| Título | `payment/fr/companycredit/title` |  |  |  |
| Nuevo estado de pedido | `payment/fr/companycredit/order_status` |  |  |  |
| Pago de los países aplicables | `payment/fr/companycredit/allowspecific` |  |  |  |
| Pago de países específicos | `payment/fr/companycredit/specificcountry` |  |  |  |
| Total de pedido mínimo | `payment/fr/companycredit/min_order_total` |  |  |  |
| Total de pedido máximo | `payment/fr/companycredit/max_order_total` |  |  |  |
| Orden | `payment/fr/companycredit/sort_order` |  |  |  |
| Habilitado | `payment/it/companycredit/active` |  |  |  |
| Título | `payment/it/companycredit/title` |  |  |  |
| Nuevo estado de pedido | `payment/it/companycredit/order_status` |  |  |  |
| Pago de los países aplicables | `payment/it/companycredit/allowspecific` |  |  |  |
| Pago de países específicos | `payment/it/companycredit/specificcountry` |  |  |  |
| Total de pedido mínimo | `payment/it/companycredit/min_order_total` |  |  |  |
| Total de pedido máximo | `payment/it/companycredit/max_order_total` |  |  |  |
| Orden | `payment/it/companycredit/sort_order` |  |  |  |

{style=&quot;table-layout:auto&quot;}
