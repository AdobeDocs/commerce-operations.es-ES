---
title: Configurar el bloque ESI de barniz
description: Obtenga información acerca de Barnish Edge Side Includes (ESI) y cómo incrustar páginas web para Adobe Commerce. Descubra la implementación y optimización de bloques de ESI.
badge: label="Colaboró Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
badgePaas: label="En las instalaciones" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
autotag-review: '2026-06-22T22:02:08.706Z'
TQID: 'https://experienceleague.adobe.com/hzsfaZyHuUhzfb86anO43PfP-62WRPOoMbYOh-H1vqo'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 159
ht-degree: 0%

---

# Configurar el bloque ESI de Barniz {#varnish-esi-block}

{{varnish-config-cloud}}

Edge Side Includes (ESI) son directivas especiales que puede utilizar para incluir páginas web en otras páginas web.

Un ejemplo:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

El barniz recupera contenido de `http://domain.com/index.php/page_cache/block/esi/blocks` y reemplaza la etiqueta `<esi>` por ella.

## Commerce y Varnish ESI

El marco de trabajo de Commerce crea una etiqueta ESI cuando se cumplen las siguientes condiciones:

- La aplicación de almacenamiento en caché está establecida en `Varnish Cache`
- Se agregó un elemento `block` de diseño XML con un atributo `ttl`

### Ejemplo

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

En el ejemplo anterior, el elemento `block` agrega contenido de la plantilla `esi.phtml` a una página principal y Varnish lo actualiza automáticamente cada 30 segundos.

## Limitaciones

Actualmente, Varnish no admite ESI sobre HTTPS, por lo que cambia automáticamente a HTTP.

`Magento\PageCache\Observer\ProcessLayoutRenderElement`:

```php
    private function _wrapEsi(
        \Magento\Framework\View\Element\AbstractBlock $block,
        \Magento\Framework\View\Layout $layout
    ) {
    ....
        // Varnish does not support ESI over HTTPS must change to HTTP
        $url = substr($url, 0, 5) === 'https' ? 'http' . substr($url, 5) : $url;
        return sprintf('<esi:include src="%s" />', $url);
    }
```
