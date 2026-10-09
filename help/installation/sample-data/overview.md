---
title: Resumen de datos de muestra
description: Obtenga información acerca de la instalación de datos de muestra de Adobe Commerce para demostraciones y formación, cómo se comporta la tienda basada en Luma y las limitaciones para el desarrollo de la producción.
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%
---
# Resumen de datos de muestra

Los datos de muestra proporcionan una tienda basada en el tema de Luma equipado con productos, categorías, registro de clientes, etc. Funciona igual que una tienda de Commerce y puede manipular los precios, el inventario y las reglas de precios promocionales usando el administrador.

>[!NOTE]
>
>Para revisar y analizar la base de datos y varias funciones, considere la posibilidad de utilizar datos reales en lugar de datos de ejemplo. Los datos de muestra están diseñados como una simulación de tienda generada previamente para demostrar el diseño del tema y el comportamiento básico de la tienda. Todas las entidades de datos de ejemplo se escriben directamente en las tablas de la base de datos, mientras que los datos de ejemplo se instalan.

Puede instalar datos de ejemplo antes o después de instalar el software de Commerce. Cuando haya terminado con los datos de ejemplo, puede eliminarlos o instalarlos de nuevo tal como se describe en [Quitar módulos de datos de ejemplo o actualizar datos de ejemplo](remove-or-update.md).

>[!WARNING]
>
>No puede desinstalar datos de ejemplo. Utilice datos de ejemplo solo para obtener más información sobre cómo funciona Adobe Commerce. Evite realizar cualquier desarrollo en un sistema en el que haya instalado datos de ejemplo.

Puede instalar datos de ejemplo opcionales de cualquiera de las siguientes maneras:

| Método de instalación | Descripción | Nivel de habilidad requerido |
|--- |--- |--- |
| Uso del compositor | [Ejecute `magento sampledata:deploy` para modificar la raíz de la aplicación `composer.json`](composer-packages.md) y habilitar los módulos de datos de ejemplo. | Requiere conocimientos de composición y acceso al sistema de archivos de Commerce. |
| Clonación de repositorios | [Clona el repositorio de GitHub](git-repositories.md) y el repositorio de datos de ejemplo y, a continuación, vincúlelos. | Solo para desarrolladores colaboradores. Todos los demás deben utilizar uno de los métodos anteriores. |
