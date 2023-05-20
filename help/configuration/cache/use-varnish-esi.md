---
title: Barniz Bloque ESI
description: Obtenga información acerca de las inclusiones de Edge Side y cómo puede utilizarlas para incrustar páginas web.
badge: label="Colaborado por Konstantin G." type="Informativo" url="https://github.com/goivvy" tooltip="Konstantin G."
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Barniz Bloque ESI

Edge Side Includes (ESI) son directivas especiales que puede utilizar para incluir páginas web en otras páginas web.

Un ejemplo:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

El barniz obtiene contenido de `http://domain.com/index.php/page_cache/block/esi/blocks` y sustituya el `<esi>` etiqueta con ella.

## Comercio y Barniz ESI

El marco de Commerce crea una etiqueta ESI cuando se cumplen las siguientes condiciones:

- La aplicación de almacenamiento en caché está configurada en `Varnish Cache`
- Un diseño XML `block` se añade con un `ttl` atributo

### Ejemplo

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

En el ejemplo anterior, la variable `block` añade contenido desde el `esi.phtml` plantilla a una página de inicio y Barnish la actualiza automáticamente cada 30 segundos.

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
