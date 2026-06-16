---
title: Versiones de Beta
description: Obtenga información sobre las versiones beta de Adobe Commerce y cómo participar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/es/docs/commerce/user-guides/product-solutions" tooltip="Se aplica solo a proyectos de Adobe Commerce en la nube (infraestructura PaaS administrada por Adobe) y a proyectos locales."
badgeSaas: label="SaaS" type="Positive" url="https://experienceleague.adobe.com/es/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos de Adobe Commerce as a Cloud Service y Adobe Commerce Optimizer (infraestructura de SaaS administrada por Adobe)."
source-git-commit: bf0f269900468870a1da7b5360548d49e009097c
workflow-type: tm+mt
source-wordcount: '1400'
ht-degree: 0%

---

# Versiones beta de Adobe Commerce

Los programas de Beta para [soluciones de productos de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce/user-guides/product-solutions) son una forma para que los comerciantes obtengan acceso a las características y el código de la versión preliminar, proporcionen comentarios y guíen el futuro de Adobe Commerce. Existen dos tipos de programas beta:

- Beta público: Hay un programa beta público disponible para todos los clientes y socios de Adobe Commerce
- Private Beta: Un programa beta privado puede requerir una aprobación basada en los criterios de calificación para participar

>[!IMPORTANT]
>
>**Descargo de responsabilidad legal**<br/>
>Las >versiones de Beta incluyen funciones de versión preliminar y código que pueden contener defectos y se proporcionan &quot;TAL CUAL&quot; sin garantía de ningún tipo. Adobe tiene la única discreción de si las versiones beta están disponibles de forma general. Adobe no tiene obligación de mantener, corregir, actualizar, cambiar, modificar, ofrecer asistencia (a través de los servicios de soporte de Adobe o de otro modo) o entregar dichas versiones beta en una fecha específica. En caso de que se publique una versión beta, podría estar sujeta a términos y condiciones adicionales, incluidas las tarifas aplicables. Las versiones de Beta están sujetas a cambios sin previo aviso, incluida la interrupción. Se aconseja a los clientes que tengan cuidado y que no confíen en modo alguno en el funcionamiento o el rendimiento ininterrumpidos o sin errores de las versiones beta.  Por lo tanto, cualquier uso de las versiones beta es totalmente bajo el propio riesgo del cliente.

## Ventajas de participar

El acceso anticipado a las funciones que Adobe está desarrollando permite a los clientes y socios proporcionar comentarios, dar forma al desarrollo de productos y prepararse para adoptar nuevas funciones antes de la disponibilidad general.

## Programas actuales de Beta

Consulte las secciones siguientes para obtener una lista de los programas beta activos.

### Coincidencia y clasificación de búsquedas (Private Beta)

Adobe está mejorando la forma en que la detección de productos clasifica los resultados de búsqueda de [!DNL Live Search] en [!DNL Adobe Commerce] y para [!DNL Adobe Commerce Optimizer]. La actualización da prioridad a **coincidencias exactas y cercanas a la frase**, luego coincide donde **todos los términos de consulta aparecen en el mismo atributo en el que se puede buscar** y, finalmente, **coincidencias entre campos** (incluido el comportamiento que admite sugerencias de estilo autocompletado). Ese modelo por capas ayuda a las consultas de alta intención a mostrar primero los productos más relevantes, al tiempo que devuelve alternativas útiles.

El mismo modelo de relevancia interactúa con **pesos de búsqueda**, **clasificación inteligente**, **sinónimos** y **reglas de comercialización** (fijar, impulsar, enterrar). Los escaparates alemanes pueden usar **decompositor** para palabras compuestas, con el mismo enfoque de priorización general.

**Ventajas principales**

- Aumentos más fuertes para las coincidencias de frases exactas y cercanas (incluidas las formas normalizadas como singular y plural).
- Clasificación más alta cuando todas las palabras de consulta aparecen juntas en un campo en el que se puede buscar.
- Expectativas más claras sobre cómo se combinan las ponderaciones, la clasificación inteligente y las reglas manuales en el momento de la consulta.
- Directrices para validar consultas de alto valor y ajustar reglas de ampliación después del cambio.

Obtenga más información acerca de la estrategia de búsqueda y clasificación en [Adobe Commerce Optimizer (SaaS)](https://experienceleague.adobe.com/es/docs/commerce/optimizer/manage-results/search-relevance-matching) y [Live Search (PaaS)](https://experienceleague.adobe.com/es/docs/commerce/live-search/live-search-admin/search-relevance-matching).

Para solicitar una invitación para esta versión beta privada, envía un correo electrónico a [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com). El equipo de Adobe responderá con los siguientes pasos y los requisitos de idoneidad.

### Filtros de precio de recomendación (Beta público) {#recommendation-price-filters-public-beta}

[!BADGE Solo SaaS]{type=Positive url="https://experienceleague.adobe.com/es/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos de Adobe Commerce as a Cloud Service y Adobe Commerce Optimizer (infraestructura de SaaS administrada por Adobe)."}

[!DNL Adobe Commerce Optimizer] agrega **filtros de precio** a las recomendaciones de productos para que pueda incluir o excluir productos recomendados según el precio cuando cree o edite una unidad de recomendación. Los filtros usan el **precio calculado final** de cada producto del **libro de precios activo** de la tienda, incluidos los descuentos y las promociones de ese libro de precios (no solo el precio de lista). Las reglas de precios refinan el conjunto de candidatos; no reclasifican los productos.

Puede definir rangos **static** con valores mínimos y máximos fijos en la moneda base de su tienda, o reglas **dynamic** en páginas de detalles de productos que comparan productos recomendados con el **producto visualizado actualmente**, usando operadores tales como menor o igual que, mayor o igual que, o dentro de un valor o rango de porcentaje del precio de anclaje. Los filtros dinámicos están disponibles para tipos de recomendación relacionados con SKU que se ejecutan en el contexto del producto (por ejemplo, *Visualizó esto, vio aquello* y *Más como esto*).

**Ventajas principales**

- Incluir o excluir candidatos de recomendación por precio usando reglas de inclusión y exclusión en el paso **Filtrar productos**.
- Utilice bandas de precios estáticas para los objetivos de comercialización fijos (por ejemplo, complementos económicos o ventas adicionales premium).
- Utilice reglas de precios dinámicas en la página de detalles del producto para mostrar alternativas dentro de una banda de precios comparable en relación con el producto que se está viendo.
- Alinee el filtrado con el precio que ven los compradores, que es el mismo precio final del libro de precios activo que se utiliza para el filtrado y la visualización.

Para obtener más información, consulte [Filtros de recomendación — Precio](https://experienceleague.adobe.com/es/docs/commerce/optimizer/merchandising/recommendations/filters#price) en la guía del comerciante y [Configuración de recomendaciones de productos](https://experienceleague.adobe.com/developer/commerce/storefront/merchants/content-customizations/product-recommendations/?lang=es) en la guía desplegable de la tienda.

Para compartir tus comentarios mientras usas esta función beta, envía un correo electrónico a [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com).

### Servicio de parches de automatización de la nube (Private Beta)

[!BADGE Solo PaaS]{type=Informative url="https://experienceleague.adobe.com/es/docs/commerce/user-guides/product-solutions" tooltip="Se aplica solo a proyectos de Adobe Commerce en la nube (infraestructura PaaS administrada por Adobe) y a proyectos locales."}

El servicio de parches de automatización de la nube [Cloud](../tools/caps-tool/intro.md) automatiza el proceso de aplicar parches de seguridad aislados a los entornos de [Adobe Commerce en la infraestructura de la nube](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/overview).

En octubre de 2025, la versión beta del servicio de parches de automatización de la nube se agregará al [panel de herramientas de análisis en todo el sitio](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard). Este servicio es compatible con los administradores de proyectos de Commerce con un flujo de trabajo optimizado de parches que incluye:

- Instalación automatizada de parches
- Recuperación de reversión
- Verificación posterior a la implementación.

El servicio garantiza que puede mantener entornos seguros, estables y actualizados con un esfuerzo manual y un riesgo mínimos.

La versión beta incluye las siguientes funciones:

- **Automatizar la instalación de parches**: Simplifique y automatice el proceso de aplicar parches a vulnerabilidades críticas en entornos.
- **Minimizar el riesgo**: Evite las interrupciones del sitio con las funciones de comprobación de estado y reversión posteriores a la implementación.

>[!NOTE]
>
>Dado que el servicio de parches de automatización de la nube aplica automáticamente parches de seguridad aislados, debe tener la función [Colaborador o Administrador de proyecto](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/project/user-access) para poder usarlos.

Para participar en esta versión beta, completa y envía el [Servicio de parches de automatización de la nube - Formulario de suscripción de Beta](https://forms.office.com/r/3Wfxj5nPdB).

### Asistente de inteligencia artificial aplicada a la productividad del comerciante (Beta público)

El asistente de inteligencia artificial aplicada a la productividad del comerciante es una interfaz conversacional integrada en el administrador de Adobe Commerce que ayuda a los comerciantes a completar tareas rutinarias y acceder a perspectivas comerciales bajo demanda mediante lenguaje natural. Permite a los comerciantes gestionar promociones, actualizar la información del catálogo de productos y recuperar datos operativos (como pedidos recientes o promociones activas) directamente dentro de sus flujos de trabajo existentes. El asistente también proporciona orientación en contexto para ayudar a los comerciantes a navegar y utilizar el administrador de forma más eficaz.

**Ventajas principales**

- Automatice tareas comunes de comercialización, incluida la creación de promociones y las actualizaciones de metadatos de catálogo, siguiendo instrucciones en lenguaje natural.
- Acceda a asistencia y orientación contextuales directamente dentro del flujo de trabajo de administración.
- Consultar datos del almacén activo bajo demanda; por ejemplo, recuperar los últimos 10 pedidos, ver las promociones activas actualmente o comprobar el estado del inventario.
- Reduzca el tiempo invertido en tareas repetitivas de administración, liberando a los comerciantes para que se centren en la estrategia y el crecimiento.

Para participar en esta versión beta, envía un correo electrónico a [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com).

### Adobe Commerce Foundation (Alpha público/Beta)

[!BADGE Solo PaaS]{type=Informative url="https://experienceleague.adobe.com/es/docs/commerce/user-guides/product-solutions" tooltip="Se aplica solo a proyectos de Adobe Commerce en la nube (infraestructura PaaS administrada por Adobe) y a proyectos locales."}

Cada versión alfa y beta de Adobe Commerce Foundation incluye todos los cambios entregados al código principal de Adobe Commerce en la fecha programada de lanzamiento, incluidas, entre otras, las siguientes áreas funcionales:

- Últimas correcciones de seguridad
- Mejoras de rendimiento
- Mejoras de GraphQL
- Correcciones de errores de calidad generales
- Contribuciones comunitarias
- Cambios necesarios para admitir la compatibilidad con [servicios de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce/user-guides/home)

#### Convenciones y programación de nombres

Adobe suele publicar parches alfa y beta varias veces al año.

Los paquetes de la versión de Alpha tienen un sufijo `-alphaX`. Por ejemplo, los paquetes de la versión Adobe Commerce 2.4.7 alpha utilizan la siguiente convención de nombres:

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Los paquetes de la versión de Beta tienen un sufijo `-betaX`. Por ejemplo, los paquetes de la versión beta de Adobe Commerce 2.4.7 utilizan la siguiente convención de nombres:

- `2.4.7-beta1`
- `2.4.7-beta2`

Consulte la [programación de versiones](schedule.md) para ver la lista de fechas de las próximas versiones alfa y beta públicas.

#### Acceso de versión

Las versiones alfa y beta de Adobe Commerce se distribuyen de la misma manera que cualquier otra versión de parche de Adobe Commerce: como metapaquetes de Composer en `https://repo.magento.com`. El código fuente está disponible en [GitHub](https://github.com/magento/magento2).

Consulte [Inicio rápido de la instalación del compositor](../installation/composer.md) para obtener más información.

#### Informe de problemas

Adobe no proporciona el servicio de asistencia estándar de Adobe para las versiones alfa y beta.

Para enviar comentarios relacionados con las versiones alfa y beta, sigue el [flujo regular de informes de problemas](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) en [GitHub](https://github.com/magento/magento2).

Adobe supervisa todos los problemas críticos notificados con respecto a la última versión alfa o beta y da prioridad a que se resuelvan antes de la fecha de lanzamiento de GA.
