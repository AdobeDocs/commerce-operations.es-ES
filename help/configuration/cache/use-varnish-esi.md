---
title: Barniz ESI
description: Obtenga más información sobre Edge Side Includes y cómo puede utilizarlas para incrustar páginas web.
contributor_name: Goivvy LLC
contributor_link: https://www.goivvy.com/magento-optimization-service
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Barniz ESI

Edge Side Includes (ESI) son directivas especiales que puede utilizar para incluir páginas web en otras páginas web.

Un ejemplo:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

Var obtiene contenido de `http://domain.com/index.php/page_cache/block/esi/blocks` y reemplace el `<esi>` con él.

## Commerce y Varnish ESI

El marco de comercio crea una etiqueta ESI cuando se cumplen las siguientes condiciones:

- La aplicación de almacenamiento en caché está configurada en `Varnish Cache`
- Un diseño XML `block` se agrega con un `ttl` attribute

### Ejemplo

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

En el ejemplo anterior, la variable `block` el elemento agrega contenido desde el `esi.phtml` plantilla en una página principal y Varnish la actualiza automáticamente cada 30 segundos.

## Limitaciones

Actualmente, Varnish no admite ESI a través de HTTPS, por lo que cambia automáticamente a HTTP.

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
