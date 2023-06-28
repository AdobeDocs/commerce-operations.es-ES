---
title: Listas de comprobación de requisitos
description: Utilice esta lista de preguntas completas para prepararse para una implementación de Adobe Commerce.
exl-id: 9ac485c5-d491-4022-9366-5e3a382513b6
feature: Best Practices
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1536'
ht-degree: 0%

---

# Listas de comprobación de requisitos

Las siguientes preguntas pueden servir como punto de partida para ver qué información debe documentarse para confirmar la preparación de la organización. También pueden ayudar al desarrollar una RFP.

## Empresa

- ¿Cuáles son los objetivos comerciales de la nueva plataforma de comercio electrónico?

- ¿Cuáles son las razones para cambiar su plataforma de comercio electrónico actual?

- ¿Cuáles son los objetivos de la infraestructura del sitio web?

- ¿Cuál es su periodo de tiempo para ofrecer la nueva plataforma de comercio electrónico?

- ¿Cuántos de sus jefes de proyecto de TI se asignarán a este proyecto?

- ¿Cuántos de sus analistas empresariales se asignarán a este proyecto?

- ¿Cuántos de sus analistas técnicos se asignarán a este proyecto?

- ¿Cuántos de los desarrolladores HTML se asignarán a este proyecto?

- ¿Qué documentación existe para los procesos empresariales actuales?

- ¿Qué documentación existe para las integraciones de sistemas actuales?

- ¿Qué documentación existe para los flujos de proceso actuales?

- ¿Qué documentación existe para los flujos de datos actuales?

- ¿Quién proporcionará la formación?

- ¿Qué formación se completará antes del lanzamiento?

- ¿Qué formación se completará después del lanzamiento?

- ¿Qué asistencia de Adobe Commerce se requerirá después del lanzamiento?

- ¿Depende este proyecto de otros proyectos de desarrollo de sistemas?

- ¿Cómo cree que crecerán sus ventas en los próximos 12-24 meses?

- ¿Quiénes son sus principales competidores? Proporcione vínculos a sus sitios. ¿Cómo desea diferenciar su experiencia en línea de la de sus competidores?

- ¿De dónde cree que proviene el crecimiento futuro de su negocio?

- ¿Qué papel desempeña el comercio digital en su estrategia comercial? ¿Cuáles son sus objetivos principales para configurar esta plataforma de comercio electrónico?

- ¿Tiene alguna marca o empresa que tome como referencia sobre cómo hacer crecer su negocio omnicanal?

- ¿Qué equipos o personas impulsan la estrategia de comercio electrónico? Describa las posiciones relevantes.

## Plataforma actual

- ¿Cómo se aloja la plataforma actual: interno, proveedor de alojamiento, servidores de nube privados o servidores de nube alojados?

- ¿Qué entornos tiene la plataforma actual: desarrollo, control de calidad, preproducción, producción?

- ¿Cuántos servidores web y de base de datos hay en el entorno de desarrollo?

- ¿Cuántos servidores web y de base de datos hay en el entorno de control de calidad?

- ¿Cuántos servidores web y de base de datos hay en el entorno de ensayo (preproducción)?

- ¿Cuántos servidores web y de base de datos hay en el entorno de producción?

- ¿Se trata de una arquitectura de varios servidores con equilibrio de carga?

- ¿Es una arquitectura de sistema de alta disponibilidad?

- ¿Qué problemas tiene con sus sitios web actuales?

- ¿Tamaño del catálogo actual (número de SKU)?

- ¿Visitantes promedio por día?

- ¿Promedio de sesiones simultáneas por hora?

- ¿Promedio de vistas de página por día?

- ¿Pedidos medios por hora y por día?

## Requisitos de plataforma previstos

- ¿Qué versión de Adobe Commerce usará?

- ¿Cómo se alojará la futura plataforma: interno, proveedor de alojamiento, servidores de nube privados o servidores de nube alojados?

- ¿Qué entornos tendrá la futura plataforma: desarrollo, control de calidad, preproducción, producción?

- ¿Cuántos servidores web y de base de datos habrá en el entorno de desarrollo?

- ¿Será una arquitectura de sistema de alta disponibilidad?

- ¿Cuántos administradores de Adobe Commerce tendrá?

- ¿Tamaño de catálogo esperado (número de SKU)?

- ¿Visitantes promedio esperados por día?

- ¿Promedio esperado de sesiones simultáneas por hora?

- ¿Promedio esperado de vistas de página por día?

- ¿Qué datos deben importarse del sitio antiguo al nuevo? (Ejemplo: producto, cliente, historial de pedidos)

## Sitios web

- ¿Cuántos sitios web nacionales se implementarán?

- ¿Qué idiomas se implementarán?

- ¿Cuántos sitios web internacionales se implementarán?

- ¿Con qué regiones son compatibles los sitios web?

- ¿Qué idiomas se implementarán?

- ¿Qué monedas se implementarán?

- ¿Tiene acuerdos de nivel de servicio de entrega para cada país?

- ¿Quiénes son sus proveedores de envíos para cada país?

- ¿Quiénes son sus proveedores de contabilidad tributaria para cada país?

- ¿Necesitará un tema de sitio web internacional personalizado?

- ¿Se trata principalmente de un sitio B2C o B2B? ¿Hay algún elemento B2B2B o B2B2C?

- ¿Existe un diseño existente que esté adaptado o la plataforma se diseñará desde cero?

- ¿Existe algún requisito para el comercio sin encabezado (capas de front-end y back-end independientes)?

- ¿Cuáles son los puntos de interrupción (tableta/móvil) para el diseño interactivo?

- ¿Se requiere una aplicación móvil? ¿Se debe aprovechar PWA para el front-end móvil?

- ¿Algún navegador específico que se deba probar (excepto los navegadores estándar IE9+, Firefox, Chrome, Safari)?

- ¿Cuáles son los idiomas de cada front-end? ¿Está disponible el contenido traducido o se necesita asistencia?

- ¿Hay varios sitios web? Si es así, ¿pueden los clientes utilizar sus credenciales en todos los sitios?

- ¿Los datos del producto de se comparten en todos los sitios?

- ¿Hay cambios en el diseño de un sitio a otro?

- ¿Existen opciones de suscripción y cómo se administran los suscriptores?

- ¿Existen requisitos específicos de SEO? ¿Cómo se administra el marketing del motor de búsqueda?

## Integraciones

- ¿Qué sistema CMS se integrará con Adobe Commerce? (Ejemplos: WordPress, Drupal, Concrete5)

¿Existen API que se puedan usar?

- ¿Se ha diseñado y desarrollado la gestión de errores del sistema para esta integración de sistemas de terceros?

- ¿Qué sistema ERP se integrará con Adobe Commerce? (Ejemplos: SAP, MS Dynamics NAV)

- ¿Qué sistema de transportista se integrará con Adobe Commerce?

- ¿Qué sistema de software fiscal se integrará con Adobe Commerce? (Ejemplo: Taxware)

- ¿Desde qué sistema se importarán los datos de productos en Adobe Commerce?

- ¿Frecuencia de las cargas de datos de productos importados?

- ¿En qué sistema exportará Adobe Commerce los datos de productos?

- ¿Frecuencia de las cargas de datos de productos exportados?

- ¿Desde qué sistema se importarán los datos en Adobe Commerce?

- ¿Frecuencia de las cargas de datos de pedidos importados?

- ¿En qué sistema exportará Adobe Commerce los datos de los pedidos?

- Frecuencia de las cargas de datos de pedidos exportados

- ¿Qué plataforma de análisis se utiliza? (Ejemplos: Adobe Analytics, Google Analytics)

- ¿Habrá inicio de sesión único y uso compartido en redes sociales? En caso afirmativo, ¿qué redes sociales?

- ¿Hay algún programa de recompensas o fidelización? ¿Existe alguna integración con los sistemas POS para recompensas?

- ¿Cómo se gestionan las devoluciones de productos? ¿Se espera que el cliente registre una solicitud de devolución en línea?

- ¿Se necesita una herramienta de chat en línea? ¿Se necesita un bot de chat?

- ¿Qué pasarela de pago desea que tenga su sitio?

- ¿Qué sistema de gestión de pedidos se integrará con Adobe Commerce? (Ejemplos: Microsoft Dynamics, SAP, Retail Pro)

- ¿Qué sistema de administración de la información del producto se integrará con Adobe Commerce? (Ejemplos: Akeneo, InRiver, Bluestone)

- ¿Qué sistema de administración de la relación con los clientes se integrará con Adobe Commerce? (Ejemplos: Hubspot, Salesforce, Klaviyo)

## Funciones específicas de Adobe Commerce

- ¿Requerirá algún tipo de prueba A/B?

- ¿Cuántos administradores simultáneos pueden estar trabajando en el sistema?

- ¿Permitirá que un cliente recoja artículos comprados en el sitio web en una tienda?

- ¿Tendrá páginas promocionales?

- ¿Tendrá titulares de marketing?

- ¿Desea que los vídeos se reproduzcan en una página CMS?

- ¿Cuál será la frecuencia de modificación o actualización del contenido?

- ¿Qué tipo de contenido se cargará?

- ¿Se programarán las actualizaciones de contenido?

- ¿Necesitará un sitio web de ensayo de contenido?

- ¿Se debe permitir a los clientes crear una cuenta de sitio web?

- ¿Utilizará cupones de descuento únicos para las promociones?

- ¿Tendrá precios promocionales?

- ¿Tendrá cupones flexibles (capacidad de configurar por sitio web, grupo de clientes, tiempo, categorías o productos)?

- ¿Se ofrecerán descuentos porcentuales para artículos individuales?

- ¿Qué tipo de funcionalidad de regalo se requerirá?

- ¿Se requerirá la funcionalidad del programa de recompensas?

- ¿Se requerirá la funcionalidad de la newsletter?

- ¿Desea permitir que un cliente vea pedidos pasados y seleccione los artículos que desea intercambiar?

- ¿Permitirá a un cliente iniciar la cancelación de un pedido desde el sitio web?

- ¿Permitirá que un cliente inicie el intercambio de artículos desde el sitio web?

- ¿Requerirá validación de direcciones en tiempo real?

- ¿Permitirá que un cliente inicie la devolución de artículos desde el sitio web?

- ¿Adobe Commerce emitirá una autorización de devolución de material?

- ¿Desea recopilar información sobre reembolsos en Adobe Commerce?

- ¿Requerirá el seguimiento de pedidos en línea para un cliente registrado?

- ¿Requerirá el seguimiento de pedidos en línea para un cliente invitado?

- ¿Ejecutar la autorización en línea y la captura durante la realización del pedido?

- Autorización con filtro de fraude durante la realización del pedido con captura retrasada

- ¿Número de días para recibir el pago completo (sin autorización)?

- ¿Capturar y ejecutar contra vencimiento de autorización?

- Authorize.net

- Braintree

- PayPal Express

- Almacenar crédito

- Tarjetas de regalo de plástico

- Puntos de recompensa

- &quot;Facturarme más tarde&quot;: más conocido como &quot;Comprar ahora, pagar más tarde&quot;, ya que se factura inmediatamente, pero aún no se ha pagado

- ¿Habrá diferentes precios de productos en diferentes sitios web?

- ¿Se requerirá la funcionalidad para comparar diferentes productos?

- ¿Qué tipos de productos venderá?

- ¿Cuál será la frecuencia de adición de nuevos productos?

- ¿Cuál será la frecuencia de actualización de los productos?

- ¿Cuál será la frecuencia de creación de nuevas categorías o subcategorías?

- ¿Se requiere la funcionalidad &quot;Valoraciones y críticas&quot;?

- ¿Permitirá que los clientes recomienden un producto?

- Ventas: Pedidos, impuestos, facturados, envíos, reembolsos, cupones, informes de liquidación de PayPal

- Carrito de compra: Productos en carritos, artes abandonadas

- Productos: Bestsellers, productos pedidos, más vistos, bajo stock, descargas

- Clientes: Cuentas nuevas, clientes por total de pedidos, clientes por número de pedidos, segmentos de clientes, opiniones de clientes

- Revisiones de productos

- Etiquetas: Clientes, productos, populares

- Términos de búsqueda

- Invitaciones: General, clientes, tasa de conversión de pedidos

- ¿Necesita Adobe Commerce para generar informes basados en datos de uso de cupones?

- ¿Necesita Adobe Commerce para generar informes basados en datos de ventas?

- ¿Necesitará informes personalizados de Adobe Commerce?

- ¿Cuál es tu estrategia actual de SEO?

- ¿Cuál será su nueva estrategia de SEO?

- ¿Cuáles son sus requisitos para la migración a SEO?

- ¿Almacenar tarifas fijas en Adobe Commerce?

- ¿Permitir el envío parcial?

- ¿Debe almacenarse la información de seguimiento de envíos en Adobe Commerce?

- ¿Exigirá reglas de cálculo de impuestos para sus regiones domésticas?

- ¿Exigirá reglas de cálculo de impuestos para sus regiones internacionales?
