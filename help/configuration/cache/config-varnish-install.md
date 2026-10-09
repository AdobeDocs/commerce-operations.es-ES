---
title: Instalar barniz
description: Obtenga información acerca de los requisitos de instalación de Varnish para el almacenamiento en caché de Adobe Commerce. Descubra los recursos de instalación y las instrucciones de instalación.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
badgePaas: label="En las instalaciones" type="Informative" url="https://experienceleague.adobe.com/es/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
autotag-review: '2026-06-22T21:26:58.525Z'
TQID: 'https://experienceleague.adobe.com/Cvy4Qsi-5Fom1t5wqNlq1SiSs4Bb8-DPsWrGfapWfSc'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%
---
# Instalar barniz

{{varnish-config-cloud}}

La instalación del barniz queda fuera del ámbito de esta guía. En este tema se da por hecho que se admite la versión de Varnish y que se ejecuta un servidor de origen de Adobe Commerce detrás de Varnish. Los ejemplos de esta guía utilizan nginx como servidor web de origen.

- [guía de instalación](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Guías de instalación de barniz](https://www.varnish-cache.org/docs)
- [Cómo instalar Varnish (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Si tiene intención de instalar módulos Varnish (vmods), como el modo Saint, debe instalar Varnish compilando el código, en lugar de instalar desde un paquete. Consulte [Modo Saint](config-varnish-advanced.md#saint-mode) para obtener más información.

## Confirma tu versión de Barniz

Abra un terminal e introduzca el siguiente comando para mostrar la versión de Barniz:

```shell
varnishd -V
```

Asegúrese de que [Adobe Commerce admite](../../installation/system-requirements.md) la versión instalada de Varnish antes de continuar. Si está ejecutando una versión no compatible, debe actualizar a una versión compatible. Consulte la documentación de instalación de Varnish para obtener más información.
