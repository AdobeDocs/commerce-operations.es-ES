---
title: Configurar el bloque ESI de barniz
description: Obtenga información acerca de Barnish Edge Side Includes (ESI) y cómo incrustar páginas web para Adobe Commerce. Descubra la implementación y optimización de bloques de ESI.
badge: label="Colaboró Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: 605b2e59d200bc8eeab43e91006a3f95e6a6c138
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---

# Configurar el bloque ESI de Barniz {#varnish-esi-block}

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
