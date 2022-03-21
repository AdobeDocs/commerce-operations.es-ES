---
title: Listas de comprobación de requisitos
description: Utilice esta lista de preguntas completas para prepararse para una implementación de Adobe Commerce.
exl-id: 9ac485c5-d491-4022-9366-5e3a382513b6
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '1536'
ht-degree: 0%

---

# Listas de comprobación de requisitos

Las siguientes preguntas pueden servir de punto de partida para ver qué información debe documentarse para confirmar la preparación de la organización. También pueden ayudar a desarrollar una RFP.

## Empresa

- ¿Cuáles son los objetivos comerciales de la nueva plataforma de comercio electrónico?

- ¿Cuáles son las razones para cambiar la plataforma de comercio electrónico actual?

- ¿Cuáles son los objetivos de la infraestructura del sitio web?

- ¿Cuál es su periodo para ofrecer la nueva plataforma de comercio electrónico?

- ¿Cuántos de sus jefes de proyecto de TI se asignarán a este proyecto?

- ¿Cuántos de sus analistas de negocio se asignarán a este proyecto?

- ¿Cuántos de sus analistas técnicos se asignarán a este proyecto?

- ¿Cuántos de los desarrolladores HTML se asignarán a este proyecto?

- ¿Qué documentación existe para los procesos comerciales actuales?

- ¿Qué documentación existe para las integraciones actuales del sistema?

- ¿Qué documentación existe para los flujos de proceso actuales?

- ¿Qué documentación existe para los flujos de datos actuales?

- ¿Quién proporcionará la formación?

- ¿Qué formación se completará antes del lanzamiento?

- ¿Qué formación se completará después de la entrada en funcionamiento?

- ¿Qué soporte de Adobe Commerce se necesitará después de la activación?

- ¿Este proyecto depende de otros proyectos de desarrollo del sistema?

- ¿Cómo ve que sus ventas crecen en los próximos 12-24 meses?

- ¿Quiénes son sus principales competidores? Proporcione enlaces a sus sitios. ¿Cómo desea diferenciar su experiencia en línea de la de sus competidores?

- ¿De dónde puede ver el crecimiento futuro en su negocio?

- ¿Qué papel desempeña el comercio digital en su estrategia empresarial? ¿Cuáles son sus objetivos principales para configurar esta plataforma de comercio electrónico?

- ¿Tiene alguna marca o empresa que tome como referencia para el crecimiento de su negocio omnicanal?

- ¿Qué equipos o personas están impulsando la estrategia de comercio electrónico? Describa las posiciones relevantes.

## Plataforma actual

- Cómo se aloja la plataforma actual: Interno, proveedor de alojamiento, servidores de nube privados o servidores de nube alojados?

- Qué entornos tiene la plataforma actual: desarrollo, control de calidad, preproducción, producción?

- ¿Cuántos servidores de bases de datos y web se encuentran en el entorno de desarrollo?

- ¿Cuántos servidores web y de base de datos están en el entorno de control de calidad?

- ¿Cuántos servidores web y de base de datos están en el entorno de ensayo (preproducción)?

- ¿Cuántos servidores web y de base de datos hay en el entorno de producción?

- ¿Es una arquitectura de varios servidores con equilibrio de carga?

- ¿Es una arquitectura de sistemas de alta disponibilidad?

- ¿Qué problemas experimenta con sus sitios web actuales?

- ¿Tamaño actual del catálogo (número de SKU)?

- ¿Promedio de visitantes por día?

- ¿Promedio de sesiones simultáneas por hora?

- ¿Promedio de vistas de página por día?

- ¿Promedio de pedidos por hora y día?

## Requisitos de plataforma esperados

- ¿Qué versión de Adobe Commerce utilizará?

- Cómo se alojará la futura plataforma: Interno, proveedor de alojamiento, servidores de nube privados o servidores de nube alojados?

- Qué entornos tendrá la plataforma futura: desarrollo, control de calidad, preproducción, producción?

- ¿Cuántos servidores web y de base de datos estarán en el entorno de desarrollo?

- ¿Será una arquitectura de sistemas de alta disponibilidad?

- ¿Cuántos administradores de Adobe Commerce tendrá?

- ¿Tamaño esperado del catálogo (número de SKU)?

- ¿El promedio de visitantes esperado por día?

- ¿Sesiones simultáneas promedio esperadas por hora?

- ¿El promedio de vistas de página por día esperado?

- ¿Qué datos se deben importar del sitio antiguo al nuevo? (Ejemplo: producto, cliente, historial de pedidos)

## Sitios web

- ¿Cuántos sitios web nacionales se implementarán?

- ¿Qué idiomas se implementarán?

- ¿Cuántos sitios web internacionales se implementarán?

- ¿Con qué regiones serán compatibles los sitios web?

- ¿Qué idiomas se implementarán?

- ¿Qué monedas se implementarán?

- ¿Tiene acuerdos de nivel de servicio de entrega para cada país?

- ¿Quiénes son sus proveedores de envíos para cada país?

- ¿Quiénes son sus proveedores de cuentas fiscales para cada país?

- ¿Necesitará un tema de sitio web internacional personalizado?

- ¿Se trata principalmente de un sitio B2C o B2B? ¿Hay algún elemento B2B2B o B2B2C?

- ¿Existe un diseño que se adapte o se diseñará desde cero?

- ¿Existe algún requisito para el comercio sin periféricos (capas de front-end y back-end separadas)?

- ¿Cuáles son los puntos de interrupción (tableta/móvil) para el diseño interactivo?

- ¿Existe algún requisito para una aplicación móvil? ¿Se debe aprovechar el PWA para el front-end móvil?

- ¿Algún navegador específico que deba probarse (excepto los navegadores estándar IE9+, Firefox, Chrome, Safari)?

- ¿Cuáles son los idiomas para cada front-end? ¿Está disponible el contenido traducido o se necesita soporte técnico?

- ¿Hay varios sitios web? Si es así, ¿pueden los clientes utilizar sus credenciales en todos los sitios?

- ¿Los datos del producto se comparten en todos los sitios?

- ¿Hay cambios en el diseño de un sitio a otro?

- ¿Hay opciones de suscripción y cómo se administran los suscriptores?

- ¿Existen requisitos específicos de SEO? ¿Cómo se administra el marketing de motor de búsqueda?

## Integraciones

- ¿Qué sistema CMS se integrará con Adobe Commerce? (Ejemplos: WordPress, Drupal, Concrete5)

¿Hay API existentes que se puedan usar?

- ¿Se ha diseñado y desarrollado la gestión de errores del sistema para esta integración de sistemas de terceros?

- ¿Qué sistema ERP se integrará con Adobe Commerce? (Ejemplos: SAP, MS Dynamics NAV)

- ¿Qué sistema de transportista marítimo se integrará con Adobe Commerce?

- ¿Qué sistema de software fiscal se integrará con Adobe Commerce? (Ejemplo: Taxware)

- ¿Desde qué sistema se importarán los datos del producto en Adobe Commerce?

- ¿Frecuencia de carga de datos de productos importados?

- ¿En qué sistema exportará Adobe Commerce los datos del producto?

- ¿Frecuencia de carga de datos de productos exportados?

- ¿Desde qué sistema se importarán los datos en Adobe Commerce?

- ¿Frecuencia de carga de datos de pedidos importados?

- ¿En qué sistema exportará Adobe Commerce los datos de pedidos?

- ¿Frecuencia de carga de datos de pedidos exportados?

- ¿Qué plataforma de análisis se utiliza? (Ejemplos: Adobe Analytics, Google Analytics)

- ¿Habrá inicio de sesión único y uso compartido en redes sociales? En caso afirmativo, ¿qué redes sociales?

- ¿Hay algún programa de recompensas o lealtad? ¿Existe alguna integración con los sistemas POS para recompensas?

- ¿Cómo se gestionan las devoluciones de productos? ¿Se espera que el cliente registre una solicitud de devolución en línea?

- ¿Se necesita una herramienta de chat en línea? ¿Se necesita un bot de chat?

- ¿Qué pasarela de pago desea que tenga su sitio?

- ¿Qué sistema de gestión de pedidos se integrará con Adobe Commerce? (Ejemplos: Microsoft Dynamics, SAP, Retail Pro)

- ¿Qué sistema de administración de inventario de productos se integrará con Adobe Commerce? (Ejemplos: Akeneo, InRiver, Bluestone)

- ¿Qué sistema de administración de la relación con los clientes se integrará con Adobe Commerce? (Ejemplos: Hubspot, Salesforce, Klaviyo)

## Funciones específicas de Adobe Commerce

- ¿Necesitará algún tipo de prueba A/B?

- ¿Cuántos administradores simultáneos pueden trabajar en el sistema?

- ¿Permitirá a un cliente recoger artículos comprados en el sitio web en una tienda?

- ¿Tendrá páginas promocionales?

- ¿Tendrá titulares de marketing?

- ¿Desea que los vídeos se reproduzcan en una página de CMS?

- ¿Cuál será la frecuencia de modificación o actualización del contenido?

- ¿Qué tipo de contenido se cargará?

- ¿Se programarán las actualizaciones de contenido?

- ¿Necesitará un sitio web de ensayo de contenido?

- ¿Se debe permitir a los clientes crear una cuenta de sitio web?

- ¿Utilizará cupones de descuento únicos para las promociones?

- ¿Tendrá precios promocionales?

- ¿Tendrá cupones flexibles (capacidad de configuración por sitio web, grupo de clientes, hora, categorías o productos)?

- ¿Se ofrecerán descuentos porcentuales para artículos individuales?

- ¿Qué tipo de funcionalidad de regalo se necesitará?

- ¿Será necesaria la funcionalidad del programa de recompensas?

- ¿Se necesitará la funcionalidad del boletín informativo?

- ¿Permitir que un cliente vea pedidos anteriores y seleccione artículos que desea intercambiar?

- ¿Permitirá a un cliente iniciar la cancelación de un pedido desde el sitio web?

- ¿Permitirá a un cliente iniciar el intercambio de artículos desde el sitio web?

- ¿Necesitará la validación de direcciones en tiempo real?

- ¿Permitirá a un cliente iniciar la devolución de artículos desde el sitio web?

- ¿Adobe Commerce emitirá una RMA de retorno?

- ¿Capturar información sobre reembolsos en Adobe Commerce?

- ¿Necesitará realizar un seguimiento de pedidos en línea para un cliente registrado?

- ¿Necesitará un seguimiento de pedidos en línea para un cliente invitado?

- ¿Ejecutar la autorización en línea y la captura durante la colocación del pedido?

- Autorización con filtro de fraude durante la colocación del pedido con captura retardada

- ¿Número de días para recibir el pago completo (no autorización)?

- ¿Capturar y ejecutar contra la caducidad de la autorización?

- Authorize.net

- Braintree

- PayPal Express

- Crédito de la tienda

- Tarjetas de regalo de plástico

- Puntos de rebote

- &quot;Bill Me Later&quot; - más comúnmente conocido como &quot;Buy Now, Pay Later&quot; (Comprar ahora, Pagar más tarde) ya que es facturado inmediatamente pero aún no pagado

- ¿Habrá diferentes precios de producto en diferentes sitios web?

- ¿Será necesaria la funcionalidad para comparar diferentes productos?

- ¿Qué tipos de productos venderás?

- ¿Cuál será la frecuencia de adición de nuevos productos?

- ¿Cuál será la frecuencia de actualización de productos?

- ¿Cuál será la frecuencia de creación de nuevas categorías o subcategorías?

- ¿Se requiere la funcionalidad &quot;Clasificaciones y revisiones&quot;?

- ¿Permitirá a los clientes recomendar un producto?

- Ventas: Pedidos, impuestos, facturados, envío, reembolsos, cupones, informes de liquidación de PayPal

- Carro de compras: Productos en carros, artes abandonadas

- Productos: Bestsellers, productos pedidos, más visitados, stock bajo, descargas

- Clientes: Nuevas cuentas, clientes por pedidos en total, clientes por número de pedidos, segmentos de clientes, revisiones de clientes

- Revisiones de productos

- Etiquetas: Clientes, productos, popular

- Términos de búsqueda

- Invitaciones: General, clientes, tasa de conversión de pedidos

- ¿Necesitará Adobe Commerce para generar informes basados en datos de uso de cupones?

- ¿Necesitará Adobe Commerce para generar informes basados en datos de ventas?

- ¿Necesitará informes personalizados de Adobe Commerce?

- ¿Cuál es su estrategia actual de SEO?

- ¿Cuál será su nueva estrategia SEO?

- ¿Cuáles son sus requisitos para la migración de SEO?

- ¿Desea almacenar las tarifas fijas en Adobe Commerce?

- ¿Permitir el envío parcial?

- ¿La información de seguimiento de envíos debe almacenarse en Adobe Commerce?

- ¿Necesitará reglas de cálculo de impuestos para sus regiones domésticas?

- ¿Necesitará reglas de cálculo de impuestos para sus regiones internacionales?
